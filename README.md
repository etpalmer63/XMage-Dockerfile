# XMage-Dockerfile
Credit to: https://github.com/mage-docker/xmage-beta-docker


A slight modification on the Docker container for XMage-beta from
[goesta](https://github.com/goesta). I found including the
script file in the Docker build simplified the process.

## Basic Usage

```
docker run --rm -it \
    -p 17171:17171 \
    -p 17179:17179 \
    --add-host example.com:0.0.0.0 \
    -e "XMAGE_DOCKER_SERVER_ADDRESS=example.com" \
    erikt63/xmage-beta-two:latest
```

I used a droplet from Digital Ocean as recommended by the original
author in [these instructions](https://github.com/goesta/docker-xmage-alpine/wiki/DigitalOcean-Tutorial#running-xmage-on-digitalocean).

## Troubleshooting

### Server Connection Issues

The play experience seems best when the container is running in detached mode.
So I suggest adding the `--detach` or `-d` flag, as in:

```
docker run --rm --detach \
    -p 17171:17171 \
    -p 17179:17179 \
    --add-host example.com:0.0.0.0 \
    -e "XMAGE_DOCKER_SERVER_ADDRESS=example.com" \
    erikt63/xmage-beta-two:latest
```

### Server stalls on loading the database

When I was using the cheapest droplet, I found the server start up script would
hang while building the card database. The fix was to move to a more expensive
droplet with more CPU/RAM/Faster Storage.
