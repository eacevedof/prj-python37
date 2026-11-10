#!/bin/bash
TODAY := $(shell date +'%Y-%m-%d')
CURRENT_BRANCH := $(shell git rev-parse --abbrev-ref HEAD)

help: ## Show this help message
	@echo "usage: make [target]"
	@echo
	@echo "targets:"
	@egrep "^(.+)\:\ ##\ (.+)" ${MAKEFILE_LIST} | column -t -c 2 -s ":#"

gitpush: ## git push m=any message
	clear;
	git pull;
	git add .; git commit -m "azure-devops: $(m)"; git push;

gp-def: ## git push with default azure-devops message
	clear;
	git add .; git commit -m "azure-devops"; git push;

CURRENT_BRANCH := $(shell git rev-parse --abbrev-ref HEAD)
update-branch:  ## update main branch
	git fetch --all;
	git checkout develop; git reset --hard origin/develop;
	git checkout main; git reset --hard origin/main;

	git checkout $(CURRENT_BRANCH);
	git diff --name-only develop main

