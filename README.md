## Debian & Ubuntu 安装docker
### 卸载旧版本
- 旧版本的 Docker 被称为docker,docker.io或docker-engine. 如果安装了这些，请卸载它们：
```bash
sudo apt-get remove docker docker-engine docker.io containerd runc
```
### 设置存储库
- 更新apt包索引并安装包以允许apt通过 HTTPS 使用存储库：
```bash
sudo apt-get update -y
sudo apt-get install -y ca-certificates curl gnupg lsb-release
```
添加 Docker 的官方 GPG 密钥：
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
- 使用以下命令设置存储库：
```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
### 安装 Docker
- 更新apt包索引，安装最新版本的 Docker Engine、containerd 和 Docker Compose，或者进入下一步安装特定版本：
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```
- hello-world 通过运行映像来验证 Docker 引擎是否已正确安装。
```bash
sudo docker run hello-world
```
### 示例输出验证
```
$ sudo docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/


$ sudo docker images hello-world
REPOSITORY   TAG     IMAGE ID      SIZE
hello-world  latest  feb5d9fea6a5  13256
```
 ### 祝你成功~
