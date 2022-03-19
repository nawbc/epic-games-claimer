# 自用备份
# 生成docker镜像
下载项目为zip，cd到解压的目录，然后运行这个命令就可以生成docker镜像了

docker build -t luminoleon/epicgames-claimer .
# EpicGames Claimer

<!-- [START badges] -->

<!-- ![](https://img.shields.io/badge/language-python-3572A5.svg) ![](https://img.shields.io/github/license/luminoleon/epicgames-claimer.svg) ![](https://img.shields.io/github/last-commit/luminoleon/epicgames-claimer.svg) -->

<!-- [END badges] -->

###### [疑难解答](docs/troubleshooting.md) | [Docker](docs/README_DOCKER.md)

> 自动领取Epic游戏商城[每周免费游戏](https://www.epicgames.com/store/free-games)。

十分简单易用，使用过程中几乎不需要输入或修改任何参数。

# 开始

## Docker

* 基于Ubuntu
    
    ``` bash
    docker run -it chyuz/epic-claimer
    ```

使用方法见[README_DOCKER.md](docs/README_DOCKER.md)。

## Docker-compose
首先创建`docker-compose.yml`文件，内容如下:

```yaml
version: '3'
services:
    epic-a:
        image: luminoleon/epicgames-claimer
        container_name: epic-a
        restart: unless-stopped
        environment:
        - TZ=Asia/Shanghai
        - AUTO_UPDATE=true
        - EMAIL=邮箱
        - PASSWORD=密码
    epic-b:
        image: luminoleon/epicgames-claimer
        container_name: epic-b
        restart: unless-stopped
        environment:
        - TZ=Asia/Shanghai
        - AUTO_UPDATE=true
        - EMAIL=另一个邮箱
        - PASSWORD=另一个密码
```

然后执行命令:

```bash
docker-compose up -d
```
    
## Python

### 如何使用

详见[python配置方法](docs/README_PYTHON.md)


### 腾讯云函数

详见[腾讯云函数配置方法](docs/README_TencentCloudFunction.md)

## 已知问题

Windows系统中途结束脚本可能导致浏览器进程留在后台。请检查任务管理器并手动结束浏览器进程。

## crontab表达式
[crontab表达式验证](https://www.matools.com/crontab)

**注意：由于Epic游戏商城限制了单个IP地址领取免费游戏的总量，所以使用公共IP领取游戏可能会失败。**
