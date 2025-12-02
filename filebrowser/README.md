## FileBrowser
1. Make a new user:
    ``` bash
    sudo adduser filebrowser
    ```

2. Grab the UID/GID for ```filebrowser``` user:
    ``` bash
    id filebrowser
    ```

3. Deploy:
    ``` bash
    mkdir ~/docker/containers/filebrowser -p
    nano ~/docker/containers/filebrowser/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/filebrowser/compose.yaml up -d
    ```

4. Login to the admin portal with default creds ```admin```, ```admin```