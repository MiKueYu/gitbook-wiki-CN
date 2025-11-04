---
icon: comments-question-check
---

# 常见问题和指南

{% hint style="info" %}
## 其他指南和答案

通过点击左上角的 <i class="fa-bars">:bars:</i> 可以在目录中找到其他常见问题和指南。

如果您有这里未涵盖的问题，请加入我们的 [Discord](https://discord.gg/project-fika) 服务器并在 #questions 频道中提问。
{% endhint %}

### :question:我更改了 `http.json` 但我的服务器仍然显示 `0.0.0.0`

{% hint style="warning" %}
请不要观看视频指南，它们通常已过时。
{% endhint %}

需要编辑IP的唯一位置是在 [`fika.jsonc`](../fika-configuration/server.md) 中

* 您必须在安装 `fika-server` 的情况下至少运行一次 `SPT.Server.exe` 以生成 `fika.jsonc`。

请按照 <a href="../hosting-a-fika-server/" class="button primary" data-icon="arrow-right-long">托管Fika服务器</a> 的说明操作

***

### :question:我在主菜单的在线玩家列表中看不到我的朋友 / 我在突袭列表中看不到朋友的突袭

{% hint style="warning" %}
<mark style="color:$warning;">**组中只有一个人启动 SPT.Server.exe。**</mark>
{% endhint %}

* 决定谁是服务器主机。只有那个人运行 `SPT.Server.exe` 并遵循 [托管Fika服务器](../hosting-a-fika-server/) 的说明。
* 其他人都**不运行 `SPT.Server.exe`** 而是遵循 [加入Fika服务器](../joining-a-fika-server/) 的说明。
* 确保所有人都已安装 [Fika](../installing-fika/)。在主菜单中，屏幕左下角应该显示FIKA。

***

### :question:加入突袭时出现关于打开端口的错误

{% hint style="info" %}
**确保每个人都在正确地** [**托管/加入突袭的说明**](../playing-fika.md)。
{% endhint %}

#### 如果您**没有**使用无头客户端，您的组正在使用Radmin VPN（或任何其他VPN客户端）

* 点击 `HOST RAID` 按钮的人需要**严格按照以下说明**操作：
  * 在您的F12配置菜单中的Fika.Core插件设置中导航并向下滚动到网络头部。从 `Force Bind IP` 下拉选择框中选择<mark style="color:$warning;">**您自己的VPN IP**</mark>，然后在上面的 `Force IP` 框中输入<mark style="color:$warning;">**完全相同的IP**</mark>。\
    \
    如果您在 `Force Bind IP` 选择框中看不到正确的IP，请确保您已安装VPN客户端并已连接，然后仔细重读上面的段落。\
    \
    如果您已启用高级选项可见性，则UPnP和NAT穿透都应为**禁用**。如果您没有看到这些选项，请忽略此条目，因为它们默认是禁用的。

#### 如果您**没有**使用无头客户端，您的组正在使用端口转发

* 点击 `HOST RAID` 按钮的人需要确保他们已在路由器中将25565/udp端口转发到他们正在玩SPT的PC。突袭由点击 `HOST RAID` 的人的游戏客户端托管，而不是由 `SPT.Server` 后端服务器托管。
* 确保F12 -> Fika.Core -> 网络中的所有设置都是**默认值**：
  * `Force IP` 应为空
  * `Force Bind IP` 应为禁用或 `0.0.0.0`
  * 端口应与创建端口转发规则的端口匹配（25565是默认值）
  * 如果您已启用高级选项可见性，则UPnP和NAT穿透都应为**禁用**。如果您没有看到这些选项，请忽略此条目，因为它们默认是禁用的。

#### 如果您正在使用无头客户端

* 如果您正在使用无头客户端托管突袭并遇到此错误，您需要确保无头客户端被设置为接受传入连接，方式与任何普通客户端相同。&#x20;
  * **如果您正在使用端口转发**，25565/udp的端口转发规则需要指向运行无头客户端的PC。`BepInEx/config/com.fika.core.cfg -> Network` 部分中的所有设置都应该是**默认值**。
  *   **如果您正在使用VPN**，您需要在文本编辑器中打开 `<headless install>/BepInEx/config/com.fika.core.cfg` 并确保无头客户端机器的VPN IP已设置为 `Force IP` 和 `Force Bind IP`。VPN客户端也必须安装并配置在无头客户端PC上。

      <figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

***

### :question:F8无法成功将我从突袭中提取

这有两个常见原因：要么是模组导致错误，要么是某些程序拦截了F8按键。

尝试按F12调出BepInEx配置管理器设置窗口。如果这起作用了，尝试找到Fika.Core设置中的提取热键并将其重新绑定到其他键位。

如果F12不起作用，或者您无法将提取热键重新绑定到其他键（或如果显示它被绑定到F13），您可能有某些程序拦截了F键。这通常是Overwolf或MSI Afterburner等覆盖软件，或者可能是插入了拦截F键的游戏杆/方向盘/其他控制器。尝试关闭所有覆盖软件并拔掉所有控制外设。

如果以上都没有解决问题，可能是某个模组导致了问题。您必须通过ALT+F4关闭游戏客户端，然后查看以下文件夹中的Player.log文件：

```
C:\Users\YOURUSERNAME\AppData\LocalLow\Battlestate Games\EscapeFromTarkov\
```

在文本编辑器中打开Player.log并搜索 `F8 pressed`，看看附近是否有任何错误提示可能是哪个模组导致的问题。如果您不确定，请访问[Discord](https://discord.gg/project-fika) #questions频道，解释您已尝试的操作并上传您的Player.log以获得帮助。

***

### :question: 我无法在F12 -> Fika.Core设置中启用任务分享

查看fika-server模组[配置选项](../fika-configuration/server.md)。这些更改必须由服务器主机完成。

在文本编辑器中打开`fika.jsonc`，找到名为`sharedQuestProgression`的选项，将其从`false`更改为`true`，然后保存更改并重启服务器。

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

***

### :question:我可以使启动器不显示所有人的配置文件吗？

查看fika-server模组[配置选项](../fika-configuration/server.md)。这些更改必须由服务器主机完成。

在文本编辑器中打开`fika.jsonc`，找到名为`launcherListAllProfiles`的选项，将其从`true`更改为`false`，然后保存更改并重启服务器。

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

***

### :question:我可以启用SPT聊天机器人，如Commando吗？

查看fika-server模组[配置选项](../fika-configuration/server.md)。这些更改必须由服务器主机完成。

在文本编辑器中打开`fika.jsonc`，找到名为`disableSPTChatBots`的选项，将其从`true`更改为`false`，然后保存更改并重启服务器。

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

***

### :question:如何卸载Fika？

启动`Fika-Installer`并选择`Uninstall Fika`。

或者，您可以使用以下步骤手动操作：

* 导航到`BepInEx/plugins/Fika/`并删除`Fika.Core.dll`
* 导航到`SPT/user/mods/`并删除`fika-server/`文件夹
* 打开SPT.Launcher.exe，点击右上角的设置，（如果适用）将URL改回`https://127.0.0.1:6969`\
