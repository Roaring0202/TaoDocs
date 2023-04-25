# The following are an analysis of what .py scripts you can run within the Bittensor Network in order to get responses from Agents.

__Should be noted here that if you know how to write programs, you have an advantage, but that's a baseline skill you'll have to develop for working within the Network.__

This code demonstrates the implementation of a simple Bittensor Synapse, an AI model connected to the Bittensor network. The Synapse processes text-based inputs and returns a response. The main components of the code include:

1. **Import libraries**: Import the required libraries such as `json`, `torch`, `bittensor`, and `typing` for handling data types.

2. **Configure logging**: Set up Bittensor's logging configuration.

3. **Define Synapse class**: Create a custom `Synapse` class that inherits from `bittensor.TextPromptingSynapse`. The `priority`, `blacklist`, `backward`, and `forward` methods are implemented within the class. The main focus is on the `forward` method, which processes a list of dictionaries containing message roles and content.
   - The `forward` method iterates through the list of message dictionaries, extracts the roles and content, and creates an "unravelled" message string that includes the role and content separated by a newline.
   - The method then prints the unravelled message, roles, and contents to the console and returns a hardcoded response string, "hello im a chat bot."

4. **Create wallet and axon**: Instantiate a Bittensor wallet and axon, providing the wallet, port, IP, and metagraph as arguments.

5. **Create dendrite**: Instantiate a Bittensor text-prompting dendrite, passing the axon information and wallet hotkey.

6. **Create Synapse instance**: Instantiate the custom Synapse class, providing the axon as an argument, and start the axon.

7. **Execute forward and backward calls**: Call the `dendrite.forward` method with predefined roles and messages, then perform the backward call with a reward of 1.

8. **Print results**: Print the forward and backward call results.

The printed output displays the "unravelled" message, roles, contents, and the success status of the forward and backward calls.

# The above is the analysis of this program below. 

```import json
import torch
import bittensor
from typing import List, Dict, Union, Tuple

bittensor.logging( bittensor.logging.config() )

class Synapse( bittensor.TextPromptingSynapse ):
    def priority(self, forward_call: "bittensor.TextPromptingForwardCall") -> float:
        return 0.0

    def blacklist(self, forward_call: "bittensor.TextPromptingForwardCall") -> Union[ Tuple[bool, str], bool ]:
        return False

    def backward( self, messages: List[Dict[str, str]], response: str, rewards: torch.FloatTensor ) -> str:
        pass

    def forward(self, messages: List[Dict[str, str]]) -> str:
        unravelled_message = ''
        roles = []; contents = []
        for message_dict in messages:
            message_dict = json.loads( message_dict )
            item_role = message_dict['role']
            item_content = message_dict['content']
            bittensor.logging.success(str(message_dict))
            roles.append( item_role )
            contents.append( item_content )
            if item_role == 'system': unravelled_message += 'system: ' + item_content + '\n'
            if item_role == 'assistant': unravelled_message += 'assistant: ' + item_content + '\n'
            if item_role == 'user': unravelled_message += 'user: ' + item_content + '\n'
        print('unrav', unravelled_message)
        print ('roles', roles)
        print ('contents', contents)
        return "hello im a chat bot."

# Create a mock wallet.
wallet = bittensor.wallet().create_if_non_existent()
axon = bittensor.axon( wallet = wallet, port = 9090, ip = "127.0.0.1", metagraph = None )
dendrite = bittensor.text_prompting( axon = axon.info(), keypair = wallet.hotkey )
synapse = Synapse( axon = axon )
axon.start()

bittensor.logging.debug( "Start example")
forward_call = dendrite.forward(
    roles = ['system', 'assistant'],
    messages = ['You are an Assistant designed to help create better documentation for Bittensor and help me learn.', 'What would be your first piece of advice'],
    timeout = 1e6
)
print ( forward_call )
backward_call = forward_call.backward( 1 )
print ( backward_call )```