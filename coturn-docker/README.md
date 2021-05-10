# coturn docker 

docker script from `instrumentisto/coturn`

# reference 
[ref #1](https://github.com/instrumentisto/coturn-docker-image)

# params
CONTAINER_NAME : docker container name   
NETWORK_NAME : docker network name ( recommended 'host' )   
PUBLIC_IP_1 : public-ip linked with internet network   
PRIVATE_IP_1 : private-ip will mapping into public-ip   
STUN_PORT : listening port   
URL : realm url   
UID : user id of long term credential mechanism   
PWD : user password of long term credential mechanism   


# commands
## 1. create docker image 
```
make image
```

## 2. docker run
```
make run
```

## 3. docker run for turn test
```
make run_turn_test
```