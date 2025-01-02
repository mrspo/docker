## Pi-hole
These instructions use a virtual lan configuration so that port 80 doesn't overstep any other admin interfaces you might have on port 80. If you have none, just follow the standard Pi-hole documentation. To get started, pick an unused IP from your local DHCP range and assign it to the virtual NIC. The Docker Compose file uses macvlan to assign a virtual NIC using this IP.
```
sudo mkdir /opt/[pihole]
sudo nano /opt/pihole/compose.yaml
[copy compose.yaml]
cd /opt/pihole
docker compose up -d
```

Open a browser to http://[virtual IP]/admin to reach the admin interface

Set DNS on your devices to the virtual IP to begin using pi-hole