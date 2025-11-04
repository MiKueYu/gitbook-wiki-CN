---
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

# 设置必需/可选模组

在`fika.jsonc`中设置必需/可选模组部分可能会令人沮丧。我应该在那里放什么？我如何找到模组GUID？必需和可选之间有什么区别。让我们尝试揭开这个强大功能的神秘面纱并使其得到更广泛使用。首先，让我们从一个简单的Powershell脚本开始，它将获取您当前加载的所有插件GUID。&#x20;

在执行此脚本之前，请确保您已安装了**您想要获取名称的所有插件**并启动您的SPT客户端。这将用当前安装的插件信息刷新您的Player.log，我们将使用下面的脚本提取。直接将下面的脚本复制粘贴到Powershell命令窗口中并执行它。它将打印出正确格式化的模组GUID字符串，可直接粘贴到`fika.jsonc`中。

```powershell
$LocalLow = [System.Environment]::GetFolderPath("LocalApplicationData").Replace("Local", "LocalLow")
$LogFile = Join-Path $LocalLow "\Battlestate Games\EscapeFromTarkov\Player.log"

$ModGuids = @()

Get-Content $LogFile | ForEach-Object {
    if ($_ -match '^\[Info\s+:FikaModHandler\].*?GUID \[([^\]]+)\]') {
        $ModGuids += '"' + $matches[1] + '"'
    }
}

$CSVOutput = $ModGuids -join ', '

Write-Host $CSVOutput
```

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

如果您希望加入服务器的每个人都被要求拥有您加载的相同插件，请将输出复制粘贴到`fika.jsonc` -> `"mods": { "required": [ <HERE> ]`中。如果不想强制执行某些插件但仍允许它们，则可以将一些GUID移到`"optional": [ ]`部分。任何加载了不在这些列表中的插件或缺少必需列表中插件的人将收到带有大的`EXIT`按钮的错误消息：

> 您的客户端不符合服务器要求，请检查日志以获取更多详细信息

这样您可以防止朋友安装可能带来不公平优势的模组，或者至少确保每个人都有相同的模组，从而避免问题。

