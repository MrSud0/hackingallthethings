---
title: "Docker"
---
#### Base commands
Build image
`docker build --no-cache --progress=plain -t my-image .`

Check images
`docker images`
OR
`docker image ls`

Check docker Networks
`docker network ls`

Run an image
`docker run -it --rm my-image`

Run an image and attach it to specific network
`docker run --net=host -it --rm pentester`

Run as daemon
`docker run -d -it --rm my-image`

Check the logs of a running container
`docker logs container`

Spawn TTY on running container
`docker exec -it container /bin/bash`

Spawn TTY on running container as root
`docker exec -it -u root container /bin/bash`

Save the container image as a .tar file:
`docker save -o aoc.tar public.ecr.aws/h0w1j9u3/grinch-aoc:latest`

Interesting artifacts while inspecting docker layers, **empty_layer: true **
