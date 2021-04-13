# README #


### What is this repository for? ###

* performance testing using jmeter into docker

### How do I get set up? ###

* git clone git@github.com:1ole4g5/docker-performance.git
* cd docker-performance/JMeter/

### Config file ###
* ./docker-compose.yml

### Useful commands ###
* `sudo usermod -aG docker docker-user` (create user and add to docker group)
* `docker-compose up -d`
* `docker-compose down or docker-compose down --rmi all`
* `docker-compose ps -a`
* `docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)`
* `docker-compose up --scale server=N`
* `docker-compose build --compress --parallel`
* `docker-compose build --no-cache`
* `docker-compose up --build -d`
* `docker logs container_name`
* `docker-compose exec service_name sh`
* `docker cp containerID_or_name:/path/to/file /local/path/`