---
description: 了解Fika的功能、规格和限制。
icon: circle-info
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

# 一般信息

## 什么是Fika？

Fika是[SPT](https://sp-tarkov.com/)的一个合作多人游戏模组。Fika添加了一个大厅界面，让您可以加入其他玩家的突袭行动，并提供游戏内网络功能，以及额外的功能，但默认情况下不会改变标准的《逃离塔科夫》体验。

总结来说：

* SPT是后端服务器，允许您在不使用BSG服务器的情况下开始游戏——它提供玩家档案、库存、跳蚤市场以及许多其他《逃离塔科夫》功能。
* Fika是添加合作多人游戏功能的模组组件，允许玩家托管或加入一次突袭行动以便一起游戏。

## 规格

* Fika是[BepInEx插件](https://github.com/project-fika/Fika-Plugin)和[SPT服务器模组](https://github.com/project-fika/Fika-Server)的组合。
* Fika使用SPT作为后端服务器来连接玩家。
* Fika使用客户端<->服务器UDP网络模型进行游戏。虽然Fika仍在开发中，但普遍共识是网络性能比《逃离塔科夫》实况更好（前提是主机具有适当的网络功能）。

## 主要功能

* 托管您自己的服务器或加入本地/外部服务器。
* 创建您自己的突袭行动供其他玩家加入（或单人游戏）。
* 加入别人的突袭行动。
* 一起对抗机器人，分享物品，在同一次突袭中一起完成任务。
* 保留角色、任务、库存和藏身处进展。
* 使用来自[SPT](https://forge.sp-tarkov.com/)的客户端/服务器模组（某些模组不兼容-请参见[限制](General-information.md#limitations)）。

## 其他功能

* 物品发送
  * 在库存中右键点击物品发送到另一个账户
  * 可在[服务器](fika-configuration/server.md)配置中自定义
* 自由摄像机（默认为`F9`键）
  * 在自由摄像机模式下，按`T`键可以传送到摄像机位置
  * 通过`左键/右键`点击可以跳转到另一个玩家
  * 跳转时按住`SPACE`可以锁定到他们的头部
  * 跳转时按住`CTRL`可以锁定到他们的背部第三人称视角
  * 按`HOME`键可以临时切换自由摄像机控制
* 游戏内聊天系统
* 突袭内语音通信
* 在线玩家列表
* 为主机提供动态AI，当附近没有玩家时禁用AI
* 每个地图的自定义AI限制
* 剔除系统以提高性能
* 自定义通知（队友死亡，Boss被玩家击杀等）
* 标记系统，为您的队友在游戏区域中进行标记
* 队友生命值条
* 突袭中的任务进度共享
* 可选/高级无头客户端以分载AI并获得性能提升（更多信息[在此](advanced-features/headless-client/remote-headless-client.md)）
* 网络插值以获得更流畅的游戏体验
* UPnP和NAT穿透

## 限制

* 您必须拥有合法的《逃离塔科夫》副本才能玩Fika。如果您尝试不拥有副本而使用Fika，您将被封禁。
* 没有防止滥用或作弊的保护措施。Fika设计为与可信任的朋友一起游戏。**强烈不建议托管公共服务器**。我们永远不会支持公共服务器。
* Fika不包含任何PvP机制。支持PvP不是此项目的目标。
* Fika不提供全球匹配服务。只有连接到同一服务器的玩家才能创建或加入突袭行动。
* 某些SPT模组与Fika不兼容。SPT模组通常为标准SPT安装设计，不包含多人游戏功能。如果模组作者选择，他们有责任让他们的模组与Fika兼容。
