# Mini-Mesos

## Start

### With Marathon framework

```
$ docker-compose -f docker-compose.yml -f ./marathon/docker-compose.marathon.yml up -d
```

### With Aurora framework

```
$ docker-compose -f docker-compose.yml -f ./aurora/docker-compose.aurora.yml up -d
```

### With both frameworks

```
$ docker-compose -f docker-compose.yml -f ./both/docker-compose.both.yml up -d
```

## Aurora CLI

### Connect

```
$ docker run --rm -it -v $(pwd)/aurora/cli-config/clusters.json:/home/aurora/.aurora/clusters.json -v $(pwd)/aurora/cli-config/sample.aurora:/home/aurora/sample.aurora --net=minimesos_default pkleindienst/aurora-cli bash
```

### Start demo job

```
$ aurora job create demo/aurora/test/hello-go sample.aurora
```

### Remove demo job

```
$ aurora job killall demo/aurora/test/hello-go
```

## GUI access

### Start Firefox

```
$ docker run -ti --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix --net=minimesos_default --name firefox pkleindienst/ubuntu-firefox
$ docker network connect bridge firefox
```

## Cleanup

### Shutdown containers

```
$ docker-compose -f docker-compose.yml -f ./marathon/docker-compose.marathon.yml down

$ docker-compose -f docker-compose.yml -f ./aurora/docker-compose.aurora.yml down

$ docker-compose -f docker-compose.yml -f ./both/docker-compose.both.yml down

$ sudo rm -rf /tmp/mesos_tmp/ /tmp/mesos_log
```
