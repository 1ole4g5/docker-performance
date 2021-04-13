# README #


### What is this repository for? ###

* performance testing using yandex-tank into docker

### How do I get set up? ###

* git clone git@github.com:1ole4g5/docker-performance.git
* cd docker-performance/YaTank/

### Config file ###
* load.yaml

### How to run load tests? ###
YaTank with Phantom:

* ```docker run \
    -v $(pwd):/var/loadtest \
    -v $SSH_AUTH_SOCK:/ssh-agent -e SSH_AUTH_SOCK=/ssh-agent \
    --net host \
    -it \
    direvius/yandex-tank```
    
YaTank with JMeter:

* ```docker run \
     -v $(pwd):/var/loadtest \
     -v $SSH_AUTH_SOCK:/ssh-agent -e SSH_AUTH_SOCK=/ssh-agent \
     --net host \
     -it \
     direvius/yandex-tank:jmeter-latest```
