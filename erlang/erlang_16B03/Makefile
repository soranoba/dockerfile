IMAGE_NAME = soranoba/erlang:16.b03

all: build

build:
	@cp ~/.gitconfig .
	@cp -r ~/.ssh .
	@docker build -t $(IMAGE_NAME) .
	@rm -rf .ssh
	@rm .gitconfig

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
