# `Love Calculator` Installation with docker and Jenkins.

Release linux server and install Jenkins and Docker

```sh
yum update -y
yum install docker -y
systemctl enable docker
systemctl start docker
yum install pip -y
pip install docker-py
wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
yum upgrade
amazon-linux-extras install java-openjdk11 -y
yum install jenkins -y
systemctl enable jenkins
systemctl start jenkins
yum install git -y
```
Make app directory and add Application files using git clone
```sh
rm -rf /opt/lovec/*
mkdir /opt/lovec
cd /opt/lovec
git clone https://github.com/Raam043/Love_Calculator.git
cp /opt/lovec/Love_Calculator/* /opt/lovec

```

Build Docker images and Run container 
```sh
docker stop lovec
docker rm -f lovec
docker image rm -f lovec
docker build -t lovec .
docker run --name lovec -d -p 80:80 lovec
```
Open New tab with `Server_Public_IP:`

With Above commands Jenkins CICD can be made
