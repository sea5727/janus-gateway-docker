# janus-docker

janus-base 이미지로부터 janus docker image 생성, 컨테이너 실행

## params

IMAGE_NAME : docker image name
TAG : docke image tag
FULL_IMAGE_NAME : docker image full name with dockerhub id
CONTAINER_NAME : container name
NETWORK_NAME : docker network name
VOLUME_NAME : janus home volume
VOLUME_PATH : janus home path
CERT_FILE_FROM : janus cert file from
CERT_FILE_TO : janus cert file to
KEY_FILE_FROM : janus key file from
KEY_FILE_TO : janus key file to


## commands
### create janus docker image 
```
make image
```
### run janus container
```
make run
```
### run janus container using bash ( for debug )
```
make bash
```
### docker janus exec conatiner
```
make exec
```
### stop janus docker container
```
make stop
```
### remove janus docker container
```
make rm
```
### remove janus docker image
```
make rmi
```
### stop and rm janus docker image
```
make clean
```
