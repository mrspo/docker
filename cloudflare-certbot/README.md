## Let's Encrypt Cloudflare Certbot
The [Github page](https://github.com/serversideup/docker-certbot-dns-cloudflare) has additional configuration information. This is the minimun requirement to set up an automated Certbot container for your website where DNS is managed by Cloudflare.

1. Create a Cloudflare [account API token](https://developers.cloudflare.com/fundamentals/api/get-started/account-owned-tokens) with permissions to edit DNS zones. 

2. Deploy the certbot:
    ``` bash
    mkdir ~/docker/containers/cloudflare-certbot/etc -p
    mkdir ~/docker/containers/cloudflare-certbot/lib
    mkdir ~/docker/containers/cloudflare-certbot/log
    cd ~/docker/containers/cloudflare-certbot
    sudo chown root:root etc/ lib/ log/
    sudo chmod 0755 etc/ lib/ log/
    nano ~/docker/containers/cloudflare-certbot/compose.yaml
    [copy compose.yaml]
    docker compose -f ~/docker/containers/cloudflare-certbot/compose.yaml up
    ```

    The container will start, then reach out to Cloudflare to validate the domain and API credentials, and if successful it will generate certificates and keys at `~/docker/containers/cloudflare-certbot/etc/live/[yourSite.com]`
3. The container will run in the background and issue new certificates when they are 30 days from expiring, and email the specified address.