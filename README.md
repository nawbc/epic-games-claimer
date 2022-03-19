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

## 开始

### Docker

* 基于Ubuntu
    
    ``` bash
    docker run -it chyuz/epic-claimer
    ```

使用方法见[README_DOCKER.md](docs/README_DOCKER.md)或[Docker hub页面](https://hub.docker.com/r/chyuz/epic-claimer)。

### Docker-compose
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
    
### Python

要求Python >= 3.6。

#### 如何使用

详见[python配置方法](docs/README_PYTHON.md)

## 部署

**注意：由于Epic游戏商城限制了单个IP地址领取免费游戏的总量，所以使用公共IP领取游戏可能会失败。**

### 腾讯云函数

需要关闭双重验证。

目前不支持自动更新。

需要上传的文件：epicgames_claimer.py，requirements.txt

执行方法：epicgames_claimer.main_handler

推荐配置：内存1024MB，执行超时时间900秒

#### 环境变量

| 变量                       | 说明                                                                     | 备注                                    |
| -------------------------- | ------------------------------------------------------------------------ | --------------------------------------- |
| EMAIL                      | 设置用户名/邮箱                                                          |                                         |
| PASSWORD                   | 设置密码                                                                 |                                         |
| PUSH_SERVERCHAN_SENDKEY    | 设置Server酱SendKey                                                      |                                         |
| PUSH_BARK_URL              | 设置Bark服务端地址                                                       | 默认: https://api.day.app/push          |
| PUSH_BARK_DEVICE_KEY       | 设置Bark的DeviceKey                                                      |                                         |
| PUSH_TELEGRAM_BOT_TOKEN    | 设置Telegram bot token                                                   |                                         |
| PUSH_TELEGRAM_CHAT_ID      | 设置Telegram chat ID                                                     |                                         |
| PUSH_WECHAT_QYWX_AM        | 设置企业微信应用推送的QYWX_AM                                            | 参考：http://note.youdao.com/s/HMiudGkb |
| PUSH_DINGTALK_ACCESS_TOKEN | 设置钉钉群聊机器人access token                                           |                                         |
| PUSH_DINGTALK_SECRET       | 设置钉钉群聊机器人secret                                                 | 没有勾选加签则不需要此参数              |
| PUSH_WHEN_OWNED_ALL        | 设置为true时，当执行领取过程中发现全部可用周免游戏都已领取时推送一条通知 | 默认没有游戏被领取时不会推送通知        |

#### 如何安装python模块和浏览器

使用在线编辑器中的集成终端打开src目录，运行以下命令（点（`.`）是命令的一部分，请不要忽略它们）。

```bash
pip3 install -r requirements.txt -t .
mv bin/pyppeteer-install .
./pyppeteer-install
cp -r /root/.local/share/pyppeteer/local-chromium/*/chrome-linux .
```

运行完成后点击“部署”按钮使修改生效。

## 已知问题

Windows系统中途结束脚本可能导致浏览器进程留在后台。请检查任务管理器并手动结束浏览器进程。

## crontab表达式
[crontab表达式验证](https://www.matools.com/crontab)
