---
description: 使用端口转发托管Fika服务器的逐步过程。
---

# 使用端口转发托管

端口转发是一种网络过程，允许外部设备访问您家庭网络中计算机的一个或多个端口。端口转发可以通过路由器的设置界面进行配置，通常通过在Web浏览器中输入网关IP地址来访问。

{% hint style="warning" %}
并非所有互联网服务提供商（ISP）都允许端口转发。如果您发现自己无法进行端口转发，您可以使用公共VPN服务，如Radmin、ZeroTier等。点击[此处](host-using-a-vpn.md)了解如何使用VPN进行托管。
{% endhint %}

## 路由器配置

{% hint style="info" %}
我们不提供端口转发的逐步教程，因为路由器设置界面在不同型号和制造商之间有所不同。请确保研究如何为您的特定路由器型号实现端口转发。

您可能可以在[PortForward.com](https://portforward.com/)上或通过搜索Google找到您路由器的指南。
{% endhint %}

* 进入路由器的配置界面（打开浏览器并输入[网关IP](https://www.whatismyip.com/finding-your-default-gateway-address/)）。
* 访问端口转发菜单。
* 将以下端口转发到您的计算机：
  * 6969 TCP（SPT后端服务器）。
  * 25565 UDP（Fika游戏内网络）。

{% hint style="info" %}
如果您在与运行`SPT.server.exe`不同的PC上游戏，则需要将UDP（默认为25565）转发到游戏PC，而不是运行`SPT.server.exe`的机器。
{% endhint %}

## Windows防火墙

使用Fika-Installer安装Fika将自动配置Windows防火墙。

## 测试连接

* 启动`SPT.Server.exe`。

如果一切正常工作，您应该在控制台输出中看到类似以下内容：

```
ModLoader: loading: 1 server mods...
Mod: server version: 2.4.0 by: Fika loaded
Server: executing startup callbacks...
Importing database...
Database import finished
Started webserver at https://0.0.0.0:6969
Started websocket at wss://0.0.0.0:6969
Server is running, do not close while playing SPT, Happy playing!!
```

{% hint style="warning" %}
如果您看到错误（红色文本），则您的配置无效或您无法使用配置的IP地址/端口进行托管。
{% endhint %}

* 确保`SPT.Server`正在运行。
* 在[此处](https://api.ipify.org/)获取您的公共IP地址。
* 转到[在线端口检查器](https://portchecker.co)。
* 输入您的公共IP地址和端口6969。
* 测试端口连接。

如果端口关闭，您可能有无效配置，Windows防火墙阻止连接或您的ISP不允许端口转发。验证所有网络设置或使用[VPN客户端](host-using-a-vpn.md)进行托管。

如果端口显示为打开，您的服务器可供朋友连接。您需要将格式为`https://your.pub.lic.ip:6969`的公共IPv4发送给他们，以便他们将其输入到启动器->设置->URL字段中连接到您的服务器。

## 托管突袭

您的Fika实例现在已准备好托管突袭。

* [点击此处](../playing-fika.md#hosting-a-raid)了解如何托管突袭。
* [点击此处](../fika-configuration/)了解有关其他Fika配置的更多信息。
