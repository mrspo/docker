## [FileBrowser](https://filebrowser.org/installation.html#docker)
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
    mkdir ~/docker/containers/filebrowser/config -p
    mkdir ~/docker/containers/filebrowser/database
    nano ~/docker/containers/filebrowser/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/filebrowser/compose.yaml up -d
    ```

4. Open a browser to ```http://[server IP]```, login with default creds ```admin```, ```admin``` - change this in the settings.