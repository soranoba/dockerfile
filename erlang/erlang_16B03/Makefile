all: build

build:
	cp ~/.gitconfig .
	cp -r ~/.ssh .
	docker build -t soranoba/erlang:16.b03 .
	rm -rf .ssh
	rm .gitconfig

run:
	docker run -t -i soranoba/erlang:16.b03 /bin/bash
