PROJECT_NAME := carmot

DOCKER := $(shell command -v docker 2> /dev/null)
PODMAN := $(shell command -v podman 2> /dev/null)

ifdef PODMAN
	d := podman
else
	d := docker
endif

all: $(PROJECT_NAME).tar

$(PROJECT_NAME).tar:
	cd .. && $(d) build -t $(PROJECT_NAME) -f ./docker/dockerfile .
	$(d) image save -o $(PROJECT_NAME).tar $(PROJECT_NAME)

open:
	$(d) load < $(PROJECT_NAME).tar
	$(d) run --rm -it $(PROJECT_NAME) /bin/bash

clean:
	rm -f $(PROJECT_NAME).tar
	$(d) image rm -f $(PROJECT_NAME)
