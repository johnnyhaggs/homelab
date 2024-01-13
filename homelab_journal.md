# Docker Setup
Installed Docker Engine for Linux using these instructions https://docs.docker.com/engine/install/ubuntu/
* Also ran the systemctl commands to start Docker at bootup noted in the "post install" section.

2024/1/10:  
I unintalled docker engine and installed Docker Desktop using these instructions:
https://docs.docker.com/desktop/install/ubuntu/
I did this because I was getting errors in the multi-container tutorial about having "develop" / "watch" section in the compose.yaml file. I'm thinking running Docker Desktop will fix it since this is part of their instructions. Somewhere it warns you need to run ONLY Docker Desktop OR Docker Engine... so if I want to switch between the two I need to look up how to make sure one is killed. https://docs.docker.com/desktop/faqs/linuxfaqs/#what-is-the-difference-between-docker-desktop-for-linux-and-docker-engine

How to make Docker Desktop run at bootup (from https://docs.docker.com/desktop/install/ubuntu/):  
`systemctl --user enable docker-desktop`

# Caddy
2024/01/12:  
Followed instructions to get Caddy via Docker (https://caddyserver.com/docs/install)
Stored some placeholder config files in ~/workspace/caddy-files/ to play around with launching Caddy using `docker compose up -d`


# Nextcloud Setup
Installed Nextcloud using these All-In-One Docker Container instructions https://github.com/nextcloud/all-in-one#how-to-use-this

Docker command:
```
sudo docker run \
--init \
--sig-proxy=false \
--name nextcloud-aio-mastercontainer \
--restart always \
--publish 80:80 \
--publish 8080:8080 \
--publish 8443:8443 \
--volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config \
--volume /var/run/docker.sock:/var/run/docker.sock:ro \
nextcloud/all-in-one:latest
```

# SSH Setup
Installed openssh_server per these instructions
https://ubuntu.com/server/docs/service-openssh
Did not change sshd_config files.
`sudo systemctl restart sshd.service`
TODO: Setup keys for passwordless login.

# Tailscale
Started using Tailscale MagicDNS... still learning.
