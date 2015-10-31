#!/bin/bash

# Example: make erlang=otp_18.1 os=debian os_release=testing

.PHONY = clean build push

REPO = ruanjonker/erlang_$(erlang)
TAG = $(os)_$(os_release)

DOCKERFILE_DIR = $(erlang)/$(os)/$(os_release)

DOCKERFILE = $(DOCKERFILE_DIR)/Dockerfile
DOCKERFILE_BUILT = $(DOCKERFILE_DIR)/.Dockerfile.built

build: $(DOCKERFILE_BUILT)

$(DOCKERFILE_BUILT): $(DOCKERFILE)
	@docker build -t $(REPO):$(TAG) $(DOCKERFILE_DIR) && touch $(DOCKERFILE_BUILT)

clean:
	@rm -fr $(DOCKERFILE_BUILT)
	@docker rmi -f $(REPO):$(TAG) 2>/dev/null || true

push: build
	@docker push $(REPO):$(TAG)

