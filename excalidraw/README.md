## [Excalidraw](https://hub.docker.com/r/excalidraw/excalidraw)
1. Deploy:
    ``` bash
    mkdir ~/docker/containers/excalidraw -p
    nano ~/docker/containers/excalidraw/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/excalidraw/compose.yaml up -d
    ```
2. Access the UI at ```http://[server IP]:8080```.