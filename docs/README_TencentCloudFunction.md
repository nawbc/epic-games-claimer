腾讯云函数

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
