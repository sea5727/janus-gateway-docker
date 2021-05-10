IMAGE_NAME ?= janus-gateway-docker
#TAG ?= dev
TAG ?= latest

FULL_IMAGE_NAME ?= sea5727/$(IMAGE_NAME):$(TAG)
CONTAINER_NAME ?= janus-gateway

NETWORK_NAME ?= WebRTC

VOLUME_NAME ?= janus-volume
VOLUME_PATH ?= /opt/janus

CERT_FILE_FROM ?= $(PWD)/cert.crt
CERT_FILE_TO ?= /opt/janus/certs/cert.crt

KEY_FILE_FROM ?= $(PWD)/cert.key
KEY_FILE_TO ?= /opt/janus/certs/cert.key

image:
	@docker build \
	--no-cache \
	-t $(FULL_IMAGE_NAME) \
	.

run: 
	@docker run -it -d \
	--name $(CONTAINER_NAME) \
	--network $(NETWORK_NAME) \
	--volume $(VOLUME_NAME):$(VOLUME_PATH) \
	--volume $(CERT_FILE_FROM):$(CERT_FILE_TO):ro \
	--volume $(KEY_FILE_FROM):$(KEY_FILE_TO):ro \
	$(FULL_IMAGE_NAME)

bash: 
	@docker run -it \
	--name $(CONTAINER_NAME) \
	--network $(NETWORK_NAME) \
	--volume $(VOLUME_NAME):$(VOLUME_PATH) \
	--volume $(CERT_FILE_FROM):$(CERT_FILE_TO):ro \
	--volume $(KEY_FILE_FROM):$(KEY_FILE_TO):ro \
	$(FULL_IMAGE_NAME) /bin/bash
	
exec:
	@docker exec -it $(CONTAINER_NAME) /bin/bash

stop:
	@docker stop $(CONTAINER_NAME)

rm:
	@docker rm $(CONTAINER_NAME)

rmi:
	@docker rmi $(FULL_IMAGE_NAME)

clean:
	@docker stop $(CONTAINER_NAME)
	@docker rm $(CONTAINER_NAME)
