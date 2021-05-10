CONTAINER_NAME ?= coturn
NETWORK_NAME ?= host
PUBLIC_IP_1 ?= 121.88.86.13
PRIVATE_IP_1 ?= 192.168.0.1
STUN_PORT ?= 3478
URL ?= sanghotest.iptime.org
UID ?= sanghotest
PWD ?= sanghopwd

.PHONY: image run run_turn_test start stop clean

image:
	@docker pull instrumentisto/coturn

run:
	@docker run \
	-d \
	--name=$(CONTAINER_NAME) \
	--network=$(NETWORK_NAME) \
	instrumentisto/coturn \
	-n \
	--log-file=stdout \
	--external-ip=$(PUBLIC_IP_1)/$(PRIVATE_IP_1) \
	--relay-ip=$(PUBLIC_IP_1) \
	--listening-port=$(STUN_PORT) \
	--fingerprint \
	--lt-cred-mech \
	--realm=$(URL) \
	--server-name=$(URL) \
	--user=$(UID):$(sanghopwd)

run_turn_test:
	@docker run \
	-d \
	--name=$(CONTAINER_NAME) \
	--network=$(NETWORK_NAME) \
	instrumentisto/coturn \
	-n \
	--log-file=stdout \
	--listening-port=$(STUN_PORT) \
	--fingerprint \
	--lt-cred-mech \
	--realm=$(URL) \
	--server-name=$(URL) \
	--user=$(UID):$(sanghopwd)

start:
	@docker start $(CONTAINER_NAME)


stop:
	@docker stop $(CONTAINER_NAME)

clean:
	@docker stop $(CONTAINER_NAME)
	@docker rm $(CONTAINER_NAME)