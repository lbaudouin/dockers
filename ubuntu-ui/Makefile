NAME=ubuntu-ui

BASE_OPTS = --init --rm -ti \
	    --name ${NAME} \
	    --hostname ${NAME} \
	    --volume ${PWD}/sources:/sources

UI_OPTS = -e DISPLAY=$$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix
#  -v /tmp/.docker.xauth:/tmp/.docker.xauth


all: build 

get:
	version=$$(cat /proc/driver/nvidia/version | head -n 1 | awk '{ print $$8 }' ) && \
	uri=http://us.download.nvidia.com/XFree86/Linux-x86_64/$$version/NVIDIA-Linux-x86_64-$$version.run && \
	wget -O nvidia-driver.run "$$uri"

build:
	docker image build -t ${NAME} .

build-force:
	docker image build --no-cache -t ${NAME} .

create_volumes:
	docker volume create build_folder

bash:
	xhost local:root
	docker run ${BASE_OPTS} ${UI_OPTS} \
		${NAME} bash

privileged-bash:
	xhost local:root
	docker run ${BASE_OPTS} ${UI_OPTS} \
		--privileged \
		${NAME} bash

#--device=/dev/dri/card0:/dev/dri/card0 \
