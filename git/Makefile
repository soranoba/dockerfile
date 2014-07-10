all: build

build:
	cp -r ~/.ssh .
	docker build -t soranoba/git .
	rm -rf .ssh

run:
	docker run -t -i soranoba/git /bin/bash
