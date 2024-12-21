## frigate
1. Deploy Frigate:
```
sudo mkdir /opt/frigate
sudo mkdir /opt/frigate/config
sudo mkdir /opt/frigate/media
sudo nano /opt/frigate/compose.yaml
[paste compose.yaml]
cd /opt/frigate/
docker compose up -d
```
2. Grab the admin password from the logs:
```
docker logs frigate
```
3. Edit the camera config:
```
sudo nano /opt/frigate/config/config.yml
[paste config.yml]
docker compose up -d --force-recreate
```
4. Open a browser to https://[frigate server IP]:8971 and log in with username admin, password from Docker logs
5. Hopefully the camera works lol