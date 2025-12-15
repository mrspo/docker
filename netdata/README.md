## Netdata
Easy system-level metrics, install via [Docker Compose](https://learn.netdata.cloud/docs/netdata-agent/installation/docker)

Deploy:
``` bash
mkdir ~/docker/containers/netdata/netdataconfig -p
mkdir ~/docker/containers/netdata/netdatalib
mkdir ~/docker/containers/netdata/netdatacache
nano ~/docker/containers/netdata/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/netdata/compose.yaml up -d
```

Open a browser to ```https://[server IP]:19999```