Build the docker image
```console
docker build -t postman .
```

Start docker with GUI
```console
xhost local:root
docker run -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix -it --rm postman
```
