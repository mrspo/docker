## [go2rtc](https://hub.docker.com/r/alexxit/go2rtc)
Among many other things, go2rtc restreams ffmpeg video (such as from a Raspberry Pi camera using MotionEye) as rtsp, which can be used with NVR apps like Frigate.

1. Deploy:
    ``` bash
    mkdir ~/docker/containers/go2rtc -p
    nano ~/docker/containers/go2rtc/go2rtc.yaml
    [copy go2rtc.yaml]
    nano ~/docker/containers/go2rtc/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/go2rtc/compose.yaml up -d
    ```
2. Access the web UI at ```http://[server IP]:1984```. You should see the two cameras you defined in ```go2rtc.yaml```. Click on the additional camera links to see all the restream options.
