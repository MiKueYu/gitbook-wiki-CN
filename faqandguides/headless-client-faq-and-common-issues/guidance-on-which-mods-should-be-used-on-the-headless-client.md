---
description: 由Shynd创建
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

# 关于应在无头客户端上使用哪些模组的指导

## 注意：无头客户端是一个_客户端_ — 客户端只加载`BepInEx/`中的内容。任何在`SPT/user/mods/`中的模组仅由后端服务器SPT.Server.exe加载。

稍微扩展一下我关于无头客户端**需要**的插件与无头客户端不需要的插件之间的区别的含义：

* <mark style="color:$warning;">它是否仅在仓库或藏身处时才有效果？如果是，则它可能</mark> <mark style="color:$warning;"></mark>_<mark style="color:$warning;">不</mark>_ <mark style="color:$warning;"></mark><mark style="color:$warning;">需要用于无头客户端。</mark>
  * 这类似于QuickSell这样的东西。它不需要在无头客户端上安装，因为它只影响仓库行为。
  * 此类别的插件可能可以留在无头客户端上安装，但它们可能会引起问题。它们不太可能_解决_任何问题。
* <mark style="color:$warning;">它是否只改变信息或图形的显示方式，而不改变该信息？如果是，则它可能</mark> <mark style="color:$warning;"></mark>_<mark style="color:$warning;">不</mark>_ <mark style="color:$warning;"></mark><mark style="color:$warning;">需要用于无头客户端。</mark>
  * 这将包括MoreCheckmarks、AmandsGraphics、DynamicMaps、ItemSellPrice等。这些插件获取游戏客户端中已有的信息并以不同方式显示。它们不会添加或更改任何行为。
  * 此类别的插件也可能可以留在无头客户端上安装，它们也可能引起问题。它们不太可能_解决_任何问题。
  * 请记住，无头客户端会自动导航菜单以开始和结束突袭。任何更改或修补菜单的内容都可能导致问题。
* <mark style="color:$warning;">它是否以某种方式改变突袭内行为？如果是，则它可能是必需的。</mark>
  * 这将是类似SAIN的东西，影响AI行为，或机器人生成模组，或UIFixes（更改_库存行为方式_），或任何您认为_**可能**_对突袭内行为有影响的其他内容。
  * 此类别的插件有时难以识别。像UIFixes这样的内容可能并不明显地_改变_库存行为，用户可能不会意识到突袭主机对库存操作具有权威性。
  * 一些似乎属于此类别的插件只是显示触发原版行为的其他方式，因此不需要在无头客户端上，但通常安装也不会有害。例如，ItemContextMenuExtended使您可以右键点击手电筒以切换其开关，但它们不会_改变_该行为，只是以新方式使其可访问，因此_不需要_在无头客户端上。

有一些插件，如SearchOpenContainers，很难判断它们需要在哪里或是否会引起问题。人们可能合理地假设搜索一个开放的容器是在改变行为，所以需要为无头客户端安装；人们也可能合理地假设搜索一个开放的容器完全是客户端的事情，由于无头客户端角色永远不会搜索容器，所以这不是必需的。感觉模糊的插件应该进行测试，以确保它们不会引起任何问题。&#x20;

归根结底，将不会改善无头客户端体验的插件安装在无头客户端上通常没有_好处_，但通常也不会有问题。有时更多插件确实会增加更多处理开销，从而降低突袭内FPS。如果这对您不重要，请安装所有内容，只删除引起问题的插件！如果这很重要，请选择并自行测试。&#x20;

我个人将上述逻辑作为测试的起点。我会移除任何我非常确定不需要的插件，并保留任何我不确定的插件，然后运行突袭并特别测试插件行为。我查看日志中的错误。如果一切正常，我就继续。到目前为止，这对我很有帮助。

以下是无头客户端与Fika实例的模组设置说明：

**无头客户端**

<figure><img src="../../.gitbook/assets/image (22) (1).png" alt=""><figcaption></figcaption></figure>

**Fika实例**

<figure><img src="../../.gitbook/assets/image (23) (1).png" alt=""><figcaption></figcaption></figure>
