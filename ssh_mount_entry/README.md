<style>
  :root {
    --yello:#ffcc00;
    --blu:#00e6b8;
    --orang:#ff5a1f;
    --gren:#00e600
  }

  code {
    background: #000000;
  }
  .span1  {
    background-color: #000000;
    padding: 0.2rem 0.2rem 0.2rem;
    -webkit-box-decoration-break: clone;
    -ms-box-decoration-break: clone;
    -o-box-decoration-break: clone;
    box-decoration-break: clone;
    color: #ffcc00;
  }
  /* li works for markdown lists fine */
  li {
    background-color: #000000;
    padding: 0.2rem 0.2rem 0.2rem;
    -webkit-box-decoration-break: clone;
    -ms-box-decoration-break: clone;
    -o-box-decoration-break: clone;
    box-decoration-break: clone;
    color: var(--orang);
  }
  .hd {
    background-color: #000000;
    padding: 0.2rem 0.2rem 0.2rem;
    -webkit-box-decoration-break: clone;
    -ms-box-decoration-break: clone;
    -o-box-decoration-break: clone;
    box-decoration-break: clone;
    color: #ffcc00;
  }

  p {
    background-color: #000000;
    padding: 0.2rem 0.2rem 0.2rem;
    -webkit-box-decoration-break: clone;
    -ms-box-decoration-break: clone;
    -o-box-decoration-break: clone;
    box-decoration-break: clone;
    color: var(--blu);
  }
</style>

# Debian latest (trixie) with ssh mount. {.span1} 
  * Adds user: (nyx) with password: (qwerty)
  * Uses ssh mount to git clone private, ssh-key protected repository, by letting the builder connect to ssh agent.
  * Optional personalized bash aliases.
<span class="span1"><b>--> Let me know if something could be improved! <--</b></span>
<details open>

<summary>
<span class="span1">Docker compose instructions</span>
</summary>

## Do steps below inside the directory which contains specific with Dockerfile {.hd} 

### Add identity to the authentication agent, so the ssh-mount works. {.hd}
```bash
ssh-add <path_to_your_ssh_key_file>
```
## Place ssh url for your private ssh-key protected repository to be cloned. {.hd}

1. Open ```Dockerfile``` file and replace ```<ssh_url>``` with your repo's url.
2. That is it, ```Dockefile``` is ready for building image!

### Build: {.hd}
```bash
docker compose build
```
### Enable docker to connect to X server {.hd}
```bash
xhost +local:docker
```
After closing container turn it off:
```bash
xhost -local:docker
```
### Start: {.hd}
```bash
docker compose up -d deb-main-ssh-mount-service
```
### Attach to container: {.hd}
```bash
docker compose attach deb-main-ssh-mount-service
```
### Tips: {.hd}
  * To detach from the container, and let it run in the backgroud, use the following shortcut sequence inside of it: ``` CTRL+p CTRL+q ```.

</details>
