## Pi-hole
1. Limit the DHCP scope of your internal network on your router
2. Pick an IP from outside this range and assign it to the virtual NIC. The Docker compose file uses macvlan to assign a virtual NIC using this IP. This is all done so the port 80 interface for pihole doesn't interfere with the OMV interface
3. Open a browser to the pi-hole IP to reach the admin interface