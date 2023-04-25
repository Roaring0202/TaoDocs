# IP Address Utility Script - ```bittensor/bittensor/utils/networking.py```

This script provides a set of utility functions to help you work with IP addresses, automatically detect your external IP address, set up port forwarding using the Universal Plug and Play (UPnP) protocol, and format WebSocket URLs. It is designed to simplify common networking tasks for users without extensive knowledge in networking.

## Key Functions

1. **IP address conversion**: Convert IP addresses between their string and integer representations.
   - `int_to_ip(int_val: int) -> str`: Converts an integer to an IP address string.
   - `ip_to_int(str_val: str) -> int`: Converts an IP address string to an integer.

2. **IP version detection**: Determine if a given IP address is IPv4 or IPv6.
   - `ip_version(str_val: str) -> int`: Returns the IP version (4 or 6) of a given IP address string.

3. **Formatted IP string**: Create a formatted IP string including the IP type, IP address, and port.
   - `ip__str__(ip_type:int, ip_str:str, port:int)`: Returns a formatted IP string.

4. **External IP address detection**: Automatically find your router's external IP address using various methods.
   - `get_external_ip() -> str`: Tries multiple methods to obtain the external IP address of the router and returns it as a string.

5. **UPnP port mapping**: Set up port forwarding on your router using the UPnP protocol.
   - `upnpc_create_port_map(port: int)`: Creates a UPnP port map on the router from the provided external port to the local port.

6. **WebSocket URL formatting**: Format WebSocket URLs for proper use in applications.
   - `get_formatted_ws_endpoint_url(endpoint_url: str) -> str`: Returns a formatted WebSocket endpoint URL.

## Custom Exceptions

The script defines two custom exception classes that are raised when specific issues occur:

1. `ExternalIPNotFound`: Raised when the script cannot find the external IP address using any of the available methods.
2. `UPNPCException`: Raised when there are issues with UPnP port mapping, such as when UPnP is not enabled on the router.

By using this script, users who are not well-versed in networking can easily perform tasks related to IP addresses and networking without diving deep into the technical details.
