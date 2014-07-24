IMAGE_NAME = soranoba/ubuntu-ja:14.04

all: build

build:
	@docker build -t $(IMAGE_NAME) .

start:
	@if [ -f .docker ]; then \
		read DOCKER < .docker; \
		docker start $$DOCKER; \
		docker attach $$DOCKER; \
	else \
		read -p "Container's name : " DOCKER; \
		echo $$DOCKER > .docker; \
		docker run -t -i --name $$DOCKER $(IMAGE_NAME) /bin/bash; \
	fi
