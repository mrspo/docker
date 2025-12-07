# Install Docker
```
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```
Log out and log back in

# Manage Docker containers
* Start container:
```
cd /path/to/container/dir
sudo nano compose.yaml
[enter Docker container config]
docker compose up -d
```
* List running containers: ```docker ps```
* Manage running containers: ```docker stop/start/restart [container ID or container name]```
* List images: ```docker images```
* Delete container: ```docker rm -f [container ID or container name]```
* Delete image: ```docker rmi [image ID]```
* List container info: ```docker inspect [container ID or container name]```
* Get container internal IP: ```docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' [container ID or container name]```
* Get command line on a running container: ```docker exec -t -i [container] /bin/bash```
* Update container:
```
docker pull [image name]
cd /path/to/container/dir
docker compose up -d --force-recreate
```
* Logs: ```docker logs [container ID or container name]```
