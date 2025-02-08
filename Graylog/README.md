## [Graylog](https://go2docs.graylog.org/current/downloading_and_installing_graylog/docker_installation.htm?tocpath=Install%20Graylog%7C_____2)
```
sudo mkdir /opt/graylog
sudo nano /opt/graylog/compose.yaml
[copy compose.yaml]
cd /opt/graylog
docker compose up -d
```

Generate a ```GRAYLOG_DATANODE_ROOT_PASSWORD_SHA2``` value by running:
```
echo -n "Enter Password: " && head -1 </dev/stdin | tr -d '\n' | sha256sum | cut -d" " -f1
```

Need to figure out the config