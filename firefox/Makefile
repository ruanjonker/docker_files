
SHELL = /bin/bash

RUNASUSER = $(shell id -u $(USER))

.PHONY = build clean

build: .Dockerfile.built

firefox.tar.bz2:
	curl -sSL -o firefox.tar.bz2 "https://download.mozilla.org/?product=firefox-45.0.1-SSL&os=linux64&lang=en-US"

.Dockerfile.built: firefox.tar.bz2 Dockerfile
	@docker build --pull=true --build-arg runasuser=$(RUNASUSER) -t firefox . && touch .Dockerfile.built

clean:
	@rm -fr firefox.tar.bz2
	@rm -fr .Dockerfile.built

