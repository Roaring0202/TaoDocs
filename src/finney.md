# What is Finney?

**But first, who was Finney**

[Hal Finney](https://en.wikipedia.org/wiki/Hal_Finney_(computer_scientist)) was a computer scientist and Cypherpunk who recieved the first Bitcoin from Satoshi Nakamoto in January 2009.

```In 2004, Finney created the first reusable proof of work system before Bitcoin.[10] In January 2009, Finney was the Bitcoin network's first transaction recipient from the legendary Satoshi Nakamoto.```

This person is of signifigance because he created the blue-print. Bittensor is another take on that blue-print, only this time, it leverages both Block-chain and AI to it's advantage.
Without Finney, we wouldn't be here today - so if you want anybody to thank, I would thank him. 

# Finney Prompt Subnetwork

The very first subnetwork on the Finney Network -- prompt subnetworks -- is now available for mining and usage. The prompting subnetwork enables Bittensor to run many prompt neural networks such as GPT-3, GPT-4, ChatGPT, and others to perform **decentralized inference**. This allows users to communicate with the Validators on the network to get the output of the best performing models on the network to power their applications. 

## Testing on the prompting Subnet

Using btcli you can specify you wish to run your miner on the testnet by adding the following flags: 
```--subtensor.network finney --subtensor.chain_endpoint wss://test.finney.opentensor.ai:443.```

## Hardware Requirements

The prompt subnetwork has largely the same hardware requirements as Subnet 3 on Finney. However, there is one exception to the Validators as they are performing more work since they are running a reward and gating model, and servers now respond with a longer response. Therefore we recommend at least 40GB vRAM (40 GB RAM if using only CPU) or above on each graphics card that is running a validator. This also means that running multiple Validators on one card is ill-advised and will likely result in your miner being de-registered. Note that you can still run **Servers** of any size on any graphics card. 

If you are running one validator on multiple subnetworks, then you must make sure that your graphics card is able to hold all the Validators in each subnet. Thus it's best to dedicate one graphics card to each validator. 

## Registration

Registration in the prompt is performed the same way you have always registered. A Hotkey can be registered in multiple subnetworks, hence you can have one validator running in multiple subnetworks.

## Usage instructions
To utilize the prompt subnetwork, run the following commands in your terminal.

```bash
cd ~/.bittensor/bittensor && git pull origin text_prompting
cd ~/.bittensor/bittensor && python3 -m pip install -e .
```

All the default Servers are in the following directory within the Bittensor root directory (~/.bittensor/bittensor).

For instance, to run a `pythia` miner, use the following command:

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Servers/pythia/neuron.py 
```

You can still use flags as before. For example to run the `pythia` miner in the test network (Test network has subnetwork UID 91 as the prompt subnetwork):

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Servers/pythia/neuron.py --wallet.name prompt_Servers --wallet.hotkey prompt_miner1 --subtensor.network finney --subtensor.chain_endpoint wss://test.finney.opentensor.ai:443 --netuid 1

```

You can run the core validator by typing the following:

```bash
python3 ~/.bittensor/bittensor/neurons/text/prompting/Validators/core/neuron.py
```

