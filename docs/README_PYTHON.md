1. 克隆

    ``` bash
    git clone -b main https://github.com/cyz0105/epic-games-claimer.git
    cd epic-games-claimer
    ```

2. 安装Python模块

    ``` bash
    pip3 install -r requirements.txt
    ```

3. 安装依赖（仅Linux）

    ``` bash
    sudo sh install_dependencies.sh
    ```

4. 运行

    ``` bash
    python3 main.py
    ```

    <details>
    <summary>启用自动更新</summary>

    ```bash
    python3 main.py --auto-update
    ```

    </details>

    <details>
    <summary>不使用交互输入</summary>

    ```bash
    python3 main.py -u <你的邮箱> -p <你的密码>
    ```

    ```bash
    python3 main.py -u <你的邮箱> -p <你的密码> -t <双重验证代码>
    ```

    </details>

    <details>
    <summary>添加通知推送</summary>

    * server酱
        ```bash
        python3 main.py -ps <SendKey>
        ```

    * Bark
        ```bash
        python3 main.py -pbu <BarkPushUrl> -pbk <BarkDeviceKey>
        ```

	    非自建服务端无需-pbu参数，默认采用官方推送地址https://api.day.app/push

    * Telegram
        ```bash
        python3 main.py -ptt <TelegramBotToken> -pti <TelegramChatId>
        ```

    </details>

#### Python版本可选参数

| 参数                                   | 说明                                                       | 备注                                                                                                                                       |
| -------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `-n`, `--no-headless`                  | 显示浏览器的图形界面                                       |                                                                                                                                            |
| `-c`, `--chromium-path`                | 指定浏览器可执行文件路径                                   |                                                                                                                                            |
| `-r`, `--run-at`                       | 指定每日运行时间                                           | 格式：HH:MM，默认为当前时间                                                                                                                |
| `-o`, `--once`                         | 运行一次领取过程后退出                                     | [参数`--once`或环境变量`ONCE`的具体含义，应在什么情况下使用](docs/troubleshooting.md#参数--once或环境变量once的具体含义应在什么情况下使用) |
| `-a`, `--auto-update`                  | 启用自动更新                                               | 运行`epicgames_claimer.exe`或`epicgames_claimer.py`此参数无效                                                                              |
| `--cron`                               | 使用cron表达式运行定时任务                                 | 默认每天当前时间执行一次。运行`epicgames_claimer.exe`或`epicgames_claimer.py`此参数无效                                                    |
| `-u`, `--username`                     | 设置用户名/邮箱                                            |                                                                                                                                            |
| `-p`, `--password`                     | 设置密码                                                   |                                                                                                                                            |
| `-t`, `--verification-code`            | 设置双重验证代码                                           |                                                                                                                                            |
| `--cookies`                            | 设置保存cookies信息文件路径                                | 用`get_cookies.py`或者`get_cookies.exe`获取                                                                                                |
| `-l`, `--login`                        | 登录并创建User_Data后退出                                  | 需要在打开的浏览器里手动完成登录    
| `--push-lang`    			 | 通知语言                               | zh, en, ru
| `-ps`, `--push-serverchan-sendkey`     | 设置Server酱SendKey                                        |                                                                                                                                            |
| `-pbu`, `--push-bark-url`              | 设置Bark服务端地址                                         | 默认: https://api.day.app/push                                                                                                             |
| `-pbk`, `--push-bark-device-key`       | 设置Bark的DeviceKey                                        |                                                                                                                                            |
| `-ptt`, `--push-telegram-bot-token`    | 设置Telegram bot token                                     |                                                                                                                                            |
| `-pti`, `--push-telegram-chat-id`      | 设置Telegram chat ID                                       |                                                                                                                                            |
| `-pwx`, `--push-wechat-qywx-am`        | 设置企业微信应用推送的QYWX_AM                              | 参考：http://note.youdao.com/s/HMiudGkb                                                                                                    |
| `-pda`, `--push-dingtalk-access-token` | 设置钉钉群聊机器人access token                             |                                                                                                                                            |
| `-pds`, `--push-dingtalk-secret`       | 设置钉钉群聊机器人secret                                   | 没有勾选加签则不需要此参数                                                                                                                 |
| `-ns`, `--no-startup-notification`     | 禁用脚本启动时推送一条通知                                 |                                                                                                                                            |
| `--push-when-owned-all`                | 当执行领取过程中发现全部可用周免游戏都已领取时推送一条通知 | 默认没有游戏被领取时不会推送通知                                                                                                           |
| `-v`, `--version`                      | 显示版本信息并退出                                         |                                                                                                                                            |
