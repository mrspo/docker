## speedtest-tracker
[Docker documentation](https://docs.linuxserver.io/images/docker-speedtest-tracker/)
[Speedtest Tracker documentation](https://docs.speedtest-tracker.dev/getting-started/installation/using-docker-compose)

1. Create a randomly generated key from the command line: ```echo -n 'base64:'; openssl rand -base64 32;``` and paste it in the compose file ```APP_KEY``` environment variable.
2. Deploy
    ```
    mkdir ~/docker/internet-speedtest-tracker
    nano ~/docker/internet-speedtest-tracker/compose.yaml
    [paste compose.yaml]
    cd ~/docker/internet-speedtest-tracker
    docker compose up -d
    ```
3. Access the interface at http://[server IP]:8443. The default credentials are ```admin@example.com```, ```password```