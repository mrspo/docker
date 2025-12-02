## Apache
Deploys a simple web container

1. Deploy
    ``` bash
    mkdir ~/docker/containers/apache/website -p
    nano ~/docker/containers/apache/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/apache/compose.yaml up -d
    ```

2. Copy your website files to ```~/docker/containers/apache/website```

3. Visit the running web page at ```http://[server IP]```