# janus-base

janus build environment docker image
janus 소스를 git으로부터 내려받아 빌드하기 위한 base 이미지

# dockerhub
```
docker pull sea5727/janus-gateway-base
```


# parms
BASE_NAME : docker image name
TAG : docker image tag
BASE_IMAGE_NAME : full docker image name

# commands
# create docker image
```
make image
```

# remove docker image
```
make rmi
```