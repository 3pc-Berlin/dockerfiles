# [Debian](https://hub.docker.com/_/debian/) Stretch Slim with [gosu](https://github.com/tianon/gosu/)

Docker base image with gosu for handling permission issues with docker containers

This image is mainly based on [HANDLING PERMISSIONS WITH DOCKER VOLUMES](https://denibertovic.com/posts/handling-permissions-with-docker-volumes/).

## Usage

```console
$ docker run -it -e LOCAL_USER_ID=`id -u $USER` foobar
```

