IMAGE = ghcr.io/soranoba/erlang:29.1.2-rockeylinux9

build:
	docker buildx build --platform linux/amd64,linux/arm64 -t $(IMAGE) --push .
