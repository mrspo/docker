## n8n
If you want to run [n8n](https://n8n.io/) with a [Cloudflare tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) and custom domain, you're gonna have a bad time using the [n8n Docker documentation](https://docs.n8n.io/hosting/installation/server-setups/docker-compose/) because the Traefik container is configured to use a TLS challenge to validate the domain name, which is not compatible with the Cloudflare tunnel. This configuration is updated to work with Cloudflare using a DNS challenge instead.

Prerequisites: custom domain registered with Cloudflare, Cloudflare tunnel, [Cloudflare API token](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/) with edit DNS privileges for your domain

1. Set up the container:
    ```
    mkdir ~/docker/containers/n8n/local-files -p
    nano ~/docker/containers/n8n/compose.yaml
    ```

    Add ```compose.yaml```, save, and exit

2. Create the n8n env file:
    ```
    nano ~/docker/containers/n8n/.env
    ```

    Add ```.env```, save, and exit

3. From the [Cloudflare Zero Trust dashboard](https://one.dash.cloudflare.com), add a published application route to your tunnel:
    * **Subdomain**: n8n
    * **Domain**: [yourdomain.com]
    * **Service Type**: HTTPS
    * **Service URL**: [n8n server IP]
    * **Additional application settings** > **TLS**, turn on **No TLS Verify**

4. Start the container: ```docker compose -f ~/docker/containers/n8n/compose.yaml up -d```
5. n8n should be available from the public internet at ```n8n.yourdomain.com```