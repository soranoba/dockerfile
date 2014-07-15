all: build

build:
	cp -r ~/.ssh .
	cp ~/.gitconfig .
	docker build -t soranoba/git .
	rm .gitconfig
	rm -rf .ssh

run:
	docker run -t -i soranoba/git /bin/bash
