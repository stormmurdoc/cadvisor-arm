# cAdvisor for ARM-based devices

cAdvisor docker image build for ARM-based devices (e.g.: Raspberry PI).
This package is based on official [google/cadvisor](https://github.com/google/cadvisor)

## Content

```shell
docker run \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:rw \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  --volume=/dev/disk/:/dev/disk:ro \
  --publish=8080:8080 \
  --detach=true \
  --name=cadvisor \
  stormmurdoc/cadvisor-arm:latest
```

### Docker Compose Example

```yml
version: '3'

services:
  cadvisor:
    image: stormmurdoc/cadvisor-arm
    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:rw
      - /sys:/sys
      - /var/lib/docker/:/var/lib/docker:ro
      - /dev/disk/:/dev/disk:ro
    ports:
      - 8080:8080
```

