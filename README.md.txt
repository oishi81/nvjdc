# nvjdc

### 🚩 一键安装nvjdc+XDD面板命令

``` bash
bash -c "$(curl -fsSL git.io/J1pMg)"
```

## docker安装教程

如果你是装过NVjdc 先看看后面1.2以前如何更新之1.2升级说明

1拉源码
国内
```
git clone https://ghproxy.com/https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```
国外
```
git clone https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```


2 拉取基础镜像以后不需要拉取镜像了 如果需要拉取我会通知
```
sudo docker pull nolanhzy/nvjdc:latest
```

3 执行命令

```
yum install wget unzip -y
```

4创建一个目录放配置

```
 cd /root/nvjdc
```
```
mkdir -p  Config && cd Config
```

5下载config.json 配置文件 并且修改自己的配置 不能缺少
源码库已经关闭了Json 需要自行需找。

```
wget -O Config.json  https://raw.githubusercontent.com/shidahuilang/nvjdc/main/Config.json
```
国内请使用
 ```
wget -O Config.json   https://ghproxy.com/https://raw.githubusercontent.com/shidahuilang/nvjdc/main/Config.json
```

6 回到nolanjdc目录创建chromium文件夹并进入

```
cd /root/nolanjdc && mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

7下载 chromium 

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

8删除刚刚下载的压缩包 

```
rm  -f chrome-linux.zip
```

9回到刚刚创建的目录

```
cd  /root/nvjdc
```



10启动镜像

```
sudo docker run   --name nolanjdc -p 5701:80 -d  -v  "$(pwd)":/app \
-v /etc/localtime:/etc/localtime:ro \
-it --privileged=true  nolanhzy/nvjdc:latest
```

11查看 日志 

```
docker logs -f nvjdc 
```

  

出现 NETJDC  started 即可 


## 1.2以前如何更新之1.2
如果你是装过NVjdc 并且root下存在nvjdc 文件夹

并且你的浏览器和配置已经在/root/nvjdc文件下了


请你将你现有的/root/nvjdc更换名称 如nvjdc1
```
mv /root/nvjdc /root/nvjdc1
```

然后执行步骤一 拉取代码
国内
```
git clone https://ghproxy.com/https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```
国外
```
git clone https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```


然后将刚刚更换名称文件夹 如nvjdc1中的 配置文件放到/root/nvjdc/Config 文件夹中
```
 cd /root/nvjdc &&  mkdir -p  Config &&  mv /root/nvjdc1/Config.json /root/nvjdc/Config/Config.json
```

将刚刚更换名称文件夹 如nvjdc1 中的浏览器所有文件放到/root/nvjdc/.local-chromium/Linux-884014 文件夹中
```
 cd /root/nvjdc &&    mv /root/nvjdc1/.local-chromium /root/nvjdc/.local-chromium
```

删除容器
```
docker rm -f nvnjdc 
```
然后从步骤9开始即可

后续更新只需要按照下方代码更新即可


## 更新

```
cd /root/nvjdc
```
```
docker stop nvjdc
```
```
git pull
```
```
docker start nvjdc
```

