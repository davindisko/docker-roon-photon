# Docker for Roon using Photon OS

**Unstable, and not fully functional. Only for testing purposes, still working on it**

Docker container for [Roon], based on Photon OS linux
Based on the great work of [steefdebruijn] who did the same from a debian-slim image.
All informations to troubleshoot your linux server can be found [here]

## Differences
- ffmpeg is installed manually from official sources
- Uses local volumes for app, data, music and backups folders
- Using Photon OS linux results on a lighter image (approx. 290 Mo)
- For now, debian:12-slim seems to run faster, I have to do further tests and maybe tweek a little bit the system

Be careful, this is for test purpose only

## Not working
- Roon ARC, testing Tailscale on the way

## Steps
- First clone the repo
- Change TZ param in docker-compose.yaml
- Uncomment privileged if you encounter problems with network mounts

## Run container with docker compose
```sh
docker-compose up -d
```

## Run container
```sh
docker run -d \
  --net=host \
  -e TZ="Europe/Paris" \
  -v ./app:/app \
  -v ./data:/data \
  -v ./music:/music \
  -v ./backups:/backup \
  davindisko/roon-photon:latest
```

[steefdebruijn]: <https://github.com/steefdebruijn/docker-roonserver>
[roon]: <https://roonlabs.com>
[here]: <https://help.roonlabs.com/portal/en/kb/articles/linux-install>