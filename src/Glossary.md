# Glossary
---
## Miner Architecture 


### Miner/Neuron/Peer/Node

Used interchangeably to refer to a participant in the network. 


### Hotkey

The part of the miner that contains "hot storage". It is loaded into the network and gives ability to set weights (for Validators). 


### Coldkey

The part of the miner that contains cold storage. Remains on device.


### Axon

Servers receive requests from other peers in the network via the axon.


### Dendrite 

Servers send requests to other peers in the network via the dendrite. 


### Metagraph

A Python torch object that produces a view into the network. This tool is used internally by Servers and also for network analysis. 


## Network 


### Tao 

The digital token that functions as currency in the network. Tao uses the same tokenomics as Bitcoin with a 4 year halving cycle and a max supply of 21 millions tokens.


### Subtensor

The network blockchain. 


### Nakamoto

Our main network. 


### Nobunaga

Our test network. 


### Block step

Occurs every 12 seconds. The blockchain is updated, and newly minted Tao is distributed to the system. 


### UID

The unique identifying number for each Miner. Represents its position in the network. There are currently 4096 UIDs available in the network. 


### Forward Requests

The first stage of the transaction in which a Validator sends data to a Server in the form of tokens, and the the Server sends embeddings back. 


### Backward Requests

The second stage of the transaction in which the Validator sends feedback (in the form of gradients) to the Server.


## Consensus Mechanism


### Stake

Equivalent to the amount of Tao attached to the Miner's hotkey. For Validators, more stake translates to rankings being worth more. For Servers, more stake translates to a lower likelihood of being deregistered from the network. 


### Rank

The raw score given to a Server by a Validators, combined with the stake of the Validator. 


### Trust

This score represents the number of non-zero (approval) rankings that Servers receives from Validators. The trust score is used to determine whether a Server has achieved consensus in the network. The more stake a Validator has, the more trust scores it can distribute. 


### Consensus


Achievement of a Server who has received a non-zero ranking from more than 50% of the stake in the network. Servers who reach consensus receive significantly higher rewards than those who have not. 


### Incentive

The inflation achieved by a Server before dividends are distributed. The incentive is a combination of the rank and consensus scores. 


### Inflation

The amount of currency (1 tao) released into the network at each block step. The single Tao is distributed amongst all peers in the network according to their performance.


### Emissions

Refers to the portion of the one Tao distributed to a single peer each block step.


### Dividends

When Validators rank Servers, they take on part ownership of them through the bonding matrix. When a Server's incentive is calculated, a portion of this is distributed to Validators who have bonds.


### Bonding Matrix

Refers to the bonds that Validators hold in Servers. The higher the stake the Validator has, and the more staked in the Server, the larger the dividend the Validator will receive.


### Embeddings

Also referred to as representations, embeddings are a way of expressing information (i.e the comprehensible meaning of a word) as a very high-dimensional vector.


### Logits

The probability of a word in NTP (next token prediction) or MTP (masked token prediction).


### Next Token Prediction

Predicting an answer given a context before the place of prediction (i.e. predicting the next word in a sentence).

![logit/tokens](NextTokenPrediction.png)

### Masked Token Prediction

Predicting an answer given a context before and after the place of prediction (i.e. predicting the next word in a sentence).

![logit/tokens](MaskedTokenPrediction.png)

### Shapely Value

A measure of individuals' contributions in a cooperative game.


### Dataset

Bittensor uses a 1.5 Terrabyte corpus dataset for training known as the Mountain.


### Sigmoid Function

The sigmoid produces a threshold-like scaling that rewards connected peers and punishes the non-trusted.


### Chain Security

Connecting to the Polkadot infrastructure will offer greater network security. Polkadot takes the concept of validation security away from the chain so that the Polkadot relay chain is now responsible for security. Read more about [Polkadot security.](https://wiki.polkadot.network/docs/learn-security)