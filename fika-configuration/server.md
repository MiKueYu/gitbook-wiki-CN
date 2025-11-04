---
description: 带有每个设置描述的默认服务器配置文件。
---

# 服务器

服务器配置可以在 `SPT\user\mods\fika-server\assets\configs` 文件夹中找到。用文本编辑器打开 `fika.jsonc`。您需要至少启动一次服务器以生成此文件。

{% hint style="info" %}
确保保存更改并在完成后重启服务器，以确保您的更改生效！
{% endhint %}

{% code fullWidth="true" %}
```json5
{
    "client": {
        "useBtr": true, // BTR是否应该生成
        "friendlyFire": true, // 是否启用友军伤害
        "dynamicVExfils": false, // 载辆撤离是否应根据玩家数量动态缩放
        "allowFreeCam": false, // 玩家是否可以在仍然存活时使用自由摄像机
        "allowSpectateFreeCam": false, // 玩家是否被迫观看其他玩家或是否可以自由移动
        "blacklistedItems": [], // 不能发送的物品
        "forceSaveOnDeath": false, // 玩家死亡时是否强制保存库存，以减轻ALT+F4作弊
        "mods": {
            "required": [], // 客户端需要的模组
            "optional": [] // 允许连接的可选模组
        },
        "useInertia": true, // 是否启用惯性，如果禁用，则表现得像什么都没穿一样
        "sharedQuestProgression": false, // 任务进度是否应该共享，也会影响共享经验值选项
        "canEditRaidSettings": true, // 客户端是否可以在开始突袭前修改突袭设置
        "enableTransits": true, // 如果启用转机
        "anyoneCanStartRaid": false // 是否任何人都可以点击"开始突袭"
    },
    "server": {
        "SPT": {
            "http": {
                "ip": "0.0.0.0", // 要监听的接口
                "port": 6969, // 要托管的端口
                "backendIp": "0.0.0.0", // 发送给客户端用于请求的IP
                "backendPort": 6969 // 发送给客户端用于请求的端口
            },
            "disableSPTChatBots": true // 强制聊天机器人关闭
        },
        "webhook": {
            "enabled": false,
            "name": "Fika服务器",
            "avatarUrl": "https://github.com/project-fika/Fika-Server-CSharp/blob/main/FikaWebApp/wwwroot/images/FIKA_LOGO.png?raw=true",
            "url": ""
        },
        "allowItemSending": true, // 允许玩家互相发送物品
        "itemSendingStorageTime": 7, // 发送的物品邮件在多久后过期
        "sentItemsLoseFIR": true, // 发送的物品是否失去其FIR状态
        "launcherListAllProfiles": true, // 是否在启动器中列出所有账户
        "sessionTimeout": 5, // 在不响应时，突袭被视为"丢失"需要多少分钟
        "showDevProfile": true, // 是否启用开发人员配置文件
        "showNonStandardProfile": true, // 是否启用非标准EFT配置文件
        "adminIds": [], // 允许与Mr Fika管理员机器人命令交互的配置文件ID列表
        "apiKey": "" // 与Fika API交互的API密钥
    },
    "natPunchServer": {
        "enable": false, // 是否启用NAT穿透模块
        "port": 6790, // 要使用的端口
        "natIntroduceAmount": 1
    },
    "headless": {
        "profiles": {
            "amount": 0, // 要生成/使用的配置文件数量
            "aliases": {
                "68eac997dc053e6fwhatever" : "NameOfHeadless" // 无头配置文件uid : 您希望在突袭主机屏幕上显示的名称
            } // 选择无头客户端时要显示的别名
        },
        "scripts": {
            "generate": true, // 是否应该生成无头脚本
            "forceIp": "https://127.0.0.1:6969" // 无头连接的URL
        },
        "setLevelToAverageOfLobby": true, // 在无头端生成机器人时使用所有玩家的平均等级
        "restartAfterAmountOfRaids": 0 // 无头是否应该在X次突袭后重启，0为禁用
    },
    "background": {
        "enable": true, // 启用自定义启动器背景
    }
}
```
{% endcode %}
