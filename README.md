### Getting Started

```
mkdir testdriven-app && cd testdriven-app $ mkdir services && cd services
mkdir users && cd users
mkdir project
python3.6 -m venv env
source env/bin/activate
deactivate
```
## Dependencies - requirement.txt
```
(env)$ pip install flask==0.12.2
(env)$ pip install Werkzeug==0.16.1
```
## Docker Config

Next, we need to create a new Docker host with Docker Machine and point the Docker client at it:
```
docker -v
docker-compose -v
docker-machine -v
```
##### (Optional Steps)
```
docker-machine create -d virtualbox testdriven-dev 
docker-machine env testdriven-dev
eval "$(docker-machine env testdriven-dev)"
```

### Docker-compose

```
docker-compose -f docker-compose-dev.yml build
docker-compose -f docker-compose-dev.yml up -d
```