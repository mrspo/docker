## MariaDB
Deploy a new db:
``` bash
mkdir ~/docker/containers/mariadb -p
nano ~/docker/containers/mariadb/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/mariadb/compose.yaml up -d
```