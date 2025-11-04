---
description: Fika安装的逐步过程。
icon: desktop-arrow-down
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

# 安装Fika

## 安装Fika之前

**始终**记住Fika是一个[SPT](https://sp-tarkov.com/#download)模组。在尝试安装Fika之前，您**必须**拥有正常工作的SPT。

这意味着您必须能够正常的启动SPT，并且在安装Fika之前不应运行任何模组。请确保满足此条件后再继续后续步骤。

{% hint style="info" %}
如果您不确定如何安装SPT，请按照[此处](https://forge.sp-tarkov.com/installer)的说明操作，并在完成后回到这里。再次提醒，在继续之前，请确保您的SPT能正常工作。
{% endhint %}

我们建议阅读[一般信息](../General-information.md)部分，以便更好地了解Fika的工作原理。

## 先决条件

* 您必须拥有一个最新且正常工作的[SPT](https://forge.sp-tarkov.com/installer)，**且未安装任何模组**。
  * 您可以在之后安装SPT模组，但首先让Fika在无模组的情况下正常工作是很重要的。
* Fika不支持SPT的最新开发版本。
* 定位您的SPT安装文件夹。在以下步骤中这将被称为`SPT文件夹`。

## 硬件要求

* **CPU**: i7 8700k / Ryzen 5 3600X
* **GPU**: GTX 2070 / RX 5700 XT
* **内存**: 32 GB RAM
* **存储**: 必须使用SSD，不支持在HDD上安装

在Fika（以及SPT）中最大的提升将是获得更强的CPU和RAM。AMD X3D系列将提供最佳性能，因为缓存速度更快。

## 安装

{% stepper %}
{% step %}
### 使用BSG启动器安装逃离塔科夫

在安装SPT和Fika之前，必须在计算机上安装逃离塔科夫。这是为了确保您拥有游戏。&#x20;

**如果您跳过此步骤，Fika将无法工作！**
{% endstep %}

{% step %}
### 安装[SPT](https://forge.sp-tarkov.com/installer)

在安装Fika之前**必须**进行全新的SPT安装。**暂时不要安装模组！**
{% endstep %}

{% step %}
### 下载[Fika-Installer](https://github.com/project-fika/Fika-Installer/releases/latest)
{% endstep %}

{% step %}
### 将`Fika-Installer.exe`复制到SPT安装文件夹的根目录

不要复制到`SPT`文件夹内！

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F5yu7c0P4PT4gSQwcgOw5_2Fimage.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`Fika-Installer.exe`

如果出现管理员权限提示，这是正常的。Fika-Installer需要管理员权限来设置防火墙规则。
{% endstep %}

{% step %}
### 选择`Install Fika`

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 安装完成后关闭`Fika-Installer`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FD9VHauheMEVLMpsMRod5_2Fimage.avif" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Server`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FLRc3xTCQ6XWf6cP3JDMG_2Fimage.png" alt=""><figcaption></figcaption></figure>

您应该看到`Mod: server version: x.x.x (targets SPT: 4.x.x) by: Fika loaded`。

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 启动`SPT.Launcher`

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 创建或登录您的账户，然后启动游戏

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 验证Fika成功加载

主菜单的左下角应显示`FIKA x.x.x | SPT x.x.x`。您还应该在主菜单右侧看到`在线玩家`小部件。

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### 退出游戏

退出游戏并继续下一步。
{% endstep %}
{% endstepper %}

***

## 设置Fika

为了托管或加入Fika服务器，您必须遵循必要的步骤。

如果您要托管Fika服务器，[点击这里](../hosting-a-fika-server/)。

如果您要加入Fika服务器，[点击这里](../joining-a-fika-server/)。
