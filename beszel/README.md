## Beszel
[Getting started docs](https://beszel.dev/guide/getting-started)

1. Deploy Beszel server:
    ``` bash
    mkdir ~/docker/containers/beszel -p
    nano ~/docker/containers/beszel/compose.yaml
    [copy ONLY the server section of server-compose.yaml for now]
    docker compose -f ~/docker/containers/beszel/compose.yaml up -d
    ```
2. Open a browser to `http://[server IP]:8090`, create an admin account, and sign in
3. (optional) Set universal token - this makes it easier to add Beszel agents to your hosts: click Settings > Tokens & Fingerprints, toggle `Universal token`, and set persistence to `permanent`.
4. (for Raspberry Pi OS) Add CPU/memory cgroups, necessary if you want to view Docker CPU/memory data from Beszel:
    ``` bash
    sudo nano /boot/firmware/cmdline.txt
    ```
    Add this to the end, save, and exit:
    ```
    cgroup_enable=cpuset cgroup_enable=memory cgroup_memory=1
    ```
    Reboot:
    ``` bash
    sudo reboot
    ```
5. Deploy Beszel agent to the Beszel server: in the UI click `+Add System`, provide the server name and set the host/IP to `/beszel_socket/beszel.sock`, then click the button to `copy Docker Compose`, then click `Add system`.

    Deploy:
    ``` bash
    nano ~/docker/containers/beszel/compose.yaml
    [add the copied docker compose under the server section, which should match server-compose.yaml]
    docker compose -f ~/docker/containers/beszel/compose.yaml up -d
    ```
    The container will recreate and the server should appear online in the Beszel dashboard.
6. Deploy Beszel agent to all other servers: if you set a universal token, you can deploy the agent on all the servers with the same Docker Compose config, without also having to add the system in the UI:
    ``` bash
    mkdir ~/docker/containers/beszel
    nano ~/docker/containers/beszel/compose.yaml
    [copy agent-compose.yaml, using your Beszel key and universal token]
    docker compose -f ~/docker/containers/beszel/compose.yaml up -d
    ```
    The server should appear online in the Beszel dashboard automatically.
7. (optional) Add Signal notifications: in the UI, click Settings > Notifications > Webhook/Push notifications > +Add URL, paste the [Shoutrrr](https://github.com/containrrr/shoutrrr) string for Signal - requires hosting the [Signal CLI app](/uptime%20kuma/README.md):
    ```
    signal://[signal server IP]:8080/+[signal account]/+[signal recipient]?disabletls=yes
    ```