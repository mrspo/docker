## Setting up the MotionEye Cameras
0. Update the Pi:
    ```
    sudo apt update
    sudo apt full-upgrade -y
    ```
1. Install dependencies:
    ```
    sudo apt install python3-dev libcurl4-openssl-dev libssl-dev python3-pip libcamera-v4l2 libcamera-tools -y
    ```
2. Install MotionEye. ```--break-system-packages``` is required for python3:
    ```
    sudo pip3 install 'https://github.com/motioneye-project/motioneye/archive/dev.tar.gz' --break-system-packages
    ```
3. Initialize MotionEye:
    ```
    sudo motioneye_init
    ```
4. Update the service file to use libcamera and restart MotionEye:
    ```
    sudo nano /etc/systemd/system/motioneye.service
    ```
    Find this line...
    ```
    ExecStart=/usr/local/bin/meyectl startserver -c /etc/motioneye/motioneye.conf
    ```
    ...and replace it with this, save, and exit:
    ```
    ExecStart=/usr/bin/libcamerify /usr/local/bin/meyectl startserver -c /etc/motioneye/motioneye.conf
    ```
    Restart the systemctl daemon and MotionEye:
    ```
    sudo systemctl restart motioneye
    sudo systemctl daemon-reload
    ```
5. Load the bcm module at next boot ([required for Camera Module 3 and Pi Zero 2](https://github.com/motioneye-project/motioneyeos/issues/288)):
    ```
    sudo nano /etc/modules
    ```
    Add this to the bottom, save and exit:
    ```
    bcm2835-v4l2
    ```
6. Reboot
    ```
    sudo reboot
    ```

Detect local camera:
```
libcamera-vid --list-cameras
```

### Accessing MotionEye Cameras
Open a browser to __http://[pi camera IP]:8765__ to reach the admin interface. The default user is _admin_ with no password - change this in the settings.

If everything went well, the camera will be detectable by Motioneye. Configure the interface, camera, streaming, authentication, etc. settings. Make note of the streaming path - you will need this in the Frigate configuration. You can test the stream by opening VLC Media Player > Media > Open network stream... and entering the path from the MotionEye config.

## Setting up Frigate server and cameras
_Note:_ this is for Hailo 8L configuration and an external MotionEye camera config

1. Deploy Frigate:
```
sudo mkdir /opt/frigate
sudo mkdir /opt/frigate/config
sudo mkdir /opt/frigate/media
sudo nano /opt/frigate/compose.yaml
[paste compose.yaml]
cd /opt/frigate/
docker compose up -d
```
2. Grab the admin password from the logs:
```
docker logs frigate
```
3. Edit the camera config:
```
sudo nano /opt/frigate/config/config.yml
[paste config.yml]
docker compose up -d --force-recreate
```
4. Open a browser to https://[frigate server IP]:8971 and log in with username admin and password from Docker logs
5. Hopefully the camera works lol