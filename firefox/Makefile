
SHELL = /bin/bash

RUNASUSER = $(shell id -u $(USER))

.PHONY = build clean

build: .Dockerfile.built

firefox.tar.bz2:
	curl -sS https://download-installer.cdn.mozilla.net/pub/firefox/releases/42.0/linux-x86_64/en-US/firefox-42.0.tar.bz2 > firefox.tar.bz2

.Dockerfile.built: firefox.tar.bz2 Dockerfile
	@docker build --pull=true --build-arg runasuser=$(RUNASUSER) -t firefox . && touch .Dockerfile.built

clean:
	@rm -fr firefox.tar.bz2
	@rm -fr .Dockerfile.built

