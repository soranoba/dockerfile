IMAGE_NAME = soranoba/ubuntu-git:13.04

.PHONY: build start clean clean_all

all: build start

build: .build

.build: Dockerfile
	@cp -rf ~/.ssh .ssh
	@cp ~/.gitconfig .gitconfig
	@docker build -t $(IMAGE_NAME) .
	@if [ $$? = 0 ]; then touch .build; fi
	@rm -rf .gitconfig .ssh

start:
	@if [ -f .docker ]; then \
		read DOCKER < .docker; \
		if [ $$DOCKER -a `docker start $$DOCKER` ]; then \
			docker attach $$DOCKER; \
			exit; \
		fi; \
		rm .docker; \
	fi; \
	read -p "Container's name : " DOCKER; \
	echo $$DOCKER > .docker; \
	docker run -t -i --name $$DOCKER $(IMAGE_NAME) /bin/bash; \
	if [ $$? = 1 ]; then \
		rm .docker; \
	fi

clean:
	@rm .docker

clean_all: .docker
	@read DOCKER < .docker; docker rm $$DOCKER;
	@rm .docker;
