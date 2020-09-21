# Portus on Docker compose

## configure server

### Install packages required to run Portus
```bash
sudo yum install git gcc gcc-c++ yum-utils wget nano nodejs gettext device-mapper-persistent-data lvm2 bzip2 python3-pip -y
```
### Add the Docker repository
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
### Install Docker and Docker Compose
```bash
sudo yum install docker-ce docker-ce-cli containerd.io -y
sudo yum install docker-compose -y
```
### Start the Docker service and enable it to start after system reboot
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

## Certificates

```bash
mkdir -p /etc/certs/
cd /etc/certs/
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout portus.key -out portus.crt
```
### Download Registry and portus project
```bash
cd /opt/
git clone https://github.com/ziedters/registry_potus.git 
```
### create a envirenement file

```bash
cd registry_potus/
vi .env
```
MACHINE_FQDN=portus.yourdomain.com
 
SECRET_KEY_BASE=Tn9aBRsh3j
 
PORTUS_PASSWORD=VJhE6kQShj
 
DATABASE_PASSWORD=3UvMDpk2Pr
```bash

##start the containers
docker-compose up

``` 
