---
title: Docker备忘录
date: 2024-07-17 12:10:43
tags:
    - 备忘录
    - Docker
---
{% folding blue::安装 For Linux %}

For Centos/RedHat/Rocky

``` Shell
sudo yum install -y yum-utils
# 使用官方源
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# 或使用Aliyun源
sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
# 安装组件
sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
# 启动服务
sudo systemctl start docker
# 添加到自启动
sudo systemctl enable docker
```
 
{% endfolding %}