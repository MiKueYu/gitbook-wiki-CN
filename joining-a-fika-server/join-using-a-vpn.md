---
description: 使用VPN客户端加入Fika服务器的逐步过程。
---

# 使用VPN加入

本指南将使用Radmin作为VPN客户端。如果您的网络允许，它能够建立直接连接，提供最佳可能的性能。

{% hint style="warning" %}
免费VPN服务已知会导致性能或连接问题，因此使用风险自负。官方支持的玩Fika的方式是使用端口转发。我们不会为VPN服务引起的问题提供支持。

像**BitDefender**这样的自定义防火墙也可能在游戏时阻止您的连接。请确保允许连接或在游戏时临时禁用它！

如果您使用另一个VPN服务，即使已禁用，您也可能会遇到问题。如果您有问题，请考虑卸载任何其他虚拟网络适配器。
{% endhint %}

## 安装Radmin VPN客户端

* 导航到[Radmin网站](https://www.radmin-vpn.com/)并下载Radmin VPN客户端。
* 运行安装程序并继续安装步骤。
* 重新启动计算机。这对于确保虚拟网络适配器正确安装很重要。**不要跳过此步骤！**
* 从任务栏或从开始菜单打开Radmin VPN客户端。
* 点击`加入网络`。

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

* 输入主机使用的网络名称和密码。

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

* 您现在应该能够看到连接对等方列表，包括主机。

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* 转到`系统`->`防火墙例外`并点击`允许所有应用程序`。

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## 测试连接

* 在Radmin中右键点击主机名称并点击`Ping`。

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

* Ping成功时关闭命令提示符。

{% hint style="warning" %}
如果ping失败，则意味着VPN工作不正常。每个人都应尝试重新启动PC并确保每个人都加入了Radmin中的同一网络。

像`BitDefender`这样的自定义防火墙可以阻止VPN通信 - 尝试关闭它。
{% endhint %}

## 确保直接连接

为了获得最佳性能，确保您通过Radmin直接与朋友通信是很重要的。

* 在Radmin中右键点击主机名称并点击`属性`。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FzCgqmu3LxK8ZdsRiLKjm_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* 验证通道类型为`TCP/out`。这意味着您与此对等方有直接连接。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FcYerBNYv2Eeg8Sz1TYL4_2Fimage.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
如果您看到`TCP/relay`，则通信通过Radmin的服务器中继。性能将严重下降。尝试禁用系统中的任何防火墙和/或防病毒软件，并在Radmin中重新连接到网络。
{% endhint %}

## 配置SPT启动器

* 启动`SPT.Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage.png" alt=""><figcaption></figcaption></figure>

* 点击`设置`按钮。

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

* 选中`Developer Mode`框。

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* 在URL部分输入主机的VPN地址。**不要**省略`https://`，不要忘记添加端口`:6969`，不要在末尾添加斜杠。URL框应该看起来像这样：`https://20.21.22.23:6969`。

<figure><img src="../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* 按右角的箭头。

<figure><img src="../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* 您现在应该能够创建您的配置文件并登录到服务器。
* 启动游戏。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage (1).avif" alt=""><figcaption></figcaption></figure>

## 加入突袭

* [点击此处](../playing-fika.md#joining-a-raid)了解如何加入突袭。
