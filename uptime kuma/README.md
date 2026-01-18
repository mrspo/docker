Stand up [Uptime Kuma](https://github.com/louislam/uptime-kuma), and a [Signal CLI REST API](https://github.com/bbernhard/signal-cli-rest-api) client to use for sending monitoring alerts using [Signal](https://signal.org/)

## Uptime Kuma
1. Create folders and Compose file
    ``` bash
    mkdir ~/docker/containers/uptime-kuma/data -p
    nano ~/docker/containers/uptime-kuma/compose.yaml
    ```
2. Copy and paste ```uptime-kuma-compose.yaml```, save, and exit
3. Deploy the container
    ``` bash
    docker compose -f ~/docker/containers/uptime-kuma/compose.yaml up -d
    ```
3. Open a web browser to **http://[server IP]:3001**

## Signal CLI REST API Client
1. Create folders and Compose file
    ``` bash
    mkdir ~/docker/containers/signal-cli/config -p
    nano ~/docker/containers/signal-cli/compose.yaml
    ```
2. Copy and paste ```signal-cli-compose.yaml```, save, and exit
3. Deploy the container
    ``` bash
    docker compose -f ~/docker/containers/signal-cli/compose.yaml up -d
    ```
4. Query the API (can be done from the server, or from another device)
    ``` bash
    curl -X 'GET' 'http://[signal client IP]:8080/v1/about' -H 'accept: application/json'
    ```
5. Generate a Signal device registry QR code
    ``` bash
    curl -X 'GET' 'http://[signal client IP]:8080/v1/qrcodelink?device_name=[device name]' -H 'accept: application/json'
    ```
    **NOTE** - you may receive response ```error: "Couldn't create QR code: no data to encode"```. If so, try a different ```MODE``` option in ```compose.yaml```

6. Register the device with your Signal app:
    * Tap your user icon > Linked Devices > Link a new device
    * Scan the QR code
    * Tap Add device
7. See [Signal Swagger site](https://bbernhard.github.io/signal-cli-rest-api/) for usage information

## Add Signal notifications to Uptime Kuma
1. From the Uptime Kuma console, click the upper right menu button > Settings > Notifications, and click Setup Notification
2. Input these options:
    * Notification type: Signal
    * Friendly Name: [your device name]
    * Post URL: ```http://[signal client IP]:8080/v2/send```
    * Number: [the phone number associated to the Signal account]
    * Recipients: [phone number recipient]
3. Click Test to send a message verifying functionality. You should receive a Signal message: ```[friendly name] Testing```
4. Click Save
5. Add notifications to your monitors by toggling the friendly device name in the Notifications settings. Alerts should arrive by Signal message.