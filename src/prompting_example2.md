# More Prompting Examples

**The following is from the example agent.py file.**

```import bittensor as bt
import json

axon_client = bt.AxonClient(ip="127.0.0.1", port=9090)

messages = [{"role": "user", "content": "What is the purpose of the Bittensor network?"}]
encoded_messages = [json.dumps(message) for message in messages]

response = axon_client.forward(encoded_messages)

print("Response:", response)```



