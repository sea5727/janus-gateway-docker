IMAGE_NAME ?= nginx
CONTAINER_NAME ?= nginx
NETWORK_NAME ?= WebRTC
VOLUME_NAME ?= janus-volume
LINKED_VOLUME_PATH ?= /opt/janus

CONF_FILE_FROM ?= $(PWD)/nginx.conf
CONF_FILE_TO ?= /etc/nginx/nginx.conf

CERT_FILE_FROM ?= $(PWD)/cert.crt
CERT_FILE_TO ?= /etc/nginx/certs/cert.crt

KEY_FILE_FROM ?= $(PWD)/cert.key
KEY_FILE_TO ?= /etc/nginx/certs/cert.key

.PHONY: image bash run start exec stop clean rm rmi

image:
	@docker pull nginx

bash:
	@docker run -it -t --name $(CONTAINER_NAME) --network $(NETWORK_NAME) -p 8083:80 -p 8084:443 $(IMAGE_NAME) /bin/bash

run: 
	@docker run -d -it --name $(CONTAINER_NAME) \
	--network $(NETWORK_NAME) \
	--volume $(VOLUME_NAME):/opt/janus \
	--volume $(CONF_FILE_FROM):$(CONF_FILE_TO):ro \
	--volume $(CERT_FILE_FROM):$(CERT_FILE_TO):ro \
	--volume $(KEY_FILE_FROM):$(KEY_FILE_TO):ro \
	-p 8083:80 \
	-p 8084:443 \
	$(IMAGE_NAME)

start:
	@docker start $(CONTAINER_NAME)
exec:
	@docker exec -it $(CONTAINER_NAME) /bin/bash
stop:
	@docker stop $(CONTAINER_NAME)

rm:
	@docker rm $(CONTAINER_NAME)

rmi:
	@docker rmi $(IMAGE_NAME)

clean:
	@docker stop $(CONTAINER_NAME)
	@docker rm $(CONTAINER_NAME)
