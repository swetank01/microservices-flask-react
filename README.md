### Getting Started

```
mkdir testdriven-app && cd testdriven-app $ mkdir services && cd services
mkdir users && cd users
mkdir project
python3.6 -m venv env
source env/bin/activate
deactivate
```

## RUN 
```
cd /testdriven-app/services/users/
python manage.py run
```

##### Dependencies - requirement.txt
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

## Postgres Setup :
- Add a "db" directory to "project", and add a create.sql file in that new directory:

```
CREATE DATABASE users_prod; 
CREATE DATABASE users_dev; 
CREATE DATABASE users_test;
```

* PYTHON 3 SUPPORT psycopg2==2.8.4

```
docker-compose -f docker-compose-dev.yml run users python manage.py recreate-db
docker exec -ti $(docker ps -aqf "name=users-db") psql -U postgres
```
##### PostresDB Commands
```
\c users_dev
\dt
\q
```

## Test Setup :
- Let's get our tests up and running for this endpoint.

Add a "tests" directory to the "project" directory, and then create the following files inside the newly created directory:
1. __init__.py
2. base.py
3. test_config.py 4. test_users.py


## RESTful Routes

- Let's set up three new routes, following RESTful best practices, with TDD:

- For each, we'll-
1. writeatest
2. runthetest,watchingitfail(red)
3. writejustenoughcodetogetthetesttopass(green)
4. refactor(ifnecessary)

### POST
Add the test to the TestUserService() class in project/tests/test_users.py: