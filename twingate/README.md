## Twingate
Run two connectors per server

1. Create a new connector in Twingate and copy the name, access token and refresh token. You will need them for the next steps.
2. Deploy first connector:
``` bash
mkdir ~/docker/containers/twingate-connector-1
sudo nano ~/docker/containers/twingate-connector-1/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/twingate-connector-1/compose.yaml up -d
```
3. Deploy second connector:
``` bash
mkdir ~/docker/containers/twingate-connector-2
sudo nano ~/docker/containers/twingate-connector-2/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/twingate-connector-2/compose.yaml up -d
```