# myselenium

selenium image for debian 11 , choromium


### tag

* monthly202204, debian11, stable, latest
    * first release

### known problem

The Chromium requests X11 display setting when screen shots some web site.

This container image can not run above web site.


### how to use

outputs JSON data.

```
    # when running on Windows , set below
    WINPTY_CMD=winpty.exe

    # run image
    docker pull docker.io/georgesan/myselenium:latest
    ${WINPTY_CMD} docker run -i -t --rm \
        -e http_proxy=${http_proxy} -e https_proxy=${https_proxy} -e no_proxy="${no_proxy}" \
        --cap-add SYS_ADMIN \
        docker.io/georgesan/myselenium:latest \
        access-url-and-screen-shot.py --screenshot https://www.google.com/
```

outputs below.

```
{
  "title": "Google",
  "screenshot": "iVBORw0KGgoAAAANSrk..."
}
```

screenshot is PNG file data encoded base64.

