## [Plex](https://docs.linuxserver.io/images/docker-plex/#docker-compose-recommended-click-here-for-more-info)
1. Make a new user:
    ``` bash
    sudo adduser plex
    ```

2. Grab the UID/GID for ```plex``` user:
    ``` bash
    id plex
    ```

3. Deploy:
    ``` bash
    mkdir ~/docker/containers/plex/config -p
    nano ~/docker/containers/plex/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/plex/compose.yaml up -d
    ```
4. Access the first time setup from a computer, on ```http://[server IP]:32400/web```