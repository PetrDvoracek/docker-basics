# docker-basics

For each line in Dockerfile, new container with process is created - use `&&` instead of `newline` as much as possible. This is done because of caching so you are able to start the container faster.

```
//good
RUN apk add --no-cache make gcc g++ python && \
  npm install --production --silent && \
  apk del make gcc g++ python
  
//bad
RUN apk add --no-cache make gcc g++ python
RUN npm install --production --silent
RUN apk del make gcc g++ python
```

To remove old and unused images, use `docker image prune`
It is recommended to build new image with `--rmi` parametter (cleanup).


# Run Xserver in Docker
```
# Dockerfile
FROM debian
RUN apt-get update
RUN apt-get install -qqy x11-apps
CMD xeyes

```
```
# run.sh
docker run -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=:2 xeyes
```
