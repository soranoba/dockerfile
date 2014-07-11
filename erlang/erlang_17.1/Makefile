all: build

build:
	cp ~/.gitconfig .
	cp -r ~/.ssh .
	docker build -t soranoba/erlang:17.01 .
	rm -rf .ssh
	rm .gitconfig

run:
	docker run -t -i soranoba/erlang:17.01 /bin/bash
