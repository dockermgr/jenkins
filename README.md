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
mkdir -p "$HOME/.local/share/srv/docker/jenkins/rootfs"
git clone "https://github.com/dockermgr/jenkins" "$HOME/.local/share/CasjaysDev/dockermgr/jenkins"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/jenkins/rootfs/." "$HOME/.local/share/srv/docker/jenkins/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-jenkins \
--hostname jenkins \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/rootfs/data:/data:z" \
-v "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/rootfs/config:/config:z" \
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
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/rootfs/data:/data:z"
      - "$HOME/.local/share/srv/docker/casjaysdevdocker-jenkins/rootfs/config:/config:z"
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
