---
description: >-
  设置无头客户端以从您玩SPT的同一PC上托管您的突袭的说明。支持有限。
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

# 本地无头客户端

{% hint style="info" %}
请确保您首先阅读了通用[无头客户端页面](./)上的所有内容。
{% endhint %}

{% hint style="danger" %}
## 支持有限

请注意，如果您选择在与您玩SPT的同一PC上运行无头客户端，**支持有限**。这不是官方支持的配置，可能会导致：

* 性能下降
* 崩溃次数增加
* 页面文件使用量显著增加
* 一般不稳定性，可能对整个PC或操作系统产生不良影响

如果您遇到任何与性能或稳定性相关的问题，请**停止使用**在与您玩游戏的同一PC上的无头客户端。

如果您遇到性能相关问题，请不要寻求支持。
{% endhint %}

***

## 推荐硬件要求

* 您**必须**至少有64 GB的RAM。
  * 少于这个数量在有限情况下**可能工作**，但可能会导致问题。
* 在所有核心都加载时保持高提升时钟（4Ghz+）的CPU。
* 100GB在非常快的SSD上的可用空间，最好是NVMe。

***

## 注意事项

* Windows虚拟分页设置**必须是默认的**，在您的`C:\`驱动器上有充足的可用空间。
  * 如果您更改了Windows虚拟内存选项，请将所有设置返回到默认配置。`自动管理所有驱动器的分页文件大小`复选框应该被选中。
* 下面的安装过程假设您完全按照[安装Fika](../../installing-fika/)过程进行。偏离该过程可能会导致问题。
* 如果您以前安装过模组，特别是客户端插件，<mark style="color:$warning;">请在继续之前删除它们</mark>。此过程假设安装的唯一模组是Fika。
  * 在安装模组的情况下继续此指南是_可能的_，但您可能会遇到问题。如果您在此过程中遇到任何问题，请重新开始，但这次首先删除所有模组。
* 角色进度和服务器设置将基本不受影响。
  * 您现有服务器设置的唯一变化是在[fika.jsonc](../../fika-configuration/server.md)中的一点小变化，以生成必要的无头配置文件。

<details>

<summary>这怎么可能提高性能？</summary>

可以理解，很难看出在同一台PC上运行两个SPT客户端如何能提高性能。为什么在相同硬件上运行游戏两次会比只运行一次游戏更好？

原因都归结为基础游戏客户端如何处理突袭内动作。

基本上，AI/机器人采取的任何动作都必须在CPU将数据推送到您的显卡以渲染下一帧之前在同一CPU核心/线程上计算。多线程非常有限，因此托管所有AI计算的游戏客户端有更多工作要做，每个帧渲染得更慢。

通过使用Fika无头客户端插件将AI计算卸载到单独的游戏客户端，您正在释放游戏客户端的主逻辑线程，使其在渲染每个帧之前做更少的工作。这有效地将突袭行为多线程化，您的游戏客户端负责所有图形渲染，第二个无头游戏客户端负责大部分突袭内计算。

<sub>以上所有内容仅为说明目的而简化。</sub>

</details>

***

## 安装

{% stepper %}
{% step %}
### 可选：[创建新的SPT+Fika安装](../../installing-fika/)

您可以使用现有的SPT+Fika安装遵循以下步骤，但您可能会遇到问题，特别是如果您已经安装了模组。创建新的SPT+Fika安装如果您发现这在您的PC上不工作，则更容易撤销，它也完全不会触及您现有的安装。

从头到尾遵循整个[安装Fika](../../installing-fika/)部分，包括创建角色并到达您的仓库。

<mark style="color:$warning;">跳过此步骤风险自负。</mark>
{% endstep %}

{% step %}
### 可选：在[fika.jsonc](../../fika-configuration/server.md)中设置URL

{% hint style="info" %}
如果您仅为自己使用或正在使用端口转发，则不需要此步骤。
{% endhint %}

如果您使用像Radmin或ZeroTier这样的VPN，您需要：

1. 导航到`[现有SPT安装]\SPT\user\mods\fika-server\assets\configs\`
   1. 如果`fika.jsonc`不存在，请从您现有的SPT安装中运行一次SPT.Server.exe，然后关闭它。
2. 在文本编辑器中打开`fika.jsonc`。
3. 向下滚动到`scripts -> forceIp`设置，并将其更改为在按照[托管说明](../../hosting-a-fika-server/)时设置的URL。
4. 保存文件并关闭文本编辑器。

<div align="left"><figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### 创建无头客户端SPT安装文件夹

在您的PC上的某个位置创建一个新的空文件夹，您希望将无头客户端安装在该位置。从您的原始SPT安装中复制并粘贴`Fika-Installer.exe`到这个新空文件夹中。

<div align="center"><figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### 使用`Fika-Installer`创建无头SPT安装副本

运行`Fika-Installer.exe`并选择`高级选项`，然后选择`安装Fika无头客户端`

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 选择现有的SPT+Fika安装文件夹

按`ENTER`，然后选择您现有的SPT+Fika安装文件夹。

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 创建无头配置文件

选择`创建新的无头配置文件`

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 选择安装方法

根据您的喜好选择`HardCopy`或`Symlink`。

* `HardCopy`将创建现有SPT+Fika安装的1:1副本，这将占用全部50+ GB的存储空间。这是完全避免问题或混淆的方法。
* `Symlink`将硬复制现有安装的部分到新的无头客户端文件夹，但将创建EFT数据文件的大部分符号链接。这节省了大量存储空间，但如果您删除原始文件或将来需要重新安装SPT，可能会创建问题。

#### 如果您没有偏好，请选择`Symlink`以节省存储空间。

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 验证完成

<kbd>Fika-Installer</kbd>应该创建必要的无头配置文件，将文件复制到新的无头客户端安装文件夹，然后安装最新版本的Fika。如果此步骤没有成功完成，请从头重新开始。

完成后，您现在可以关闭`Fika-Installer`。

<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 从现有的SPT+Fika文件夹启动`SPT.Server`

打开一个新的文件资源管理器窗口，导航到您现有的SPT+Fika文件夹并启动`SPT.Server`

<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 等待控制台中出现`Server has started, happy playing`消息

<figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Launcher`和您的游戏客户端

从相同的现有SPT+Fika安装文件夹，运行`SPT.Launcher`。

<figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

如有必要创建角色并点击`开始游戏`按钮。

<figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 验证您的游戏客户端加载并且Fika已安装

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`Fika无头管理器`

从您的无头客户端安装文件夹，运行`FikaHeadlessManager.exe`。`Fika无头管理器`将启动您的无头客户端。

<figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 等待无头客户端加载

运行脚本后将出现两个控制台窗口：`Fika无头管理器`和无头客户端控制台。**不要关闭它们**。等待无头客户端加载。加载完成后控制台中的活动将停止。

<figure><img src="../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 使用无头客户端托管突袭

像平常一样导航游戏内菜单以到达`Raids`菜单并点击`Host Raid`。

<figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption></figcaption></figure>

勾选`Use Headless Host`框并按`Start`。这将请求无头客户端在选定位置开始突袭。等待无头客户端加载突袭。

<figure><img src="../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 当无头客户端准备好时开始突袭

当您看到此屏幕时，您的朋友可以加入无头客户端的突袭。当每个人都加入后，按`Start Raid`。

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
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
* 如果您的无头客户端加载失败，如果可以的话，在`Fika无头管理器`启动期间按`G`键以图形模式启动。如果无法以图形模式启动，请在SPT日志文件夹中的`<timestamp> errors.log`中查找提示。这通常是由有故障或无效插件引起的，有时也是由于缺少服务器上某个模组所需的插件。
* 在[常见问题和指南](../../faqandguides/)和[无头客户端常见问题和常见问题](../../faqandguides/headless-client-faq-and-common-issues/)中查看其他常见问题
