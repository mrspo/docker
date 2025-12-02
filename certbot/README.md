## Let's Encrypt Certbot
1. Deploy
    ``` bash
    mkdir ~/docker/containers/letsencrypt -p
    nano ~/docker/containers/letsencrypt/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/letsencrypt/compose.yaml up -d
    ```
2. Using [Certbot](https://eff-certbot.readthedocs.io/en/stable/using.html#getting-certificates-and-choosing-plugins):
    * Test the certification process: ```sudo certbot certonly -d yourdomain.com --dry-run```
    * Create a certificate: ```sudo certbot certonly -d yourdomain.com```
    * View your certificate: ```sudo cat /etc/letsencrypt/live/yourdomain.com/fullchain.pem```
    * View your private key: ```sudo cat /etc/letsencrypt/live/yourdomain.com/privkey.pem```