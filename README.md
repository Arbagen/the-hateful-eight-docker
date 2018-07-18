### Requirements:
* docker
* docker-compose
* git

### Services:
1. nginx
2. mysql
3. pma
4. php (contains installed git and composer)

### Configs:
All configs/logs/data for each service in appropriate service folder.

### Application files:
All application files folder contains in public_html

### Links(dev):
* web-server: [http://localhost:8080/](http://localhost:8080/)
* PMA: [http://localhost:8081/](http://localhost:8081/)

# Instaling
* [docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
* [docker-compose](https://docs.docker.com/compose/install/#install-compose)
### docker prepare
```bash
apt update
apt install curl git mc
```

### RUN:
```bash
#dev
docker-compose up --build
#prod
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

### prepare libs
```bash
docker-compose exec php bash
composer install
```
