## Ollama
1. Deploy
    ``` bash
    mkdir ~/docker/containers/ollama
    nano ~/docker/containers/ollama/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/ollama/compose.yaml up -d
    ```
2. Open a browser to ```http://[server IP]:11434```