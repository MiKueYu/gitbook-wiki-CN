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

# 为无头客户端配置模组

## 一般说明

* 如果安装无头客户端的PC有GPU，您可以在启动时由FikaHeadlessManager提示时按G键以图形模式打开无头客户端。在图形模式下，您可以访问F12（或SAIN的F6）来配置您的模组。
* 如果安装无头客户端的PC**没有**GPU，请关闭FikaHeadlessManager和无头客户端。在您将要玩游戏的SPT实例上安装您希望配置的插件（**不是无头客户端**），以您想要的方式配置选项，然后将必要的.cfg文件从`<SPT安装>/BepInEx/config/`复制到无头客户端安装的`<无头SPT>/BepInEx/config/`文件夹中。

## SAIN

* SAIN设置存储在`BepInEx/plugins/SAIN/Presets/`文件夹中。我建议使用您的主游戏将SAIN选项配置为您希望在无头客户端上使用的方式，然后将整个`BepInEx/plugins/SAIN/`文件夹复制到专用客户端，在提示时覆盖所有文件。

## Donuts

* Donuts设置存储在`BepInEx/plugins/dvize.Donuts/Config`文件夹中。与上面的SAIN相同，我建议使用主游戏的GUI配置Donuts设置，然后将整个`BepInEx/plugins/dvize.Donuts/`文件夹复制到无头客户端。

***
