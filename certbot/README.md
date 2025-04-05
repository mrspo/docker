## Let's Encrypt Certbot
1. Deploy the container:
    ``` bash
    sudo mkdir /opt/letsencrypt
    sudo nano /opt/letsencrypt/compose.yaml
    [copy compose.yaml]
    docker compose -f /opt/letsencrypt/compose.yaml up -d
    ```
2. Using [Certbot](https://eff-certbot.readthedocs.io/en/stable/using.html#getting-certificates-and-choosing-plugins):
    * Test the certification process: ```sudo certbot certonly -d yourdomain.com --dry-run```
    * Create a certificate: ```sudo certbot certonly -d yourdomain.com```
    * View your certificate: ```sudo cat /etc/letsencrypt/live/yourdomain.com/fullchain.pem```
    * View your private key: ```sudo cat /etc/letsencrypt/live/yourdomain.com/privkey.pem```