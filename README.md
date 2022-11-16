# Docker-compose files for personal my home server
This repo contains the docker compose files used to build my personal home server. The operating system used is debian. It consists of a jellyfin and *arr streaming and downloading stack to manage media, wireguard to host a vpn-server and a nextcloud-stack to host a personal cloud.

Folder structure used: 
```
data
├── torrents
│  ├── movies
│  ├── music
│  └── tv
└── media
   ├── movies
   ├── music
   └── tv
```

## Install
Make sure docker and docker-compose are installed and a docker user having the correct permissions. [My install script for docker](https://github.com/JaccoR/dockerinstallscript) takes care of this.

- Copy the contents of this repo to your servers srv folder with `git clone https://github.com/JaccoR/homeserver.git .`. Run `docker-compose up -d` in each of the directories. 
-  make sure the dockeruser has read and write permissions over the right directories. `chown -R dockeruser:dockeruser /srv/streaming-stack /srv/downloading-stack /data`
- Configure Jellyfin, Prowlarr, Sonarr, Radarr, Jellyseerr, Bazarr and Transmission by navigating to the webservers at the corresponding ports. Ports can be found in the docker-compose.yml files.

## Maintaining
- `docker-compose up -d` To update and recreate containers, config files are not deleted.
- `sudo docker system prune -a --volumes --force` Removes all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes