## Gitea
[Docker Installation instructions](https://docs.gitea.com/installation/install-with-docker/)

1. Deploy:
    ``` bash
    mkdir ~/docker/containers/gitea/data -p
    mkdir ~/docker/containers/gitea/mysql
    nano ~/docker/containers/gitea/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/gitea/compose.yaml up -d
    ```
2. Access the web UI at ```http://[server IP]:3000```. The first time login presents a wizard to configure the database. The fields are pre-populated with the info in the compose file, just click **Install Gitea**.
3. Set up the first user/system administrator, and click **Register Account**. Password must be at least 8 characters.