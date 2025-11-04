---
description: 使用VPN客户端托管Fika服务器的逐步过程。
---

# 使用VPN托管

虚拟专用网络（VPN）使您能够通过公共集中服务器加入同一网络。您可以使用免费的VPN服务，如[Radmin](https://www.radmin-vpn.com/)或设置您自己的VPN。仅在无法使用端口转发时才建议使用此方法。

本指南将使用Radmin作为VPN客户端。如果您的网络允许，它能够建立直接连接，提供最佳可能的性能。

{% hint style="warning" %}
免费VPN服务已知会导致性能或连接问题，因此使用风险自负。官方支持的Fika连接方式是使用端口转发。我们不会为VPN服务引起的问题提供支持。

像**BitDefender**这样的自定义防火墙也可能在游戏时阻止您的连接。请确保允许连接或在游戏时临时禁用它！

如果您使用另一个VPN服务，即使已禁用，您也可能会遇到问题。如果您有问题，请考虑卸载任何其他虚拟网络适配器。
{% endhint %}

## 安装Radmin VPN客户端

* 导航到[Radmin网站](https://www.radmin-vpn.com/)并下载Radmin VPN客户端。
* 运行安装程序并继续安装步骤。
* 重新启动计算机。这对于确保虚拟网络适配器正确安装很重要。**不要跳过此步骤！**
* 打开Radmin VPN客户端（从任务栏或从开始菜单）。
* 点击`创建网络`。

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* 输入网络名称（可以是任何内容 - 确保记住它。您需要与朋友分享）。
* 输入密码。
* 点击`创建`。

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

* 记下您的`VPN IP`，该IP显示在Radmin中您的计算机名称下方。在以下步骤中它将被称为`your_vpn_ip`。

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

* 转到`系统`->`防火墙例外`并点击`允许所有应用程序`。

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## 测试连接

* 请您的朋友[在此处](../joining-a-fika-server/join-using-a-vpn.md)遵循步骤。
* 在Radmin中右键点击他们的名称并点击`Ping`。

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

* Ping成功时关闭命令提示符。

{% hint style="warning" %}
如果ping失败，则意味着VPN连接工作不正常。每个人都应尝试重新启动PC并确保每个人都加入了Radmin中的同一网络。

像`BitDefender`这样的自定义防火墙可以阻止VPN通信 - 尝试关闭它。
{% endhint %}

## 确保直接连接

为了获得最佳性能，确保您通过Radmin直接与朋友通信是很重要的。

* 在Radmin中右键点击您朋友的名称并点击`属性`。

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

* 验证通道类型为`TCP/out`。这意味着您与此对等方有直接连接。

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
如果您看到`TCP/relay`，则通信通过Radmin的服务器中继。性能将严重下降。尝试禁用系统中的任何防火墙和/或防病毒软件，并在Radmin中重新连接到网络。
{% endhint %}

## 在Fika中配置您的`VPN IP`

* 至少启动一次`SPT.Server`以生成配置文件，然后关闭它。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FlZfa6hVfcUTBztlqMtZ7_2Fhttps___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzs.png" alt=""><figcaption></figcaption></figure>

* 导航到`user\mods\fika-server\assets\configs`。
* 使用您首选的文本编辑器打开`fika.jsonc`（推荐使用Notepad++）。

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

* 找到`server`部分。
* 将`ip`更改为`your_vpn_ip`。确保在引号内写入。
* 将`backendIp`更改为`your_vpn_ip`。确保在引号内写入。

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

* 保存文件并关闭它。
* 启动`SPT.Launcher`

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2F89xf4fwAOWUZlYNbpj1u_2Fimage (1).png" alt=""><figcaption></figcaption></figure>

* 点击`设置`按钮。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FqwHM3gxlwjEsrugHTtc0_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* 选中`Developer Mode`框。
* 在URL部分输入您的VPN地址。不要省略`https://`，也不要添加结尾斜杠。URL框应该看起来像这样：`https://20.21.22.23:6969`。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FRJRDafOFXrz8sQBMXNfo_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* 按右角的箭头。
* 您现在应该能够创建您的配置文件并登录到服务器。
* 启动游戏。

<figure><img src="../.gitbook/assets/https___files.gitbook.com_v0_b_gitbook-x-prod.appspot.com_o_spaces_2FKIBpsnthxy8OSpsWzsDI_2Fuploads_2FVhkOgEbLlzyx9kazRxLl_2Fimage.avif" alt=""><figcaption></figcaption></figure>

* 在游戏中按`F12`以调出配置管理器。
* 在配置管理器的`Fika.Core`部分找到`Force IP`和`Force Bind IP`。
* 将Force IP和Force Bind IP都设置为`your_vpn_ip`。

<figure><img src="../.gitbook/assets/forceip.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
注意：愿意托管突袭的玩家还需要在各自的Fika配置中设置`Force IP`和`Force Bind IP`。
{% endhint %}

## 托管突袭

[点击此处](../playing-fika.md#hosting-a-raid)了解如何托管突袭。

[点击此处](../fika-configuration/)了解更多关于其他Fika配置的信息。
