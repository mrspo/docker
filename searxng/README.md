## SearXNG
[Self hosted meta-browser](https://docs.searxng.org/) which aggregates your web searches across multiple search engines, but with user tracking data obfuscated so you can't be profiled.

1. Deploy:
``` bash
mkdir ~/docker/containers/searxng/config -p
mkdir ~/docker/containers/searxng/data
nano ~/docker/containers/searxng/compose.yaml
[copy compose.yaml]
docker compose -f ~/docker/containers/searxng/compose.yaml up -d
```
2. Open a browser to ```http://[server IP]:8080``` and begin searching.
3. Customize the logo (optional): save a 640 x 110 .png file to ```~/docker/containers/searxng``` and map it to ```searxng.png``` in the Compose file.
4. Make it publicly available (optional): you may follow the [searxng-docker documentation](https://github.com/searxng/searxng-docker) for publishing your SearXNG instance on the internet. Furthermore you can add it to list of [public SearXNG servers](https://searx.space/). I was unable to follow the instructions using a Cloudflare tunnel so I just added a published application route to my local instance like I do for all my other services and it works. Check it out at [fucktracking.com](https://fucktracking.com), just don't make me regret it lol.