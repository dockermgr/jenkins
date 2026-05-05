## 👋 Welcome to jenkins 🚀  

jenkins README  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update jenkins
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/jenkins/volumes"
git clone "https://github.com/dockermgr/jenkins" "$HOME/.local/share/CasjaysDev/dockermgr/jenkins"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/jenkins/volumes/." "$HOME/.local/share/srv/docker/jenkins/volumes/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-jenkins \
--hostname jenkins \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/volumes/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/volumes/config:/config:z" \
-p 80:80 \
casjaysdevdocker/jenkins:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/jenkins
    container_name: casjaysdevdocker-jenkins
    environment:
      - TZ=America/New_York
      - HOSTNAME=jenkins
    volumes:
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/volumes/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/volumes/config:/config:z"
    ports:
      - 80:80
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/jenkins
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/jenkins" "$HOME/Projects/github/casjaysdevdocker/jenkins"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/jenkins"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
