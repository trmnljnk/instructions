# Portainer

## Updating Portainer

As Portainer is managing all other containers it is not possible to update this container like you would do with all other containers.
We update this specific container from the commmand line as that's the only way.

1. Find the Portainer container by running `docker ps` and do a `grep` for portainer.

```sh
media@debian:~$ docker ps | grep portainer
f2949d0e3fd5   portainer/portainer-ce                               "/portainer"             2 months ago   Up 2 hours             0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp, 0.0.0.0:9443->9443/tcp, [::]:9443->9443/tcp, 9000/tcp                                                                                                                                                                                                           portainer-2
```

Checking which command we have run previously with `history` command and `grep` for run.

```sh
media@debian:~$ history | grep run
 1614  docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:f2a7f5abd4735f9cd91563c6134e014b15168c4018beea87f1eec9d9618b2ad4 
 1619  docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:bd8f7a6d98e2a512e18272c38914abd1e92d663451f3c925d502a8557a3b92d7 
 1663  docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:bd8f7a6d98e2a512e18272c38914abd1e92d663451f3c925d502a8557a3b92d7 
 1687  history | grep run
```

Now we can savely remove the container named `portainer-2` with `docker rm -f portainer-2`

```sh
media@debian:~$ docker rm -f portainer-2 
portainer-2
```

When the container is removed we can copy the previously run command. First put a # before pasting the command this allows for replaving the old hash with the new one.  

`# 1663  docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:bd8f7a6d98e2a512e18272c38914abd1e92d663451f3c925d502a8557a3b92d7`

This is how your new command would look like after changing the hash. You will see docker pulling the new image to your machine.

```sh
media@debian:~$ docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:449202d765d28ec443c1657fc1121aff92b8afcee6b58bcea36e1f0e81e8297c 
Unable to find image 'portainer/portainer-ce@sha256:449202d765d28ec443c1657fc1121aff92b8afcee6b58bcea36e1f0e81e8297c' locally
docker.io/portainer/portainer-ce@sha256:449202d765d28ec443c1657fc1121aff92b8afcee6b58bcea36e1f0e81e8297c: Pulling from portainer/portainer-ce
6970b305841e: Pull complete 
c05d4fb47930: Pull complete 
04de093ad5ed: Pull complete 
a9ff7abff372: Pull complete 
e09df2601140: Pull complete 
df254cde32a0: Pull complete 
6b34a21056c4: Pull complete 
faf3a09a336d: Pull complete 
26693e01e9e2: Pull complete 
4f4fb700ef54: Pull complete 
Digest: sha256:449202d765d28ec443c1657fc1121aff92b8afcee6b58bcea36e1f0e81e8297c
Status: Downloaded newer image for portainer/portainer-ce@sha256:449202d765d28ec443c1657fc1121aff92b8afcee6b58bcea36e1f0e81e8297c
a4bf1e2307846d7da39a7f764f784a83afaba623bc4a96f6ece1adb63db308f6
```

Last check wether the container is actully running without any issues.

```sh
media@debian:~$ docker ps | grep portainer
a4bf1e230784   portainer/portainer-ce                               "/portainer"             About a minute ago   Up About a minute      0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp, 0.0.0.0:9443->9443/tcp, [::]:9443->9443/tcp, 9000/tcp                                                                                                                                                                                                           portainer-2
media@debian:~$ 
```

This is the URL to check for the hash of the latest version.

[https://hub.docker.com/layers/portainer/portainer-ce/latest/images/sha256-e65b9b55c16c32f6abcbd1440a4fff020739973f0e41d6a99088d200a6014bfe](https://hub.docker.com/layers/portainer/portainer-ce/latest/images/sha256-e65b9b55c16c32f6abcbd1440a4fff020739973f0e41d6a99088d200a6014bfe)

docker run -d   --name portainer-2   --restart always   --network cloudflared   -p 8000:8000   -p 9443:9443   -v /var/run/docker.sock:/var/run/docker.sock   -v /home/media/portainer:/data   portainer/portainer-ce@sha256:224a378fbc5ae579dc9d570c5ca2e5e981a4a003c8d7c2c5b5e482af97c2f87c
