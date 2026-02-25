# Debian latest (trixie) with ssh mount.

### Add identity to the authentication agent, so the ssh-mount works.
```bash
ssh-add <path_to_your_ssh_key_file>
```
## Place ssh url for your private ssh-key protected repository to be cloned.

1. Open ```Dockerfile``` file and replace ```<ssh_url>``` with your repo's url.
2. That is it, ```Dockefile``` is ready for building image!

### Build:
```bash
docker compose build
```
### Enable docker to connect to X server
```bash
xhost +local:docker
```
After closing container turn it off:
```bash
xhost -local:docker
```
### Start:
```bash
docker compose up -d spot-deb-main
```
### Attach to container:
```bash
docker compose attach spot-deb-main
```
### Tips:
  * To detach from the container, and let it run in the backgroud, use the following shortcut sequence inside of it: ``` CTRL+p CTRL+q ```.