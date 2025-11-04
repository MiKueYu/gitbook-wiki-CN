---
description: 所有我们的API（最后更新于SPT 4.0，Fika 2.0）
---

# Fika API

## 概述

API密钥在首次启动时自动生成。您可以在配置文件夹中的`fika.jsonc`文件中找到它。

使用API密钥在发出请求时进行身份验证。您还需要添加值为`0`的`requestcompressed`头。

<details>

<summary>C#身份验证示例</summary>

```csharp
client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", config.APIKey);
client.DefaultRequestHeaders.Add("requestcompressed", "0");
```

</details>

例如在Postman中，身份验证类型是"API Key"，键是"`Authorization`"，值是"`Bearer {apiKey}`"。

## 获取

### fika/api/items

返回SPT数据库中的所有物品，其中MongoID是标识符，名称、描述和可堆叠数量是值。\
\
示例响应：

{% code fullWidth="false" %}
```json
{
    "items": {
        "5447a9cd4bdc2dbd208b4567": {
            "name": "Colt M4A1 5.56x45突击步枪",
            "description": "Colt M4A1卡宾枪是基本M4卡宾枪的全自动变体，主要为特种作战用途设计。\n然而，美国特种作战司令部（USSOCOM）很快采用M4A1用于几乎所有特种作战单位，随后M4A1被引入美国陆军和海军陆战队服役。",
            "stackable": 10
        }
}
```
{% endcode %}

### fika/api/raids

返回所有活动突袭。

### fika/api/headless

返回所有活动的无头客户端。

### fika/api/heartbeat

检查服务器是否正在运行。主要由WebApp使用。

### fika/api/players

返回所有在线玩家。

### fika/api/rawprofile

以JSON格式返回原始配置文件。

输入：

<table data-full-width="false"><thead><tr><th>键</th><th>值</th><th>描述</th></tr></thead><tbody><tr><td>profileId</td><td>{validMongoID}</td><td>要返回原始配置文件的MongoID。</td></tr></tbody></table>

示例输入：

`{baseUrl}/fika/api/rawprofile?profileId=68e8f63d941b8a1c94c1d8bf`

## 发布

### fika/api/fleaban

禁止玩家使用跳蚤市场X天。0 = 无限期。

<details>

<summary>架构</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "跳蚤市场禁令请求",
  "description": "禁止玩家在跳蚤市场指定天数的架构。",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "玩家配置文件的唯一标识符。"
    },
    "amountOfDays": {
      "type": "integer",
      "minimum": 0,
      "description": "玩家被禁止的天数。0表示禁令是无限期的。"
    }
  },
  "required": ["profileId", "amountOfDays"],
  "additionalProperties": false
}
```



</details>

### fika/api/createheadlessprofile

创建一个无头配置文件。由安装程序使用，不建议使用。

### fika/api/logout

从游戏中注销给定的MongoID。

<details>

<summary>架构</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "注销请求",
  "description": "使用其MongoID配置文件ID将玩家从游戏中注销的架构。",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "要注销的玩家的MongoDB ObjectID。"
    }
  },
  "required": ["profileId"],
  "additionalProperties": false
}
```



</details>

### fika/api/restartheadless

使用给定的MongoID重启无头客户端。

<details>

<summary>架构</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "重启无头客户端请求",
  "description": "重启与给定玩家配置文件ID相关联的无头实例的架构。",
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "应该重启无头实例的玩家的MongoDB ObjectID。"
    }
  },
  "required": ["profileId"],
  "additionalProperties": false
}
```



</details>

### fika/api/senditem

向给定的MongoID发送X数量的物品。

<details>

<summary>架构</summary>

{% code fullWidth="false" %}
```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "发送物品请求",
  "description": "向给定MongoID配置文件ID的玩家发送物品的架构。",
  "type": "object",
  "properties": {
    "itemTpl": {
      "type": "string",
      "description": "正在发送的物品的模板ID。"
    },
    "amount": {
      "type": "integer",
      "minimum": 1,
      "description": "要发送的物品数量。"
    },
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "随物品发送的可选消息。可以为空。"
    },
    "fir": {
      "type": "boolean",
      "description": "物品是否标记为突袭中找到（FIR）。"
    },
    "expirationDays": {
      "type": "integer",
      "minimum": 1,
      "description": "消息过期前的天数。"
    },
    "profileId": {
      "type": "string",
      "description": "要发送物品给的玩家的MongoDB ObjectID。"
    }
  },
  "required": [
    "itemTpl",
    "amount",
    "message",
    "fir",
    "expirationDays",
    "profileId"
  ],
  "additionalProperties": false
}
```
{% endcode %}



</details>

### fika/api/senditemtoall

向给定的MongoID发送X数量的物品。

<details>

<summary>架构</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "向多个玩家发送物品请求",
  "description": "使用其MongoID配置文件ID向多个玩家发送物品的架构。",
  "type": "object",
  "properties": {
    "itemTpl": {
      "type": "string",
      "description": "正在发送的物品的模板ID。"
    },
    "amount": {
      "type": "integer",
      "minimum": 1,
      "description": "发送给每个玩家的物品数量。"
    },
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "随物品发送的可选消息。可以为空。"
    },
    "fir": {
      "type": "boolean",
      "description": "物品是否标记为突袭中找到（FIR）。"
    },
    "expirationDays": {
      "type": "integer",
      "minimum": 1,
      "description": "消息过期前的天数。"
    },
    "profileIds": {
      "type": "array",
      "description": "代表要发送物品的玩家配置文件的MongoDB ObjectID列表。",
      "items": {
        "type": "string"
      },
      "minItems": 1
    }
  },
  "required": [
    "itemTpl",
    "amount",
    "message",
    "fir",
    "expirationDays",
    "profileIds"
  ],
  "additionalProperties": false
}
```



</details>

### fika/api/sendmessage

向MongoID发送消息。

<details>

<summary>架构</summary>

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "发送消息请求",
  "description": "使用其MongoID配置文件ID向玩家发送消息的架构。",
  "type": "object",
  "properties": {
    "message": {
      "type": "string",
      "maxLength": 255,
      "description": "要发送给玩家的消息。可以为空。"
    },
    "profileId": {
      "type": "string",
      "description": "要发送消息给的玩家的MongoDB ObjectID。"
    }
  },
  "required": ["message", "profileId"],
  "additionalProperties": false
}
```



</details>
