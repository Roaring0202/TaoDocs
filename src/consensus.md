# Bittensor Consensus Overview

Consensus in the Bittensor network is essential for maintaining a decentralized, distributed network's integrity and security. It involves reaching an agreement among participating nodes on the state of the network, particularly the weights assigned to each miner.

## Key Components of Consensus

1. **Weight updates**: Agreement on weight updates for each miner, representing their contribution to the network.
2. **Metagraph**: Data structure that keeps track of the miners' weights and stake, updated as part of the consensus process.
3. **Weight normalization**: Ensuring that the total weight in the network remains constant by normalizing weight updates.
4. **Block validation**: Validators (miners) propose and validate blocks containing weight updates in the PoS-based consensus.
5. **Staking**: Validators (miners) stake Subtensor tokens to participate in the consensus process, incentivizing honest behavior.

