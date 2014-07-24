IMAGE_NAME          = user/image:tag
CONTAINER_NAME_FILE = .docker 

all: build

build:
	@docker build -t $(IMAGE_NAME) .

start:
	@if [ -f $(CONTAINER_NAME_FILE) ]; then \
		read DOCKER < $(CONTAINER_NAME_FILE); \
		if [ `docker start $$DOCKER` ]; then \
			docker attach $$DOCKER; \
			exit; \
		fi; \
		rm $(CONTAINER_NAME_FILE); \
	fi; \
	read -p "Container's name : " DOCKER; \
	echo $$DOCKER > $(CONTAINER_NAME_FILE); \
	if [ ! `docker run -t -i --name $$DOCKER $(IMAGE_NAME) /bin/bash` ]; then \
		rm $(CONTAINER_NAME_FILE); \
	fi

clean:
	@rm $(CONTAINER_NAME_FILE)

clean_all:
	@if [ -f $(CONTAINER_NAME_FILE) ]; then \
		read DOCKER < $(CONTAINER_NAME_FILE); \
		docker rm $$DOCKER; \
		rm $(CONTAINER_NAME_FILE); \
	fi
