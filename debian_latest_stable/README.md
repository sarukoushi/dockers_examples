# Debian latest (trixie)

## Do steps below inside the directory which contains specific with ```Dockerfile```

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
docker compose up -d deb-main
```
### Attach to container:
```bash
docker compose attach deb-main
```
### Tips:
  * To detach from the container, and let it run in the backgroud, use the following shortcut sequence inside of it: ``` CTRL+p CTRL+q ```.