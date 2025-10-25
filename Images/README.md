## Images

It is the template we need to build and run our source code in docker it is equivalent to the Classes in the OOP e.g. as in our example below, it will include the python required as well as the flask installed to run our hello world app.

**Dockerfile:** a text file that contains the docker instructions to create these images.
The definition of the **docker instructions** below:
- **FROM:** determines the baseline that will be used to build our image the image that include all the binaries/libraries/modules to build our application and run it.
- **WORKDIR:** determines the default path that your commands will take place e.g. the COPY command copy/clone the app.py file to the workdir inside the container. Also, if you have jumped inside the container and hit ls /hello-world, you will find the app.py.
- **RUN:** executes the command(s) necessary to build our image. Note: any RUN instructions doesn't take place in the docker container unlike CMD and ENTRYPOINT.
- **COPY:** clone/copy files from your host machine to the docker image.
- **CMD:** set the default command parameters to execute inside the container.

```
FROM python:3.13-slim
WORKDIR hello-world
RUN pip3 install flask
COPY app.py .
CMD ["flask", "--app", "app", "run", "--host", "0.0.0.0"]
```

Each image docker instruction create an immutable layer where we can't modify after building, however they are replaced. **Image layers** represent change in the filesystem, for sake of simplicity we will assume that each docker instruction creates exactly a single image layer however this isn't the case.

The meaning of immutable appears when you replace a docker file instruction as docker starting from this instruction (which has been modified) will rebuild the image.

**Docker Registry** is the place where we can pull/push docker images and use them to build and run our application source code. One of the most famous docker registry which is used by default is [dockerhub](https://hub.docker.com/).

## Core Related Commands

```
# to list and get more context about the images like their names, IDs, etc..

$ docker images

# to get context about the image layers and the docker instructions built this image

$ docker history <IMAGE-NAME>/<IMAGE-ID> 

# this command builds the image and assigning to it a special name, tag pair taking into consideration that the Dockerfile exists in the current path

$ docker build -t <IMAGE-NAME>:<IMAGE-TAG> . 

# to pull image from a remote repository. Note: by default it set the registry to dockerhub so in case of any other registry you need to specify as follows: docker pull <REGISTRY-HOSTNAME>/<IMAGE-NAME>:<IMAGE-TAG>

$ docker pull <IMAGE-NAME>:<IMAGE-TAG> 

# to tag image i.e. give it a special label

$ docker tag <IMAGE-ID>/<IMAGE-NAME>:<IMAGE-TAG> <IMAGE-NAME>:<IMAGE-TAG>

# to push image to a remote repository, make sure to set the credentials before pushing the remote registry

$ docker push <REGISTRY-HOSTNAME>/<IMAGE-NAME>:<IMAGE-TAG>
```