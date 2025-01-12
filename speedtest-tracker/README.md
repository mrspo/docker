## speedtest-tracker
**Note** this config is written for me based on my region and available ISPs - yours will be different. Follow [this guide](https://pimylifeup.com/docker-internet-speedtest-tracker/)
1. Copy a randomly generated key from the [self hosted speedtest tracker site](https://speedtest-tracker.dev/)
2. Deploy
    ```
    sudo mkdir /opt/internet-speedtest-tracker
    sudo nano /opt/internet-speedtest-tracker/compose.yaml
    [paste compose.yaml]
    ```
3. Access the interface at http://[server IP]:8443. The default credentials are admin@example.com, password