## Volumes

Docker objects used to persist the data inside the container even if that container is killed. **Note:** You can check these volumes on the following path on the host OS: **/var/lib/docker/volumes/**.

**Bind mounts:** are used to mount files from your host system to the containers, the main difference between bind mounts and volumes where there is docker object(s) need to be created in case of bind mounts.

## Core Related Commands

```
# the current core volume subcommand is our gateway to maintain and observe the docker volumes

$ docker volumes --help

# to list the current volumes

$ docker volumes ls

# to create a docker volume

$ docker volumes create <VOLUME-NAME>

# to run a container and mount the docker volume into a specific path inside the container

$ docker run -v <VOLUME-NAME>:<PATH-ON-THE-CONTAINER> <IMAGE-NAME>:<IMAGE>

# to run a container and mount a path on the OS host into a specific path inside the container. Note: this path could be directory or file path e.g. /tmp/dummy vs /tmp/dummy/dummy.txt

$ docker run -v <PATH-ON-THE-OS-HOST>:<PATH-ON-THE-CONTAINER> <IMAGE-NAME>:<IMAGE>
```