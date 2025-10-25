## Containers

Running instance of the docker images i.e. it is the instance/object we create from the Class in the OOP.

**Write-On-Copy:** where docker builds a write layer upon the already existing read-only image layers.

The data written/updated on the container will no longer exist when the container will be destroyed i.e. containers are **ephemeral**. However, the data changes still exist even if you stopped and restarted a container i.e. as long as the container is still alive not killed/removed, the changes will still exist.

## Core Related Commands

```
# to run a container

$ docker run <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# to run a container and override the default CMD

$ docker run <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG> <COMMAND>

# to run a container in the detach mode i.e. run container in the background

$ docker run -d <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# to run a container with a specific name

$ docker run --name <NAME> <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG>

# to run a container with interactive shell i.e. jump into inside the container

$ docker run -it <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG> /bin/bash

# to list the current running containers

$ docker ps

# to list the current running containers' IDs only

$ docker ps -q

# to list the current containers either stopped or running

$ docker ps -a

# to stop a running container using either container id or name

$ docker stop <CONTAINER-ID>/<CONTAINER-NAME>

# to kill/remove a stopped container, remember: you can't kill/remove a running container directly

$ docker rm <CONTAINER-ID>/<CONTAINER-NAME>

# to restart an existing stopped container

$ docker restart <CONTAINER-ID>/<CONTAINER-NAME> 

# to check the container deep details e.g. the networking settings of the container

$ docker inspect <CONTAINER-ID>/<CONTAINER-NAME> 
```