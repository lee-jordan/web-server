# Tools
apt install nginx docker.io net-tools software-properties-common certbot python3-certbot-nginx docker-compose

# Docker enable
sudo systemctl enable --now docker

# Setup
rm /etc/nginx/sites-enabled/default

# Docker
docker network create <networkName>

# Ghost
docker run -dit --network <networkName> ghost

# Docker Inspect
docker ps
docker inspect <containerName>

# Nginx
nano /etc/nginx/conf.d/domain.tld.conf

```
server {
    listen 80;
    listen [::]:80;
 
    server_name yourdomainname.tld;
 
    location / {
        proxy_pass http://IP of docker container/;
        proxy_buffering off;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

nginx -t
service nginx reload

# Certbot
certbox --nginx




# Portainer
docker run -d --network leejordan.dev --name portainer --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

```
server {
    listen 80;
    listen [::]:80;
 
    server_name yourdomainname.tld;
 
    location / {
        proxy_pass http://IP of docker container:9000/;
        proxy_buffering off;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

service nginx reload
certbox --nginx
