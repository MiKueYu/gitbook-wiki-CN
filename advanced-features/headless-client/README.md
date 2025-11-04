---
description: >-
  关于Fika无头客户端功能的一般信息，用于创建专用的SPT突袭主机实例。
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

# 无头客户端

无头客户端插件是Fika的独占功能，允许您在单独的逃离塔科夫实例上托管突袭。您能够卸载AI计算和其他资源密集型任务以提高游戏性能。当在与您玩游戏的**单独PC**上托管突袭时，FPS提升通常在25%到50%之间，具体取决于您的计算机规格和游戏中机器人的数量。

{% hint style="warning" %}
请注意，这需要一些技术知识。如果您完全没有经验，您将会有困难。
{% endhint %}

### 规格

* 无头客户端基本上是另一个SPT+Fika客户端实例，它将自动托管突袭。所有玩家都成为客户端（包括点击`托管突袭`的玩家）。
* 禁用了图形渲染以使无头客户端尽可能轻量级。但是，无头客户端**不是**真正的无头服务器。它仍然需要所有游戏文件和相当大量的RAM才能工作（特别是对于较大的地图，如街道或灯塔）。
* 强烈建议在单独的物理机器上运行无头客户端。无头客户端将无法在VPS上工作。如果您真的想使用付费主机，请租用专用服务器。
* 运行无头客户端**不需要**显卡，但可能有助于配置模组。

{% hint style="danger" %}
使用无头客户端可能会导致某些模组完全无法工作或变得更难正确配置。因此，在添加任何模组**之前**设置无头客户端要容易得多，以减少问题。

如果您在无头客户端设置过程中遇到问题，请考虑首先使用完全新鲜的SPT+Fika安装，没有任何其他模组重新开始。
{% endhint %}

更多信息、指南和常见修复方法可以在[无头客户端常见问题和常见问题](../../faqandguides/headless-client-faq-and-common-issues/)部分找到。

### 选择无头客户端实现

{% tabs %}
{% tab title="在单独PC上的无头客户端" %}
{% hint style="success" %}
这是无头客户端功能的预期用例，并提供最大和最一致的性能提升。
{% endhint %}

SPT.Server和无头客户端都将在独立于您的游戏PC的单独PC上运行。这意味着您可以根据需要以任何方式使用您的游戏PC，包括重新启动，而不会影响任何其他玩家。

<h4 align="center"><a href="remote-headless-client.md" class="button primary" data-icon="network-wired">远程无头客户端说明</a></h4>
{% endtab %}

{% tab title="本地无头/同一PC上的无头" %}
{% hint style="danger" %}
**这不是无头客户端功能的预期用例！请阅读下一页顶部的警告。支持有限。**
{% endhint %}

如果您的PC可以同时处理两个EFT客户端，通过在您玩SPT的同一PC上运行无头客户端，您_可能_会看到卡顿减少或性能提升。任何性能提升完全取决于您的硬件，不保证。

#### <mark style="color:$warning;">一些用户看到性能下降。自行承担风险继续。</mark>

<h4 align="center"><a href="local-headless-client.md" class="button primary" data-icon="computer">本地无头客户端说明</a></h4>
{% endtab %}
{% endtabs %}
