## Pi-hole
These instructions use a virtual NIC configuration to avoid overstepping port 80 on any other admin interfaces you might have running. If you have none, just follow the standard [Pi-hole documentation](https://docs.pi-hole.net/docker/). OMV has [separate instructions](https://github.com/pi-hole/docker-pi-hole?tab=readme-ov-file#quick-start) for running Pihole on the same server. Before deploying, pick an unused IP from your local network and assign it to the virtual NIC. macvlan will then create a virtual NIC in the container.

I run two instances of Pi-hole locally for redundancy, one from my OMV server and one from a regular server.

### Pi-hole on OMV
1. Install [OMV](https://docs.openmediavault.org/en/latest/installation/index.html)
    ```
    wget -O - https://raw.githubusercontent.com/OpenMediaVault-Plugin-Developers/installScript/master/install | sudo bash
    sudo reboot
    ```
2. Open a browser to http://[OMV IP]
3. Install the [OMV extras plugin](https://wiki.omv-extras.org/)
4. Install [Docker Compose](https://wiki.omv-extras.org/doku.php?id=omv7:docker_in_omv)
5. Create a new Compose file
6. Paste omv-compose.yaml
7. Save, and click the Up button
8. Open a browser to http://[virtual IP] to reach the admin console

### Pi-hole in standalone Docker
1. Create the container:
    ``` bash
    mkdir ~/docker/containers/pihole -p
    nano ~/docker/containers/pihole/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/pihole/compose.yaml up -d
    ```
2. Open a browser to http://[virtual IP] to reach the admin console

Set DNS on your devices to the virtual IP to begin using pi-hole