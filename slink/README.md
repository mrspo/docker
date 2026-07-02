## slink
[Slink: Image Sharing Platform](https://github.com/andrii-kryvoviaz/slink)

1. Deploy
    ``` bash
    mkdir ~/docker/containers/slink/data -p
    mkdir ~/docker/containers/slink/images
    nano ~/docker/containers/slink/compose.yaml
    [paste compose.yaml]
    docker compose -f ~/docker/containers/slink/compose.yaml up -d
    ```
2. Open a web browser to http://server:3000, click sign in, then click sign up, and create an account.
3. If `USER_APPROVAL_REQUIRED` is set to `true`, then you have to activate the account. From the server, run:
    ``` bash
    docker exec -it slink slink user:activate --email=<your-email>
    docker exec -it slink slink user:grant:role --email=<your-email> ROLE_ADMIN
    ```

    Alternatively, you can set `USER_APPROVAL_REQUIRED` to `false`, set up the account in the browser and sign in, then set `USER_APPROVAL_REQUIRED` to `true` in the `compose.yaml` config and recreate the container: `~/docker/containers/slink/compose.yaml up -d --force-recreate`

    OR you can add the optional flags in the compose file, which will automatically create the account, activate it, and set it as admin. It's recommended you remove these environment variables from the `compose.yaml` config once the container is created and you can log in, then recreate the container: `~/docker/containers/slink/compose.yaml up -d --force-recreate`.

    More information on first user setup [here](https://docs.slinkapp.io/getting-started/03-first-user-setup/).

4. To make it shareable outside your network, use an internet domain and a reverse proxy or Cloudflare tunnel and enter the domain in the `compose.yaml` config `ORIGIN` environment variable.

5. The `images` dir will grow as you put pictures in it, make sure there is sufficient disk space available - provide a directory on a different disk if necessary.