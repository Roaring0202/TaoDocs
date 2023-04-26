# GenesisTextDataset

## This is a summary of Functions found within - 
```bittensor/bittensor/_dataset/dataset_impl.py```
## __To give a high level overview of what this script does:__ 

`GenesisTextDataset` is a class designed to handle text datasets for training language models. It uses IPFS (InterPlanetary File System) as a source for the text data and allows the user to load data from IPFS or a local directory. It provides methods to create a PyTorch DataLoader, reserve text data, and update the data size.

## Key Functions

### construct_text_corpus

This function generates the text data by getting directories from a random dataset hash and picking a random directory to get the text from. It repeats this process until the minimum data length is reached.

### reserve_multiple_data

This function reserves the data to ensure that it meets the specified multiple of the dataset size. If not, it keeps constructing text corpus until the required size is met.

### set_data_size

This function updates the size of data (batch_size, block_size) required for the DataLoader.

### dataloader

This function creates a PyTorch DataLoader from a subclass of this class, using the reserved data and the specified data size.

### set_dataset_iterator

This function gets a new dataset from the data queue and updates the `__infinite_dataset_iterator__` attribute.

### __next__

This method returns the next element from the dataset.

### __len__

This method returns the number of samples (blocks) of the dataset.

### __getitem__

This method returns a block of sentences from the text dataset at a given index.

### build_hash_table

This function builds a hash table with dataset hashes and metadata.


## Dataset class

Implements a dataset class that handles data loading from IPFS. Key methods include:

- `requests_retry_session`: Creates a retriable session for request calls, enabling automatic retries and back-off retries should any request calls fail.

- `get_ipfs_directory`: Connects to IPFS gateway and retrieves a directory, returning a dictionary of the files inside of the genesis_datasets and their hashes.

- `__len__`: Returns the length of the dataset that the dataset is processing.

- `__getitem__`: Returns the next batch from the dataset.

## GenesisTextDataset class

Inherits from the Dataset class and caters for data from IPFS. Key features include:

- **Initialization**: Initializes important attributes like block_size, batch_size, num_workers, tokenizer, dataset_names, data_dir, save_dataset, and others.

- Ensures dataset_names is formatted correctly, removing invalid datasets.

- Retrieves a random slice of the genesis dataset.

- Builds a hash table.

- Creates a ThreadQueue instance for a data queue, which reserves multiple data in batches.

- `__del__` and `close`: Close the data queue.

- `get_folder_size`: Get the size (in bytes) of a folder inside the data_dir.

- `load_hash`: Load a hash from disk, returning the text in the file.

- `save_hash`: Save a hash to disk, taking a file_meta dictionary and text as input.

- `get_text`: Either load a file from disk or download it from IPFS, returning the text from the file.

- `get_dataset`: Either load a dataset (a list of hashes) from disk or download it from IPFS.

- `get_hashes_from_dataset`: Get directories, where a directory could lead to a data file or a directory file, returning a list of directories (random directory that leads to a data file).

- `get_root_text_hash`: With recursion, get a random directory that leads to a data file from the given directory.

- `get_text_from_local`: Load text data from the local data directory, returning a list of text data.

- `construct_text_corpus`: Main function for generating the text data, returning the text corpus.

- `reserve_multiple_data`: Make sure the reserved data meet the given multiples. If not, keep constructing the text corpus.

- `set_data_size`: Update the size of data (batch_size, block_size) that is needed.

- `dataloader`: Creates a torch dataloader out of a subclass of this class.

- `set_dataset_iterator`: Get a new dataset that is ready from the queue. The result is updated to `self.__infinite_dataset_iterator__`.

- `__next__`: Returns the next element from the dataset.

- `__len__`: Returns the number of samples (blocks) of the dataset.

- `__getitem__`: Returns a block of sentences from the text dataset.

- `build_hash_table`: Builds a hash table containing dataset hashes.


