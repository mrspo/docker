## Syncthing
Syncthing [Docker documentation](https://github.com/syncthing/syncthing/blob/main/README-Docker.md)
1. Make a new user:
    ```
    sudo adduser syncthing
    ```

2. Grab the UID/GID for ```syncthing``` user:
    ```
    id syncthing
    ```

3. Deploy:
    ```
    mkdir ~/docker/containers/syncthing -p
    nano ~/docker/containers/syncthing/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/syncthing/compose.yaml up -d
    ```

4. Login to the admin portal at ```https://[server IP]:8384```