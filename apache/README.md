## Apache
Deploys a simple web container

``` bash
sudo mkdir /opt/apache
sudo mkdir /opt/apache/website
sudo nano /opt/apache/compose.yaml
# copy compose.yaml
# copy your website into the website directory
cd /opt/apache
docker compose up -d
```