
# Load Distrix

Load Distrix is a simple HTTP load balancer written in Go. It distributes incoming HTTP requests across multiple backend servers, ensuring high availability and fault tolerance. The load balancer uses a round-robin algorithm to cycle through the available backend servers, automatically retrying requests on failure and marking unresponsive servers as down.

## Features

- **Round-Robin Load Balancing:** Distributes requests evenly across backend servers.
- **Health Checks:** Continuously monitors the status of backend servers.
- **Automatic Retry:** Retries requests up to three times in case of failure.
- **Dynamic Server Pool:** Automatically adjusts to backend server availability.

## Requirements

- Go 1.16 or higher
- A configured JSON file named `LoadDistrix.config.json` with backend server details.

## Usage

1. Clone the repository:

   ```sh
   git clone https://github.com/muruga21/LoadDistrix.git
   cd loaddistrix
   ```

2. Prepare the configuration file:

   Create a `LoadDistrix.config.json` file in the root directory with the following structure:

   ```json
   {
       "backend": [
           {
               "host": "server1",
               "url": "http://127.0.0.1:8081"
           },
           {
               "host": "server2",
               "url": "http://127.0.0.1:8082"
           }
       ]
   }
   ```

3. Build and run the load balancer:

   ```sh
   go build -o loaddistrix main.go
   ./loaddistrix
   ```

4. The load balancer will start on port 8000. You can now send HTTP requests to `http://localhost:8000`, and they will be distributed across your configured backend servers.

## Configuration

The load balancer requires a JSON configuration file (`LoadDistrix.config.json`) to specify the backend servers. Each backend server should be specified with its `host` and `url`.

Example:

```json
{
    "backend": [
        {
            "host": "server1",
            "url": "http://127.0.0.1:8081"
        },
        {
            "host": "server2",
            "url": "http://127.0.0.1:8082"
        }
    ]
}
```

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.