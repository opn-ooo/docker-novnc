# noVNC Display Container
This image is intended to be used for displaying X11 applications from other containers in a browser.

## Image Contents

* [Xvfb](http://www.x.org/releases/X11R7.6/doc/man/man1/Xvfb.1.xhtml) - X11 in a virtual framebuffer
* [x11vnc](http://www.karlrunge.com/x11vnc/) - A VNC server that scrapes the above X11 server
* [noNVC](https://kanaka.github.io/noVNC/) - A HTML5 canvas vnc viewer
* [Fluxbox](http://www.fluxbox.org/) - a small window manager
* [xterm](http://invisible-island.net/xterm/) - to demo that it works
* [supervisord](http://supervisord.org) - to keep it all running

## Usage

### Variables

You can specify the following variables:
* `DISPLAY_WIDTH=<width>` (1024)
* `DISPLAY_HEIGHT=<height>` (768)
* `RUN_XTERM={yes|no}` (yes)
* `RUN_FLUXBOX={yes|no}` (yes)

### Stand-alone Demo
Run:
```bash
$ docker run --rm -it -p 8080:8080 ghcr.io/dtinth/docker-novnc
```
Open a browser and see the `xterm` demo at `http://<server>:8080/vnc.html`

### Usage in Docker Compose
```yaml
version: '2'
services:
  x11:
    image: ghcr.io/dtinth/docker-novnc
    environment:
      # Adjust to your screen size
      - DISPLAY_WIDTH=1600
      - DISPLAY_HEIGHT=968
      - RUN_XTERM=no
    ports:
      - "8080:8080"
```

## On DockerHub / GitHub
* DockerHub [theasp/novnc](https://hub.docker.com/r/theasp/novnc/)
* GitHub [theasp/docker/novnc](https://github.com/theasp/docker)

## Thanks
This is based on [theasp/docker-novnc](https://github.com/theasp/docker-novnc).
