# docker-debian-apt-cacher

see https://docs.docker.com/engine/examples/apt-cacher-ng/


# install

```bash
docker run -d -p 3142:3142 --name apt-cacher --volume /data/var/apt:/var/cache/apt-cacher-ng alekzonder/apt-cacher:latest
```


# usage

```
docker run --rm -t -i -e http_proxy=http://<your server>:3142/ debian:jessie bash
docker run --rm -t -i -e http_proxy=http://<your server>:3142/ ubuntu:16.04 bash
```

### builtin image

```
FROM ubuntu
RUN  echo 'Acquire::http { Proxy "http://<your server>:3142"; };' >> /etc/apt/apt.conf.d/01proxy
RUN apt-get update && apt-get install -y vim git

# docker build -t my_ubuntu .
```
