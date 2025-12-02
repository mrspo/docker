## Setting up Frigate server and cameras
_Note:_ this is for Hailo 8L configuration and an external MotionEye camera config

1. Deploy:
    ``` bash
    mkdir ~/docker/containers/frigate -p
    mkdir ~/docker/containers/frigate/config
    mkdir ~/docker/containers/frigate/media
    nano ~/docker/containers/frigate/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/frigate/compose.yaml up -d
    ```
2. Grab the admin credentials from the logs:
    ``` bash
    docker logs frigate
    ```
3. Edit the camera config:
    ``` bash
    sudo nano ~/docker/containers/frigate/config/config.yml
    [copy config.yml]
    docker compose -f ~/docker/containers/frigate/compose.yaml up -d --force-recreate
    ```
4. Open a browser to ```https://[frigate server IP]:8971``` and log in with credentials from Docker logs
5. Hopefully the camera works lol