---
description: 为专用SPT服务器设置NAT穿孔的逐步过程。
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# NAT穿孔

## 什么是NAT穿孔？

NAT穿孔是一种[NAT穿越技术](https://en.wikipedia.org/wiki/NAT_traversal)，允许位于不同路由器后的两个设备建立直接的点对点连接。当由于ISP或网络限制而无法进行端口转发时，这尤其有用。

然而，并非所有路由器都支持NAT穿孔。例如，**对称NAT**路由器通常由于其处理外部端口映射的方式而阻止成功的NAT穿孔。

## 它是如何工作的？

公共服务器监听来自客户端的传入连接，并记录它们的外部IP地址和端口。然后通过共享对方的外部IP地址来介绍每个客户端。例如，`客户端1`接收`客户端2`的外部IP地址，反之亦然。

这就是NAT穿孔发生的时候：当`客户端1`接收到`客户端2`的IP地址时，它开始向`客户端2`发送多个数据包（即"穿孔"）。同时，`客户端2`向`客户端1`发送数据包，在两个客户端的路由器中创建路由条目。

此时，两个路由器都允许通过此特定路由进行通信，然后可以利用该路由来托管`Fika`突袭。

## 要求

* SPT服务器必须托管在外部可访问的机器上，例如VPS。
* 突袭主机和通过NAT穿孔连接的任何玩家都必须使用支持全锥形NAT的路由器，因为这是正常连接所必需的。您可以通过在线搜索您特定的路由器型号来检查路由器的NAT类型。

## 注意事项

本指南仅涵盖Windows的安装过程。Linux不在本文涵盖范围内，但原理是相同的。请查看我们在Discord中的专用Linux频道了解更多信息。

## 安装

{% stepper %}
{% step %}
### 设置公共Windows服务器

NAT穿孔需要公共服务器。建议租用便宜的Windows VPS来托管`SPT服务器`；[**LowEndBox**](https://lowendbox.com/)上列出的提供商是低成本选项的良好起点。

如果您不确定NAT穿孔是否适用于您的网络配置，可以使用[**Kamatera**](https://www.kamatera.com/)配置临时VPS，它提供按小时计费——使其成为测试的经济高效解决方案。
{% endstep %}

{% step %}
### 下载最新的`SPT`独立版本

在此处获取最新的SPT独立版本[https://github.com/sp-tarkov/build/releases/](https://github.com/sp-tarkov/build/releases/)。下载链接将在发布说明中。
{% endstep %}

{% step %}
### 在新的空`SPT`文件夹中解压`SPT`存档

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 下载最新的`Fika-Server`独立版本

在此处获取最新的`Fika-Server`独立版本[https://github.com/project-fika/Fika-Server-CSharp/releases](https://github.com/project-fika/Fika-Server-CSharp/releases)。
{% endstep %}

{% step %}
### 在`SPT`安装文件夹的根目录中解压Fika-Server存档

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Server.exe`以生成Fika服务器配置文件

`SPT.Server.exe`位于`SPT`安装文件夹的`SPT`子文件夹中。

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 等待`SPT`服务器完全加载然后关闭它

当您看到`Server has started, happy playing`时关闭`SPT`服务器。

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 在Fika服务器中启用NAT穿孔

此设置控制`Nat Punch Server`是否应在您的SPT服务器上运行。

* 导航到`SPT\user\mods\fika-server\assets\configs`。
* 使用您首选的文本编辑器软件打开`fika.jsonc`（推荐使用`Notepad++`）。
* 找到`natPunchServer`部分并将`enable`设置为`true`。

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

* 保存并退出文本编辑器。
{% endstep %}

{% step %}
### 启动`SPT.Server.exe`

验证`Nat Punch Server`是否成功加载。

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 验证您的网络配置

确保以下端口已在您的服务器防火墙中进行端口转发并打开：

* 6969 TCP（SPT服务器）
* 6790 UDP（Nat Punch服务器）
{% endstep %}

{% step %}
### 在您的计算机上启动`SPT.Launcher`

我们假设您已经有一个正常工作的Fika安装或您知道如何设置一个。如果没有，请点击[此处](../installing-fika/)了解Fika安装步骤。
{% endstep %}

{% step %}
### 在`SPT Launcher`中配置您的服务器IP

`SPT Launcher`需要连接到您VPS/公共服务器上的`SPT`服务器。其他玩家也需要执行以下步骤。

* 单击右上角的`Settings`按钮。

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

* 选中`Developer Mode`框，然后在URL框中输入您的服务器IP地址。不要删除`https://`，不要在末尾添加斜杠。
* 按右上角的箭头键保存设置。

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动游戏

按`Start Game`启动游戏。

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 在Fika中启用NAT穿孔（仅突袭主机）

此设置表示连接到您突袭的任何玩家都必须使用NAT穿孔。这是一个客户端设置，意味着它仅适用于**您**，突袭主机。其他玩家不需要启用此设置，除非他们打算在没有端口转发的情况下主持突袭。

* 按F12打开配置管理器。
* 选中`Advanced settings`框。
* 选中`Nat Punching`框以启用NAT穿孔。

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 托管突袭并等待其他玩家连接

浏览菜单并托管突袭。您应该看到您的服务器已添加到`SPT Server`控制台中的Nat Punch服务器列表中。

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

`Nat Punch Server`将向加入您突袭的玩家介绍您的计算机的外部IP地址。

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 在所有玩家连接后启动突袭

当所有玩家都连接并准备好时启动突袭。
{% endstep %}
{% endstepper %}

## 无头客户端

要在`headless client`中启用NAT穿孔：

* 确保您已按照上述所有步骤操作。
* 导航到`headless client`的`BepInEx\config`。
* 使用您首选的文本编辑器打开`com.fika.core.cfg`。
* 搜索参数`Use NAT Punching`并设置为`true`。
* 保存并关闭文本编辑器。

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>