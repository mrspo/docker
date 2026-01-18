### Install Docker (Linux):
``` bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```
Log out and log back in.

### Create a container with Docker Compose:
``` bash
mkdir ~/docker/containers/[container name] -p
nano ~/docker/containers/[container name]/compose.yaml
[save the Docker Compose config]
docker compose -f ~/docker/containers/[container name]/compose.yaml up
```
This will launch the container in the terminal and begins streaming the containers logs, which is helpful for debugging. Press ```D``` to switch the container to run in the background (detached mode). To start a container in detached mode, add ```-d``` to the end of the ```up``` command.

### Manage containers:
* Show: ```docker ps -a```
* Up/down: ```docker stop/start/restart [container name or ID]```
* Delete: ```docker rm -f [container name or ID]```
* List info: ```docker inspect [container name or ID]```
* Get a command line inside of a running container: ```docker exec -t -i [container name or ID] /bin/bash```
* Update:
    ``` bash
    docker pull [image name or ID]
    docker compose -f ~/docker/containers/[container name]/compose.yaml up -d
    ```
* See logs: ```docker logs [container name or ID] -f```

### Manage images:
* Show: ```docker images```
* Update: ```docker pull [image name or ID]```
* Delete: ```docker rmi [image name or ID]```
* Clean up unused images: ```docker image prune```