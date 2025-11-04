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
    visible: true
  pagination:
    visible: false
  metadata:
    visible: true
---

# 无头客户端常见问题和常见问题

### :question:FikaHeadlessManager在启动时显示错误

* **错误**: <mark style="color:red;">**无法访问 \<URL> 上的 SPT.Server 请确保 SPT.Server 正在运行并可访问。**</mark>
  * FikaHeadlessManager无法验证服务器正在运行。\
    \
    检查SPT.Server是否正在运行并可通过您的SPT.Launcher访问；验证您可以像平常一样连接并启动游戏。\
    \
    在无头安装的根文件夹中，找到`HeadlessConfig.json`并在文本编辑器中打开它。验证URL是正确的，并指向无头客户端可以访问SPT.Server的位置。
* **错误:&#x20;**<mark style="color:red;">**无法访问 \<URL> 确保已安装Fika服务器模组。请查看文档中的安装过程。**</mark>
  * FikaHeadlessManager无法验证Fika在它连接的服务器上已完全安装。\
    \
    确保您已按照在运行SPT.Server的文件夹中[安装Fika](../../installing-fika/)的所有步骤。

***

### :question:我们无法连接到无头客户端托管的突袭，或者我们收到了关于确保端口已打开的错误

无头客户端需要能够在`<Headless Folder>/BepInEx/config/com.fika.core.cfg` -> `Network` -> `Port`（默认25565/udp）中配置的突袭端口上接受传入连接。

如果您正在使用端口转发，该端口需要转发到运行无头客户端的PC。如果您正在使用VPN，运行无头客户端的PC必须连接到同一VPN，并且必须在`com.fika.core.cfg`中配置`Force IP`和`Force Bind IP`。

更多信息请参见[此常见问题条目](../#if-you-are-using-headless-client)。

***

### :question:如何更改托管突袭时显示的无头客户端名称？

1. 在文本编辑器中打开[fika.jsonc](../../fika-configuration/server.md)。
2. 找到`headless` -> `profiles` -> `aliases`部分。
3.  为每个无头客户端添加一行，格式为`"ID": "Alias"`

    1. `ID`是您希望更改名称的无头角色配置文件的配置文件ID。
    2. 您可以在文本编辑器中打开`HeadlessConfig.json`来找到配置文件ID。
    3. 如果您添加多个配置文件，每行都需要以逗号`,`结尾，除了最后一行。

    <div align="left" data-full-width="false"><figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure></div>
4. 保存对`fika.jsonc`的更改并关闭文本编辑器。
5. 重启SPT.Server。

***

### :question:无头客户端的性能是否重要？

是的，某种程度上是。无头客户端的性能很重要，只要无头客户端在所有突袭场景中必须保持**高于30 FPS**。

要测试这一点，请连接到无头客户端托管的突袭，并在生成后，在您的游戏客户端上打开游戏内控制台（默认键是`~`），输入命令`debug t`，然后按Enter。

这将打开一个调试窗口，显示生成的机器人数量、您的ping/RTT，以及'服务器FPS'，即无头客户端的FPS。在整个突袭中游玩，参与战斗，投掷手榴弹等，并密切关注服务器FPS值。只要它保持在30以上，您就不应该遇到任何问题。

如果它下降到20多或十几，您可能会遇到AI行为异常和物理对象（如手榴弹）传送或缓慢移动的问题。减少生成的机器人数量或使用的模组数量，以使性能回到重要的30 FPS阈值以上。

如果即使没有任何其他模组，性能也下降到30 FPS以下，您的PC可能不够强大，无法托管无头客户端。如果您看到FPS值卡在59，这是预期行为，不表示有问题。

<figure><img src="../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

***

### :question:我收到关于"SPT.CustomPlugin中的补丁失败"的错误

错误`SPTCustomPlugin中的补丁失败。'SPT.Custom.Patches.CustomAiPatch'的类型初始值设定项...`应该在最新版本的FikaHeadlessManager中大部分避免。通过在无头客户端安装文件夹中重新运行Fika-Installer并选择`Advanced` -> `Update Fika Headless`来确保您拥有最新版本。

即使使用最新的FikaHeadlessManager，如果您仍然收到此错误，可能有什么东西阻止了您的无头客户端`EscapeFromTarkov.exe`专门连接到服务器，比如VPN或防火墙。

<figure><img src="../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
#### 确保SPT.Server正在运行并能够接受连接

使用SPT.Launcher测试连接：确保您可以启动游戏并到达您的仓库并访问商人。

如果您的SPT.Launcher无法连接到您的服务器，请找出原因并首先解决该问题。如果服务器当前正在运行但SPT.Launcher无法连接，请重新查看[托管Fika服务器](../../hosting-a-fika-server/)说明。

**注意**：无头客户端**不会替换SPT.Server**。后端服务器需要始终运行。
{% endhint %}

如果您已经生成了`HeadlessConfig.json`并且它在无头安装的根目录中，请在文本编辑器中打开它并将URL更改为与您连接到服务器的方式相匹配。这可能包括VPN IP或服务器的公共IP。保存对文件的更改并重新启动`FikaHeadlessManager.exe`

如果您尚未生成`HeadlessConfig.json`或无头配置文件，请重新查看[安装无头客户端的步骤](../../advanced-features/headless-client/remote-headless-client.md)并密切关注[关于编辑`fika.jsonc`的步骤](../../advanced-features/headless-client/remote-headless-client.md#optional-set-url-in-fika.jsonc)
