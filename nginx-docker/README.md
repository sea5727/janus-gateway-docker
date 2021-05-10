# nginx docker 


## params


TEMPLATE_NAME ?= nginx
IMAGE_NAME ?= sea5727/$(TEMPLATE_NAME):dev
NETWORK_NAME ?= WebRTC

VOLUME_NAME ?= janus-gateway
LINKED_VOLUME_PATH ?= /opt/janus

CONF_FILE_FROM ?= $(PWD)/nginx.conf
CONF_FILE_TO ?= /etc/nginx/nginx.conf

CERT_FILE_FROM ?= $(PWD)/cert.crt
CERT_FILE_TO ?= /etc/nginx/certs/cert.crt

KEY_FILE_FROM ?= $(PWD)/cert.key
KEY_FILE_TO ?= /etc/nginx/certs/cert.key