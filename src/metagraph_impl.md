```bittensor/bittensor/_metagraph/metagraph_impl.py```
# Metagraph Class Overview
The `Metagraph` class is a subclass of `torch.nn.Module` that maintains chain state.
The Metagraph class provides a representation of the Bittensor metagraph.
```/bittensor/bittensor/_metagraph/__init__.py``` 
__If I am not mistaken, this .py script initiates the metagraph_impl.py file.__ 
## Properties

- Basic properties: version, n, tau, block, uids, stake, total_stake
- Rank-related properties: ranks, trust, consensus, validator_trust, incentive, emission, dividends
- Other properties: active, last_update, validator_permit, weights, bonds, endpoints, addresses, endpoint_objs

## Methods

- Initialization and update methods: __init__, from_tensor, update
- Getter methods: getitem, get, uid_to_hotkey, hotkey_to_uid
- Persistence methods: load, save, load_from_path, save_to_path, load_from_state_dict
- Syncing method: sync
- Data export methods: to_dataframe, to_wandb
- String representation methods: __str__, __repr__

### Properties

- **tau**: Current, per block, token emission rate.
- **block**: State block number.
- **uids**: UIDs for each neuron.
- **stake**: Stake balance for each neuron ordered by uid.
- **last_update**: Last emission call for each neuron ordered by uid.
- **weights**: Full weight matrix on chain ordered by uid.
- **neurons**: Tokenized endpoint information.

### Methods

- **__init__**: Initializes a new Metagraph torch chain interface object.
- **__info_state_dict_hook__**: Hook for state_dict to add info to state_dict, e.g., before saving.
- **clear**: Erases Metagraph state.

### Properties (Derived)

- **S**: Stake
- **R**: Rank
- **I**: Incentive
- **E**: Emission
- **C**: Consensus
- **T**: Trust
- **Tv**: Validator trust
- **D**: Dividends
- **B**: Bonds
- **W**: Weights
- **hotkeys**: Returns hotkeys for each neuron.
- **coldkeys**: Returns coldkeys for each neuron.
- **modalities**: Returns the modality for each neuron.

### Properties

- **addresses**: Returns IP addresses for each endpoint.
- **endpoint_objs**: Returns endpoints as objects.

### Methods

- **hotkey_to_uid**: Fetches the UID according to the hotkey.
- **load**: Loads the metagraph object's state_dict from Bittensor root directory.
- **save**: Saves the metagraph object's state_dict under Bittensor root directory.
- **load_from_path**: Loads the metagraph object with state_dict under the specified path.
- **save_to_path**: Saves the metagraph object's state_dict to the specified path.
- **load_from_state_dict**: Loads the metagraph object from the passed state_dict.
- **sync**: Synchronizes the metagraph with the chain state.
- **to_dataframe**: Converts the metagraph data to a pandas DataFrame.
- **to_wandb**: Returns metagraph information as a dictionary for Weights & Biases logging.
- **__str__**: Returns a string representation of the Metagraph object.
- **__repr__**: Returns the string representation of the Metagraph object (same as `__str__`).

