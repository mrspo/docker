## Twingate
Run two connectors per server

1. Create a new connector in Twingate and copy the name, access token and refresh token. You will need them for the next steps.
2. Deploy first connector:
```
sudo mkdir /opt/twingate-connector-1
sudo nano /opt/twingate-connector-1/compose.yaml
[copy compose.yaml]
cd /opt/twingate-connector-1
docker compose up -d
```
3. Deploy second connector:
```
sudo mkdir /opt/twingate-connector-2
sudo nano /opt/twingate-connector-2/compose.yaml
[copy compose.yaml]
cd /opt/twingate-connector-2
docker compose up -d
```