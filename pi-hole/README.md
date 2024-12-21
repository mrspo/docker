### If running pihole from OMV with Docker Compose installed, use `omv-compose.yaml`:
1. Limit the DHCP scope of your internal network on your router
2. Pick an IP from outside this range and assign it to pihole in `omv-compose.yaml`
3. The Docker Compose file uses macvlan to assign a virtual NIC using this IP. This is all done so the port 80 interface for pihole doesn't interfere with the OMV interface

### If running pihole as a standalone Docker container (not compatible with OMV), use `local-compose.yaml`