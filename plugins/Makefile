# Project variables
DOCKER_REGISTRY ?= ghcr.io/apiclarity
VERSION ?= $(shell git rev-parse HEAD)
DOCKER_TAG ?= ${VERSION}

.PHONY: docker
docker: docker-kong

.PHONY: docker-kong
docker-kong:
	@DOCKER_BUILDKIT=1 docker build -t ${DOCKER_REGISTRY}/kong-plugin:${DOCKER_TAG} --file Dockerfile.kong .

.PHONY: push-docker
push-docker: push-docker-kong

.PHONY: push-docker-kong
push-docker-kong: docker-kong
	@echo "Publishing Kong plugin Docker image ..."
	docker push ${DOCKER_REGISTRY}/kong-plugin:${DOCKER_TAG}