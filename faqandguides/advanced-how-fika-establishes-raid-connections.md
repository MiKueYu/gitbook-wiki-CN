---
description: >-
  本页将描述Fika如何协助客户端连接到突袭主机。如果您有非标准网络设置（代理、隧道、ddns、docker等），这可能有助于故障排除。
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

# 高级：Fika如何建立突袭连接

{% hint style="warning" %}
本文适用于具有非标准网络设置的高级用户。虽然对其他人来说可能很有趣，但如果您的网络简单，您最好只遵循[托管说明](../hosting-a-fika-server/)，而不用担心Fika的内部工作原理。如果端口转发不起作用，请使用[像Radmin这样的VPN](../hosting-a-fika-server/host-using-a-vpn.md)。
{% endhint %}

### 术语定义

* **SPT服务器/后端服务器**
  * SPT服务器或后端服务器指`SPT.Server.exe`，负责处理配置文件同步和仓库管理。它由fika-server模组修改，以允许玩家托管和加入突袭。
* **fika-server模组**
  * 这是对后端服务器的修改，允许托管的突袭填充到列表中并可由客户端加入。它将连接方法信息从突袭主机转发到加入的客户端。
* **Fika客户端插件**
  * 客户端插件是一种BepInEx插件，以.dll文件的形式存在于`BepInEx\plugins\Fika\`中，并为主持突袭的网络功能。它负责监听突袭主机的连接或为加入的客户端建立连接。当您在F12配置菜单中更改设置时，您实际上是在更改客户端插件的设置。
* **插件配置**
  * 这是在BepInEx配置管理器中可以更改的设置列表，通常通过在游戏客户端内按F12访问。这些值也可以通过在文本编辑器中打开`BepInEx/config/com.fika.core.cfg`并直接编辑值来修改。

## Fika网络工作流程

### 突袭如何向客户端宣传

当突袭主机开始为其他人连接设置突袭时，它首先查看客户端插件配置的`Force IP`字段。如果该字段已填充，它会将该IP存储在内存中，此后称为`IP_1`。如果`Force IP`字段为空，插件将尝试通过查询（在撰写时）三个IP解析服务来解析公共/WAN IP，然后将公共IP存储为`IP_1`。

客户端插件还将查询本地网络适配器并存储局域网IP（通常是`192.168.x.x`或`10.0.x.x`）作为`IP_2`。如果发生此情况的PC有多个本地网络适配器，那么如果有人尝试通过同一网络连接，您可能会遇到连接问题。

{% hint style="info" %}
例如，如果PC同时具有以太网连接和Wi-Fi连接，且两者都启用并连接，客户端插件可能会记录错误的局域网IP。重要的是PC在所有情况下只拥有一个活动的局域网适配器才能正常工作。
{% endhint %}

然后客户端插件将查看插件配置中的`Port`字段并将其记录到内存中。

接下来，客户端插件将查看`Force Bind IP`字段。如果该字段的值不是'Disabled'，它将开始在与所选IP相关的适配器上监听连接。

* 对于`0.0.0.0`，它将监听来自任何地方的连接。如果`Force Bind IP`设置为'Disabled'，也会出现此行为。
* 对于特定IP，如`192.168.x.x`或`26.x.x.x`，它将仅监听来自该网络适配器的连接。这通常仅在使用VPN网络适配器时使用，否则首选`0.0.0.0`。

一旦所有值都已记录到内存中，客户端插件将尝试建立监听传入连接的服务。然后插件将向fika-server模组发送可用IP:端口组合列表，以便后端服务器可以将该信息转发给任何可能想要连接的其他客户端。列表将看起来像：

* `IP_1:Port` - 这通常是在`Force IP`中的值或您的公共/WAN IP + 插件配置中的端口
* `IP_2:Port` - 这是您的局域网IP + 插件配置中的端口

{% hint style="danger" %}
Fika.Core -> Network中的设置都不会影响**加入**突袭的客户端。它们只影响突袭主机。
{% endhint %}

### 客户端如何连接到宣传的突袭

当客户端导航到突袭屏幕并在可用突袭列表中的特定突袭上点击`JOIN`按钮时，后端服务器将上述讨论的信息转发给加入客户端的Fika插件，其中包含一系列IP:端口组合，它们将尝试连接。

连接客户端将按顺序尝试连接到`IP_1:Port`和`IP_2:Port`。如果两者都不起作用，将显示错误，建议确认所有端口都已打开且突袭主机允许传入连接。

{% hint style="info" %}
注意：在游戏客户端之间建立的是**直接连接**，而不是通过后端服务器路由的连接。如果直接连接路径被阻塞或不可用，即使两个客户端都能连接到后端服务器，连接也会失败。
{% endhint %}

### 进一步故障排除

如果您或朋友在尝试加入突袭时仍然遇到错误，您应该打开遇到错误的人的Player.log，查看发送给他们的IP。Player.log可以在以下位置找到，下面的图片显示了您正在查找的日志行示例。

```
C:\Users\YOURUSERNAME\AppData\LocalLow\Battlestate Games\EscapeFromTarkov\
```

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

列出的两个IP将是[Fika网络工作流程](advanced-how-fika-establishes-raid-connections.md#fika-network-workflow)部分中的`IP_1`和`IP_2`。

## 为什么这很重要

这与大多数'专用服务器'游戏托管场景的运作方式有很大不同。如果您曾经托管过其他游戏服务器——如Minecraft、Valheim、ARK、Palworld或7D2D——您可能会惊讶地发现Fika托管完全不同，因此您过去从为朋友圈托管中获得的几乎所有知识都不太有用。

在大多数其他游戏中，'专用服务器'应用程序负责处理所有网络同步。您和朋友都连接到服务器，你们两个都不需要能够接受传入连接即可一起玩。对于SPT+Fika，情况并非如此：您都可以连接到后端服务器，与商人互动并互相发送物品，但除非其中一人能够接受**到您的EscapeFromTarkov.exe游戏客户端**的传入连接，否则您将无法一起玩突袭。这是因为突袭是由您游戏客户端上的Fika插件托管的，而不是后端服务器。

如果托管突袭的PC只能通过代理或隧道访问，您可能需要利用上述信息来想出要输入到`Force IP`中的值，以便其他客户端可以连接到宣传的突袭。这可能很简单，就像创建一个动态DNS条目，在您的网络内部和外部解析不同——例如，`fika.yourdomain.com`对于您网络内部的用户解析为局域网IP（由您的路由器本地解析），但对于您网络外部的用户则通过您的域名注册商的A记录解析为您的公共IP。

{% hint style="success" %}
如果以上任何信息仍然无法帮助您弄清楚可以为Force IP或Force Bind IP输入什么值，请加入[Fika Discord](https://discord.gg/project-fika)并解释您的网络设置、您正在尝试做什么、您已经尝试了什么以及什么不起作用。
{% endhint %}
