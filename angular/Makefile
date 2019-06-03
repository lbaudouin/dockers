NAME="angular"

BASE_OPTS = --init --rm -ti \
	    --name ${NAME} \
	    --hostname ${NAME} \
		-p 8082:4200 \
		-v ${PWD}/sources:/sources
UI_OPTS = -e DISPLAY=$$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix

.PHONY: build run

all: bash

build:
	docker image build -t ${NAME} .

build-force:
	docker image build --no-cache -t ${NAME} .

bash:
	docker run ${BASE_OPTS} ${NAME} bash

bash-ui:
	xhost local:root
	docker run ${BASE_OPTS} ${UI_OPTS} ${NAME} bash

privileged-bash:
	docker run ${BASE_OPTS} --privileged ${NAME} bash

privileged-bash-ui:
	xhost local:root
	docker run ${BASE_OPTS} ${UI_OPTS} --privileged ${NAME} bash

run:
	xhost local:root
	docker run ${BASE_OPTS} ${UI_OPTS} ${NAME}

