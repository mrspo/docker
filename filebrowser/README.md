### FileBrowser
1. Make a new user:
```
sudo adduser filebrowser
```

2. Grab the UID/GID for ```filebrowser``` user:
```
id filebrowser
```

3. Deploy:
```
sudo mkdir /opt/filebrowser
sudo nano /opt/filebrowser/compose.yaml
[copy compose.yaml]
cd /opt/filebrowser
docker compose up -d
```

4. Login to the admin portal with default creds ```admin```, ```admin```