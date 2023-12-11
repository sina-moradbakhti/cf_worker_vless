# VLESS WebSocket Worker

This JavaScript file is designed to be used as a Cloudflare Worker to handle VLESS WebSocket connections. It provides a flexible way to connect clients to VLESS servers through Cloudflare, supporting both HTTP and WebSocket connections.

## Version Information

The current version of the script is based on commit `43fad05dcdae3b723c53c226f8181fc5bd47223e`. The timestamp for this version is `2023-06-22 15:20:02 UTC`.

## Usage

### UUID Generation

To generate your own UUID (Universally Unique Identifier):

- **Windows:**
  Open PowerShell and run the following command:
  ```powershell
  Powershell -NoExit -Command "[guid]::NewGuid()"

- **Mac/Linux:**
  Open Terminal and run the following command:
  ```Terminal
  uuidgen

## Configuration
Modify the following variables in the script according to your setup:

- userID: Your UUID generated using the instructions above.
- proxyIPs: An array of proxy IP addresses.
- dohURL: The URL for DNS over HTTPS (DoH) resolver.
- nodeId: The ID of the V2Board node.
- apiToken: Your V2Board API token.
- apiHost: The host of the V2Board API.
- Ensure that the isValidUUID function validates the correct format of your UUID.

## Run the Worker
Deploy this script as a Cloudflare Worker to handle VLESS WebSocket connections.

## Endpoints
The script handles different endpoints:

- /cf: Returns Cloudflare request information.
- /connect: For testing WebSocket connection to Cloudflare socket.
- /${userID}: Handles VLESS WebSocket connections.

**Important Notes**
`Make sure to set up your Cloudflare account properly with the necessary configurations.
Adjust the WebSocket connection logic based on your specific requirements.
VLESS Configuration
The script generates VLESS configuration links based on the hostname. Check the generated links and customize them as needed.`


## For CF-pages

```
CF-pages-vless+ws+tls Node:
vless://${userID}@skk.moe:8443?encryption=none&security=tls&type=ws&host=${hostName}&sni=${hostName}&fp=random&path=%2F%3Fed%3D2048#${hostName}
```

## For CF-workers
```
CF-workers-vless+ws Node:
vless://${userID}@skk.moe:8880?encryption=none&security=none&type=ws&host=${hostName}&path=%2F%3Fed%3D2048#${hostName}
```

## Troubleshooting
If you encounter any issues or errors, refer to the error messages in the responses and check your configuration settings.

## License
This script is provided under the MIT License.