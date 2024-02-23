# 我为人人, 人人为我

## Xrayr共享节点， 机场节点共享

## 测试中， 订阅链接可能会变， 欢迎提出建议

## 自动侦测 是否被墙屏蔽

### 无需复杂的V2Board/SSPanel安装
### 共享一台节点，获得其它人的节点，降低被封风险

以AWS Lightsail Ubuntu 为例 安装步骤如下

 1. 安装 Docker

```
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
sudo apt-get install docker-ce docker-ce-cli containerd.io -y

```
回车
```
sudo systemctl start docker
sudo systemctl enable docker
```

2. 安装Docker-compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.26.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
3. Docker-compose 安装XrayR

   ```
   git clone https://github.com/XrayR-project/XrayR-release
   cd XrayR-release
   wget https://github.com/hello-world-1989/xrayr-share/raw/main/config.yml

   ```
4. [自助生成一个 UUID](https://www.uuidgenerator.net/) 并替换 your-uuid-token, uuid例子 34498b58-d63d-432d-938f-b29b1f28fb9a

   ```
   sed -i "s/your-uuid-token/你的uuid/" ./config.yml
   ```
5. `mv config.yml config/config.yml`
6. `sudo docker-compose up -d`
7. `sudo docker-compose ps` 应该能看到 Up 状态, 如果不能， `sudo docker-compose logs` 查看日志发送到[电报群](https://t.me/EndGFWUnion)

8.  你的订阅链接如下， 替换为你的UUID
   `https://t5uxwur5pwqcpcm4jifn2hlnm40mcrow.lambda-url.us-east-1.on.aws/api/v1/client/subscribe?token=your-uuid-token`

9. 防火墙放开 8880, 8886, 8888 端口, 禁用 IPV6

