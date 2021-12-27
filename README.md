# nvjdc
 青龙对接nvjdc短信登陆
 # nvjdc

### 🚩 一键安装nvjdc+XDD面板命令

``` bash
bash -c "$(curl -fsSL git.io/J1pMg)"
```

## docker安装教程


1拉源码
国内
```
git clone https://ghproxy.com/https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```
国外
```
git clone https://github.com/shidahuilang/nvjdc.git /root/nvjdc
```


2 拉取基础镜像
```
sudo docker pull shidahuilang/nvjdc:latest
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

6 回到nvjdc目录创建chromium文件夹并进入

```
cd /root/nvjdc && mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
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
sudo docker run   --name nvjdc -p 5701:80 -d  -v  "$(pwd)":/app \
-v /etc/localtime:/etc/localtime:ro \
-it --privileged=true  shidahuilang/nvjdc
```

11查看 日志 

```
docker logs -f nvjdc 
```

  

出现 NETJDC  started 即可 




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


