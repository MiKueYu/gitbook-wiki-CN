---
description: 在本地网络中托管Fika服务器的逐步过程。
---

# 通过局域网托管

通过局域网托管允许您与同一房屋/网络中的人一起玩游戏，无需互联网访问，也无需真正的端口转发，只需允许本地防火墙中的应用程序即可。

## 获取您的本地IP

托管局域网需要您的本地IP地址。按照以下步骤获取它。

* 按`Windows键`并输入`cmd`。

<figure><img src="../.gitbook/assets/win_run_cmd.png" alt="" width="563"><figcaption></figcaption></figure>

* 在命令提示符中输入`ipconfig`，然后按`回车`。
* 找到您正在使用的网络适配器（以太网或Wi-Fi）。可能有多个以太网适配器 - 确保识别正确的那个。
* 找到IPv4地址条目并记下IP地址，例如`192.168.0.152`。这在下面将被称为`your_lan_ip`。

<figure><img src="../.gitbook/assets/fika_ipconfig.png" alt=""><figcaption><p>您的本地IP地址应出现在以太网适配器下（如果您的连接是有线的）</p></figcaption></figure>

## 配置Windows防火墙

使用Fika-Installer安装Fika将自动配置Windows防火墙。

## 在Fika中配置您的本地IP

* 至少启动一次`SPT.Server.exe`以生成配置文件，然后关闭它。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FtXMCT7qmRaqYnXrLE8Tr_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>

* 导航到您的`user\mods\fika-server\assets\configs`&#x20;
* 打开`fika.jsonc`。
* 找到`server`部分。
* 将`ip`更改为`your_lan_ip`。
* 将`backendIp`更改为`your_lan_ip`。
* 保存文件并关闭它。

<figure><img src="../.gitbook/assets/fika_jsonc_lan.png" alt=""><figcaption></figcaption></figure>

* 启动`SPT Server`

如果一切正常工作，您应该在控制台输出中看到类似以下内容：

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at https://<your_lan_ip>:6969
Started websocket at wss://<your_lan_ip>:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
如果您看到错误（红色文本），则您的配置无效或您无法使用配置的IP地址/端口进行托管。
{% endhint %}

* 启动`SPT Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FQIK2fJ1ONoqXIAA3v9tl_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>

* 点击`设置`按钮

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FqwHM3gxlwjEsrugHTtc0_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

* 选中`Developer Mode`框。
* 在URL部分输入您的本地IP地址。不要省略`https://`，也不要添加结尾斜杠。URL框应该看起来像这样：`https://192.168.0.33:6969`。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FRJRDafOFXrz8sQBMXNfo_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

* 按右角的箭头。
* 您现在应该能够创建您的配置文件并登录到服务器。
* 启动游戏。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* 在游戏中按`F12`以调出配置管理器。
* 在配置管理器的`Fika.Core`部分找到`Force IP`和`Force Bind IP`。
* 将`Force IP`和`Force Bind IP`都设置为`your_lan_ip`。

<figure><img src="../.gitbook/assets/fika_lan_f12.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
注意：愿意托管突袭的玩家还需要在各自的Fika配置中设置`Force IP`和`Force Bind IP`。
{% endhint %}

## 测试连接

* 请您的朋友从同一本地网络内的计算机ping您的本地IP地址。

如果ping失败，则意味着您获取了错误的本地IP地址或您的网络配置无效。验证您的网络设置。

## 托管突袭

您的Fika实例现在已准备好托管突袭。

* [点击此处](../playing-fika.md#hosting-a-raid)了解如何托管突袭。
* [点击此处](../fika-configuration/)了解更多关于其他Fika配置的信息。
