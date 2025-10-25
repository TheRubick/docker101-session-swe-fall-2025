## Networks

Docker has multiple modes for how it maintain the networking of the containers e.g. how ip addresses allocated and associated to the containers.

Three modes are:
- **Bridge(default):** where each container has its own ip address
- **Host:** where the container ip address is the same as the host where no two containers can share the same port
- **None:** the container is isolated and not get assigned any ip address. Mainly used for security purposes when you want to test a container and make it isolated from other containers or any other network generally speaking.

## Core Related Commands

```
# to run a container in the bridge mode which is the default mode i.e. any running container normally goes in this mode without specifying any --network option

$ docker run --network=bridge <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# to run a container in the host mode. Note: you can't have multiple containers that use the same port in this mode as one of them should lock this port on the host i.e. no containers shall use the same host port

$ docker run --network=host <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# to run a container in none mode i.e. isolated

$ docker run --network=none <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# you can also get the networking settings from the container using the inspect docker subcommand which lists the core details of any container

$ docker inspect <CONTAINER-ID>/<CONTAINER-NAME> | grep -i Network
```