.PHONY: build clean

IMAGE_NAME ?= erlang_builder
IMAGE_TAG  ?= centos7

build: .Dockerfile.built

.Dockerfile.built: Dockerfile
	docker build -t $(IMAGE_NAME):$(IMAGE_TAG) .

clean:
	docker rmi $(IMAGE_NAME):$(IMAGE_TAG) 2>/dev/null || true
	rm -f .Dockerfile.built
