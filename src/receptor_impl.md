# Receptor Class from 
```bittensor/bittensor/_receptor/receptor_impl.py```

The Receptor class is responsible for managing a gRPC connection with a remote Bittensor neuron.

## Properties

- wallet: bittensor wallet with hotkey and coldkeypub.
- endpoint: neuron endpoint descriptor proto.
- channel: gRPC TCP channel.
- stub: bittensor protocol stub created from channel.
- receptor_uid: unique identifier for the receptor.
- semaphore: a threading.Semaphore object to limit concurrent processes.
- state_dict: dictionary of connectivity states.
- stats: a SimpleNamespace object containing various statistics for the Receptor.

## Methods

- **__init__**: Initializes a receptor gRPC connection.
- **__str__**: Returns a string representation of the Receptor object.
- **__repr__**: Returns the string representation of the Receptor object (same as `__str__`).
- **__del__**: Destructor for the Receptor object.
- **__exit__**: Exit method for the Receptor object.
- **sign**: Generates a signature string for the receptor.
- **nonce**: Creates a string representation of the time (monotonic_ns).
- **state**: Returns the current connectivity state of the receptor.
- **close**: Closes the Receptor connection.
- **forward**: Triggers the gRPC call to the remote endpoint.
- **backward**: Triggers the gRPC backward call to the remote endpoint.
- **async_forward**: Asynchronous version of the `forward` method.

### backward

Triggers the gRPC backward call to the remote endpoint, which triggers the synapse's backward calls with arguments. This method returns a list of output gradient tensors, one per synapse, along with their corresponding time and bittensor.proto.ReturnCode.

#### Arguments

- synapses: List of Bittensor synapse objects with arguments.
- inputs: Single torch tensor input corresponding to the linked forward call.
- grads: List of torch tensor gradients associated with each synapse.
- timeout: Request max timeout

#### Returns

- output: Result tensors (likely zero) from the backward call, each corresponding to a single forward input.
- codes: List of return codes associated with each passed synapse enum.
- times: List of times for each call associated with each passed synapse enum.

### async_forward

Asynchronous version of the `forward` method. Triggers the gRPC call to the remote endpoint and returns a list of output tensors, one per synapse, along with their corresponding time and bittensor.proto.ReturnCode.

#### Arguments

- synapses: List of Bittensor synapse objects with arguments.
- inputs: Single torch tensor to be sent to the remote endpoint.
- timeout: Request max timeout

#### Returns

- outputs: List of result tensors from the forward call, each corresponding to a passed synapse enum.
- codes: List of return codes associated with each passed synapse enum.
- times: List of times for each call associated with each passed synapse enum.

