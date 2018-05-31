# required package

* docker

* docker-compose

## Bash run docker

```bash
#! init .env
cp .env.example .env
```

```bash
#! install && run docker
docker-compose up -d --build
```
## get /var/jenkins_home/secrets/initialAdminPassword
```
docker exec <docker_id> cat /var/jenkins_home/secrets/initialAdminPassword
```