## Portainer
Deploy [Portainer](https://docs.portainer.io/) server Community Edition via [Docker Compose](https://docs.portainer.io/start/install-ce/server/docker/linux#docker-compose). Then, manage additional standalone Docker environments by deploying the [Portainer agent](https://docs.portainer.io/admin/environments/add/docker/agent) container via Docker Compose (rather than using the command in the *Add Environment* wizard). I prefer to run the agent using Compose, this is not required.

### Install Portainer Server
Deploy Portainer container:
``` bash
mkdir ~/docker/containers/portainer -p
nano ~/docker/containers/portainer/portainer-server-compose.yaml
[copy portainer-server-compose.yaml]
docker compose -f ~/docker/containers/portainer/portainer-server-compose.yaml up -d
```

Access the admin interface at ```https://[server IP]:9443```. 

### Install Portainer Agent
Deploy the Portainer agent any remote server also running Docker containers that you wish to manage:
``` bash
mkdir ~/docker/containers/portainer-agent -p
nano ~/docker/containers/portainer/portainer-agent-compose.yaml
[copy portainer-agent-compose.yaml]
docker compose -f ~/docker/containers/portainer/portainer-agent-compose.yaml up -d
```

### Add Standalone Docker Host
When you [add a standalone Docker host](https://docs.portainer.io/admin/environments/add/docker), provide the instance name and server IP in the wizard, then click *Connect* and it will connect to the Portainer agent automatically.