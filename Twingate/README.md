## Twingate
Run two connectors per server
1. Deploy first connector:
```
sudo mkdir /opt/twingate-connector-1
sudo nano /opt/twingate-connector-1/compose.yaml
[copy connector1-compose.yaml]
cd /opt/twingate-connector-1
docker compose up -d
```
2. Deploy other connector:
```
sudo mkdir /opt/twingate-connector-2
sudo nano /opt/twingate-connector-2/compose.yaml
[copy connector1-compose.yaml]
cd /opt/twingate-connector-2
docker compose up -d
```