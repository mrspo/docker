## [Dozzle](https://dozzle.dev/)
Simple Docker log viewer UI

1. Generate `users.yaml` for admin account:
    ``` bash
    mkdir ~/docker/containers/dozzle/data -p
    docker run -it --rm amir20/dozzle generate [admin username] --password [superSecretPw] --email [your@email.com] --name [displayName]
    ```

    Copy the output, then save to `users.yaml`, and exit:
    ``` bash
    nano ~/docker/containers/dozzle/data/users.yaml
    ```

2. Deploy Dozzle server:
    ``` bash
    nano ~/docker/containers/dozzle/compose.yaml
    [copy server-compose.yaml]
    docker compose -f ~/docker/containers/dozzle/compose.yaml up -d
    ```

    Access the web interface at `http://[server IP]:8080`, sign in with the credentials you specified in the first step.

3. To monitor remote Docker host logs, deploy the Dozzle agent on the remote server:
    ``` bash
    mkdir ~/docker/containers/dozzle-agent -p
    nano ~/docker/containers/dozzle-agent/compose.yaml
    [copy agent-compose.yaml]
    docker compose -f ~/docker/containers/dozzle-agent/compose.yaml up -d
    ```

    Add each remote host to the server compose.yaml `DOZZLE_REMOTE_AGENT` environment variable, separated by commas.