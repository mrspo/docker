## Watchtower
[Github](https://github.com/nicholas-fedor/watchtower/)

According to the [quick start docs](https://watchtower.nickfedor.com/v1.14.1/quickstart/), the expected behavior is to check image updates every 24 hours and update containers automatically if a new version exists. You can change the default behavior with [arguments](https://watchtower.nickfedor.com/v1.14.1/configuration/arguments/), and add [notifications](https://watchtower.nickfedor.com/v1.14.1/notifications/overview/).

Deploy:
``` bash
mkdir ~/docker/containers/watchtower -p
nano ~/docker/containers/watchtower/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/watchtower/compose.yaml up -d
```

To use [Signal notifications](https://watchtower.nickfedor.com/v1.14.1/notifications/overview/#example_signal_configuration), add the additional environment variable:
```
- WATCHTOWER_NOTIFICATION_URL=signal://[signal cli server IP]:8080/+[signal account]/+[signal recipient]?disabletls=yes
```
