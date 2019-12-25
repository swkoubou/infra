# infra
Infra Script in swk

## RMS(https://rms.cs.kanagawa-it.ac.jp) Jenkins
### How To Setup
1. git clone this repo
1. `cd infra/rms-ci`
1. `chown -R 1000:1000 ./jenkins/jenkins_home`
1. `docker-compose up -d`
1. Access To `http://${target_uri}:8080`

### Tested On
```
~> docker -v
Docker version 19.03.5, build 633a0ea838

~> docker-compose --version
docker-compose version 1.16.1, build 6d1ac21
```

## LDAP (OpenLDAP and phpldapadmin)
### How To Setup
1. git clone
1. `cd/infra/ldap`
1. edit default admin password. in docker-compose.yaml
1. `docker-compose -up -d`
1. Access To `http://${target_uri}`

### Tested On
```
~> docker -v
Docker version 19.03.5, build 633a0ea838

~> docker-compose --version
docker-compose version 1.16.1, build 6d1ac21
```
