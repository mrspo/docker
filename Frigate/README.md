## Setting up the [MotionEye](https://raspberrytips.com/install-motioneye-on-raspberry-pi/) Cameras
1. Install dependencies:
```
sudo apt install python3-dev libcurl4-openssl-dev libssl-dev -y
sudo apt install python3-pip -y
```
2. Install MotionEye. ```--break-system-packages``` is required for Bookworm OS:
```
sudo pip3 install 'https://github.com/motioneye-project/motioneye/archive/dev.tar.gz' --break-system-packages
```
3. Initialize MotionEye:
```
sudo motioneye_init
```
4. Install the libcamera package:
```
sudo apt install libcamera-v4l2
```
5. Update the service file to use it:
```
sudo sed -i 's/\/usr\/local\/bin\/meyectl/\/usr\/bin\/libcamerify \/usr\/local\/bin\/meyectl/' /etc/systemd/system/motioneye.service
```
6. Restart MotionEye:
```
sudo systemctl restart motioneye
```
7. Load the bcm module at next boot ([required for Camera Module 3 and Pi Zero 2](https://github.com/motioneye-project/motioneyeos/issues/288)):
    ```
    sudo nano /etc/modules
    ```
    Add this to the bottom, save and exit:
    ```
    bcm2835-v4l2
    ```
    Reboot
8. Detect local camera:
```
libcamera-vid --list-cameras
```

### Accessing MotionEye Cameras
Open a browser to __http://[pi IP]:8765__ to reach the admin interface. The default user is _admin_ with no password - change this in the settings.

Configure camera, streaming, and authentication settings and make note of the streaming path - you will need this in the Frigate configuration. You can test the stream by opening VLC Media Player > Media > Open network stream... and entering the path from the MotionEye config.

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