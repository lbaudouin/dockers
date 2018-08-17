GITLAB_URL=http://192.168.1.24/
CI_TOKEN=hRjdTy5Nx-CaqGhs-fV9
NAME=$(shell basename ${PWD}):v1

BASE_OPTS = --init --rm -ti \
	    --name ${NAME} \
	    --hostname ${NAME}

.PHONY: build

all: build

build:
	docker image build -t ${NAME} .

build-force:
	docker image build --no-cache -t ${NAME} .

bash:
	docker run ${BASE_OPTS} \
		${NAME} bash

privileged-bash:
	docker run ${BASE_OPTS} \
		--device /dev/random:/dev/random \
		--privileged \
		${NAME} bash

register:
	gitlab-ci-multi-runner register \
	--non-interactive \
	--url "${GITLAB_URL}" \
	--registration-token "${CI_TOKEN}" \
	--description "Generic Ubuntu Xenial 16.04 package build runner" \
	--executor "docker" \
	--docker-image "${NAME}"

su-register:
	sudo gitlab-ci-multi-runner register \
	--non-interactive \
	--url "${GITLAB_URL}" \
	--registration-token "${CI_TOKEN}" \
	--description "Generic Ubuntu Xenial 16.04 package build runner" \
	--executor "docker" \
	--docker-image "${NAME}"

run:
	gitlab-runner run

su-run:
	sudo gitlab-runner run

restart:
	gitlab-runner restart

su-restart:
	gitlab-runner restart
