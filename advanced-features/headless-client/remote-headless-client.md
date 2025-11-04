---
description: >-
  设置无头客户端以从单独计算机托管您的突袭以获得最大性能提升的说明。这是官方支持的无头客户端配置。
hidden: true
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: true
---

# 远程无头客户端

{% hint style="info" %}
请确保您首先阅读了通用[无头客户端页面](./)上的所有内容。
{% endhint %}

## 推荐硬件要求

* 用于运行无头客户端的专用机器。
  * 大多数虚拟专用服务器（VPS）将**无法**工作，因为它们不提供无头客户端所需的性能。
* 现代CPU，至少4核心@ 4GHz+。
* 32 GB RAM（16 GB RAM _可能_能工作，但由于虚拟分页会导致性能降低）。
* 50 GB磁盘空间，带SSD/NVME驱动器。**不支持HDD。**

## 注意事项

* 下面的安装过程将指导您设置在同一台机器上安装SPT服务器和无头客户端。可以将SPT服务器和无头客户端分开，但没有性能优势，而且步骤更复杂。因此，本指南将不涵盖此设置。
* Linux不受本文支持和涵盖。请访问我们[Discord](https://discord.gg/project-fika)中的专用Linux频道以获得帮助。

***

## 安装

{% stepper %}
{% step %}
### 使用BSG启动器安装逃离塔科夫

当您计划运行无头客户端的机器/服务器上必须安装逃离塔科夫。这是为了确保您拥有游戏。&#x20;

**如果您跳过此步骤，Fika将无法工作！**
{% endstep %}

{% step %}
### 安装[SPT](https://hub.sp-tarkov.com/files/file/672-spt-installer/)

如果您的SPT服务器当前位于不同的机器上，请将其复制到您计划安装无头客户端的计算机上。它必须包含完整游戏。如果由于大小而无法复制，请使用[SPT安装程序](https://hub.sp-tarkov.com/files/file/672-spt-installer/)在服务器上安装SPT。

**请勿在您的官方逃离塔科夫文件夹中安装SPT！**
{% endstep %}

{% step %}
### 下载[Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)
{% endstep %}

{% step %}
### 将`Fika-Installer.exe`复制到SPT安装文件夹的根目录

不要复制到`SPT`文件夹内！

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 运行`Fika-Installer.exe`

如果您收到管理员权限提示，这是正常的。`Fika-Installer`需要管理员权限来设置防火墙规则。
{% endstep %}

{% step %}
### 选择`Install Fika`

<figure><img src="../../.gitbook/assets/image (20) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 确认安装完成

<figure><img src="../../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 为无头客户端在[fika.jsonc](../../fika-configuration/server.md)中设置URL

1. 导航到`[SPT根文件夹]\SPT\user\mods\fika-server\assets\configs\`
   1. 如果`fika.jsonc`不存在，请从您的无头安装中运行一次`SPT.Server.exe`，然后关闭它。
2. 在文本编辑器中打开`fika.jsonc`。
3. 向下滚动到`scripts -> forceIp`设置，并将其更改为在按照[托管说明](../../hosting-a-fika-server/)时设置的URL。
4. 保存文件并关闭文本编辑器。

<div align="left"><figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### 选择`Advanced options`

<figure><img src="../../.gitbook/assets/image (5) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 选择`Install Fika Headless`

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 选择`Create a new headless profile`

<figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 安装完成后关闭`Fika-Installer`

<figure><img src="../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Server.exe`

<figure><img src="../../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
### 等待控制台中出现`Server has started, happy playing`消息

<figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 使用`Fika Headless Manager`启动无头客户端

`Fika Headless Manager`将启动您的无头客户端。

<figure><img src="../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 等待无头客户端加载

运行脚本后将出现两个控制台窗口：`Fika Headless Manager`和无头客户端控制台。**不要关闭它们**。等待无头客户端加载。加载完成后控制台中的滚动将停止。

<figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Launcher`和您的游戏客户端

无头客户端现已准备好托管突袭。在您的计算机上启动Fika（`SPT.Launcher`）。&#x20;

**请勿在无头客户端服务器上启动SPT.Launcher.exe！**

<figure><img src="../../.gitbook/assets/image (15) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 使用无头客户端托管突袭

像平常一样导航游戏内菜单以到达`Raids`菜单并点击`Host Raid`。

<figure><img src="../../.gitbook/assets/image (16) (1) (1).png" alt=""><figcaption></figcaption></figure>

勾选`Use Headless Host`框并按`Start`。这将请求无头客户端在选定位置开始突袭。等待无头客户端加载突袭。

<figure><img src="../../.gitbook/assets/image (17) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 当无头客户端准备好时开始突袭

当您看到此屏幕时，您的朋友可以加入无头客户端的突袭。当每个人都加入后，按`Start Raid`。

<figure><img src="../../.gitbook/assets/image (18) (1) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 完成！
{% endstep %}
{% endstepper %}

***

## 模组

无头客户端对模组很敏感。请**不要**安装您在Fika中使用的相同模组。由于无头客户端经过大量修改，大多数模组可能会导致崩溃或使其不稳定。

**✅ 您可以安装：**

* AI模组（SAIN）
* 生成模组（MOAR, DONUTS）
* 明确提到支持无头客户端的模组（That's Lit, UIFixes等）
* 任何合理改变突袭内行为的模组，如进入自定义任务区域或与库存有关的模组（VCQL, Pack'n'Strap等）

**❌ 请勿安装：**

* RAM/VRAM清理模组（RAM Cleaner, VRAM Cleaner等）
* 性能模组（DeClutter等）
* 未列在**您可以安装**部分中的任何其他模组

***

## 故障排除

* 如果您在加入无头托管的突袭时崩溃或出现错误，请确保每个人都有最新版本的Fika。验证您拥有最新版本的[Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)并在您的常规SPT+Fika文件夹以及无头文件夹中使用它来`Update Fika`和`Advanced` -> `Update Fika Headless`。
* 如果`Use Headless Host`复选框变灰，这意味着无头客户端不可用。可能是由于在无头客户端中安装了不支持的模组、网络问题或其他因素引起的。请注意，无头客户端一次只能托管一个突袭。检查`BepInEx/LogOutput.log`中的错误，特别是关于不兼容模组的警告。
* 如果您的无头客户端加载失败，如果可以的话，在`Fika Headless Manager`启动期间按`G`键以图形模式启动。如果无法以图形模式启动，请在SPT日志文件夹中的`<timestamp> errors.log`中查找提示。这通常是由有故障或无效插件引起的，有时也是由于缺少服务器上某个模组所需的插件。
* 在[常见问题和指南](../../faqandguides/)和[无头客户端常见问题和常见问题](../../faqandguides/headless-client-faq-and-common-issues/)中查看其他常见问题
