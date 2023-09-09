# Deploy Docker in Ubuntu

## Uninstall old versions
```text
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```

## Install using the Apt repository

```text
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update 
```

### Install the Docker packages.
```text
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Verify that the Docker Engine installation is successful by running the hello-world image.
```text
sudo docker run hello-world
```


## Docker Command

### docker 常用命令
- 启动名为 naocs 的容器 docker start nacos  
- 停止名为 nacos 的容器 docker stop nacos  
- 重启名为 nacos 的容器 docker restart nacos  
- 删除名为 nacos 的容器 docker rm -v nacos  
- 跟踪容器日志 docker logs -f nacos  
- 列出所有启动和未启动的容器 docker ps -a  
- 列举所有的 images docker images -a  
- docker cp nacos:/home/data /root/volumes/nacos/home  
- 将nacos 容器内 /home/data 路径下的数据 copy 到 本地 /root/volumes/nacos/home 下  
- docker build -t name:1.0 -f ./Dockerfile . 以当前文件夹下 Dockerfile 文件构建镜像  
- docker compose -f ./docker-compose.yml up 以当前文件夹下的 docker-compose.yml 文件构建服务  
- docker attach 'container_name' 连接容器 (Ctrl + p Ctrl +q) 断开连接  
- docker pull 拉取镜像 image  
- docker exec -it 'container_name' /bin/bash  
### docker container  
- ls 列举现存容器  
- stop 'container_name'... 停止列举的容器名  
- rm 'container_name'... 删除列举的容器名  
### docker network  
- ls 列举现存网络  
- inspect 'network_name' 查看网络信息  
- rm 'network_name' 删除网络  
- connect 'network_name' 'container_name' 将某单例容器加入到某网络  
- disconnect 'network_name' 'container_name' 将某单例容器断开某网络  
