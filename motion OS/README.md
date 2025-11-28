## Setting up the MotionEye Cameras
Tested using Raspberry Pi Zero 2 W with Raspberry Pi OS Bookworm, and Raspberry Pi Camera Module 3

0. Update the Pi:
    ```
    sudo apt update && sudo apt full-upgrade -y
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

### Configure MotionEye Cameras
Open a browser to __http://[pi camera IP]:8765__ to reach the admin interface. The default user is _admin_ with no password - change this in the settings.

When you add the camera from the MotionEye admin interface, the camera module should be detected automatically. Configure the settings for the camera, streaming, authentication, etc. Make note of the streaming URL - you will need this in MotionOS setup. Test the streaming URL from a browser to make sure it works before moving on. The cameras should be configured to stream only.

## Deploy MotionOS
1. ```mkdir ~/docker/containers/motionos -p```
2. ```nano ~/docker/containers/motionos/compose.yaml```
3. Paste ```compose.yaml```
4. ```docker compose -f ~/docker/containers/motionos/compose.yaml up -d```

### Configure MotionOS
Open a browser to __http://[server IP]:8765__ to reach the admin interface. The default user is _admin_ with no password - change this in the settings.

Add each Pi camera as a network camera using the streaming URL from the camera interface. If you mounted local storage to the container, this is where video recordings are saved when __Movies__ settings are configured.