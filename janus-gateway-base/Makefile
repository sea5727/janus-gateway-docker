BASE_NAME ?= janus-gateway-base
#TAG ?= dev
TAG ?= latest
BASE_IMAGE_NAME ?= sea5727/$(BASE_NAME):$(TAG)

image:
	@docker build \
	--no-cache \
	-t $(BASE_IMAGE_NAME) \
	.

rmi:
	@docker rmi $(BASE_IMAGE_NAME)

