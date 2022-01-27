# docker-config
Docker configuration set-up for PiHole.

## Set up Portainer

https://docs.portainer.io/v/ce-2.11/start/install/server/docker/linux \
https://hub.docker.com/r/portainer/portainer-ce

```
docker volume create portainer_data
sudo docker run \
    -d \
    -p 9443:9443 \
    --name=portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce
```

Browse to https://HOSTNAME:9443/ for setup.

## PiHole

https://hub.docker.com/r/pihole/pihole \
https://github.com/pi-hole/docker-pi-hole/ \
https://docs.pi-hole.net/

```
sudo mkdir -p /etc/pihole/etc
sudo mkdir -p /etc/pihole/dnsmasq.d
sudo chown -R `id -u $USER`:`id -g $USER` /etc/pihole
```

[docker\_compose.yml](docker-compose.yml)

Define environment variable for `WEBPASSWORD`.
