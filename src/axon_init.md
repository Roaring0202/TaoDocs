# Axon Module

The Axon module provides a factory class for the `bittensor.Axon` object, which creates a gRPC server for the Bittensor network, facilitating communication between neurons. The server protocol is defined in `bittensor.proto` and outlines how forward and backward requests are transported and encoded between validators and servers.

## Key Components

- **Axon Factory Class**: Creates a `bittensor.Axon` object from passed arguments.
- **Synapse Functions**: Axon supports various synapse functions for different types of requests (e.g., `forward_text`, `backward_text`, `synapse_last_hidden`, `synapse_causal_lm`, `synapse_causal_lm_next`, and `synapse_seq_2_seq`).
- **Timeouts**: Axon allows specifying timeouts for synapse functions and forward/backward requests.
- **Thread Pool and Server**: The module supports the use of a custom thread pool or gRPC server, and provides default options for both.
- **Blacklist and Priority**: Axon supports custom blacklist and priority functions for handling requests.
- **IP and Port Configuration**: The module allows for setting internal and external IP addresses and ports.

## Example Usage


## Additional Components

- **Wallet**: The Axon module supports the use of a custom wallet with hotkey and coldkeypub.
- **Compression**: Axon allows for setting different gRPC compression algorithms, such as gzip, deflate, or no compression.
- **Synapse Checks**: The module provides a default synapse check function and allows using a custom synapse check function.
- **Prometheus Level**: Axon allows specifying the prometheus level for monitoring.

## Configuration

The Axon module relies on a configuration object, which can be customized to modify various aspects of its behavior. The following options can be set:

- port: Binding port.
- ip: Binding IP.
- external_ip: The external IP of the server to broadcast to the network.
- external_port: The external port of the server to broadcast to the network.
- protocol: The protocol of the server to broadcast to the network.
- max_workers: Specifies the number of active threads servicing requests.
- maximum_concurrent_rpcs: Maximum allowed concurrently processed RPCs.
- forward_timeout: Timeout on the forward requests.
- backward_timeout: Timeout on the backward requests.
- compression: The gRPC compression algorithm to use.

## Customizing Axon

The Axon module is designed to be flexible and customizable. Users can provide their own implementations for various components, such as synapse functions, blacklist functions, priority functions, and check functions. By providing custom implementations, users can tailor Axon's behavior to better suit their needs.

## Advanced Usage

For more advanced use cases, users can create a custom gRPC server or thread pool and pass it to the Axon module. This allows for greater control over the server's behavior and resource allocation. Additionally, users can set custom timeouts for synapse functions, forward requests, and backward requests to control the response times of their Axon instances.

Overall, the Axon module provides a powerful and flexible framework for creating gRPC servers on the Bittensor network, allowing for seamless communication between neurons and enabling a wide range of applications.
