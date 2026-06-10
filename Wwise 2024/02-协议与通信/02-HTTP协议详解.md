# 02 - HTTP 协议详解

## 概述

WAAPI 支持通过 HTTP POST 协议进行通信。HTTP 是一种用于分布式应用的应用层协议，是互联网上最常用的内容传输方式。

> HTTP POST: HTTP is an application protocol for distributed applications. HTTP is the most used method to transfer content on the Internet. POST enables the caller to send a document body, which, for the Wwise Authoring API, corresponds to the function arguments as JSON. The HTTP response is the JSON result.

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)

## HTTP vs WAMP 选择

| 特性 | HTTP POST | WAMP |
|------|-----------|------|
| 远程过程调用 (RPC) | ✅ 支持 | ✅ 支持 |
| 发布与订阅 (Pub/Sub) | ❌ 不支持 | ✅ 支持 |
| 双向通信 | ❌ 单向（请求-响应） | ✅ 双向 |
| 连接复用 | ❌ 每次请求新建连接 | ✅ 单连接复用 |
| 性能 | 一般 | 最优 |
| 实现复杂度 | 简单 | 中等 |
| 适用场景 | 简单脚本、无状态操作 | 需要实时通知、高性能场景 |

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)

## 端点 URL

### URL 格式

```
http://<host>:<port>/waapi
```

| 组件 | 默认值 | 说明 |
|------|--------|------|
| `host` | `127.0.0.1` | WAAPI 所在主机地址 |
| `port` | `8090` | HTTP 端口 (`WaapiHttpPort`) |
| 路径 | `/waapi` | 固定端点路径 |

### 默认端口

HTTP 默认使用端口 **8090**。此端口在 Wwise 的 User Preferences 中配置。

> WAAPI provides access to two ports for WAMP and HTTP (by default: 8080 and 8090).

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)

### 本地连接

```
http://127.0.0.1:8090/waapi
```

> **来源**: [JavaScript, Node.js - HTTP POST](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=http_post_js.html)

## HTTP 方法

WAAPI 仅支持 **POST** 方法。GET 等其他 HTTP 方法不被支持。

## 请求头

| Header | 值 | 必须 |
|--------|-----|------|
| `Content-Type` | `application/json` | ✅ 是 |

请求体以 JSON 格式发送。

## 请求体格式

HTTP POST 请求体直接使用 JSON 格式，包含以下字段：

```json
{
    "uri": "ak.wwise.core.getInfo",
    "options": {},
    "args": {}
}
```

| 字段 | 类型 | 说明 |
|------|------|------|
| `uri` | string | 要调用的 WAAPI 函数 URI |
| `options` | object | 调用选项（通常为空对象 `{}`） |
| `args` | object | 函数参数（通常为空对象 `{}`） |

> **来源**: [JavaScript, Node.js - HTTP POST](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=http_post_js.html)

## 响应格式

### 成功响应 (HTTP 200)

成功调用时，HTTP 状态码为 200，响应体为 JSON 对象，直接包含函数的返回值：

```json
{
    "displayName": "Wwise",
    "version": {
        "displayName": "2024.1.14.9084"
    }
}
```

### 错误响应

当调用失败时，响应可能包含错误信息：

- HTTP 状态码为非 200
- 如果响应头 `content-type` 为 `application/json`，响应体是一个包含错误详情的 JSON 对象
- 否则响应体为纯文本错误消息

## CORS 跨域说明

当通过浏览器连接 WAAPI 时，需要配置跨域访问：

### Origin 白名单

默认情况下，WAAPI 仅接受来自本地软件或本地文件系统打开的 HTML 文件的连接。从其他主机加载的网页需要预先在白名单中添加源地址。

配置方法：
1. 在 Wwise 中选择 **Project > User Preferences**
2. 在 **Allow browser connections from origins** 字段中添加主机 URI
   - 例如：`http://www.myhost.com`（假设端口 80）
   - 或 `http://www.myhost.com:1234`（使用端口 1234）

> WAAPI provides a security layer against cross-site scripting. By default, WAAPI will only accept connections from local software or, in the case of browsers, only when opening HTML files on the local file system.

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)

> ⚠️ **警告**: 可以添加 `*` 来允许来自任何源的连接，但这是不安全的，不推荐使用。

## 完整 HTTP 请求/响应示例

### Node.js 示例

以下代码来自官方示例 `<Wwise installation path>/SDK/samples/WwiseAuthoringAPI/js/hello-wwise-node-http/index.js`：

```javascript
(() => {
    const axios = require('axios');
    const ak = require('../../../../include/AK/WwiseAuthoringAPI/js/waapi.js').ak;

    const data = {
        uri: ak.wwise.core.getInfo,
        options: {},
        args: {}
    };

    const handleResponse = (status, headers, objectPayload) => {
        if (status != 200) {
            if (headers["content-type"] == "application/json") {
                console.log(`Error: ${objectPayload.uri}: ${JSON.stringify(objectPayload)}`);
            } else {
                console.log(`Error: ${Buffer.from(objectPayload).toString("utf8")}`);
            }
        } else {
            console.log(`Hello ${objectPayload.displayName} ${objectPayload.version.displayName}`);
        }
    };

    axios({
        method: "post",
        url: "http://127.0.0.1:8090/waapi",
        data: data,
        headers: { "content-type": "application/json" }
    }).then((response) => {
        handleResponse(response.status, response.headers, response.data);
    }).catch((err) => {
        if (err.response) {
            handleResponse(err.response.status, err.response.headers, err.response.data);
        } else {
            console.log(`Error: ${err.message}`);
        }
    });
})();
```

> **来源**: [JavaScript, Node.js - HTTP POST](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=http_post_js.html)

### 原始 HTTP 请求

```
POST /waapi HTTP/1.1
Host: 127.0.0.1:8090
Content-Type: application/json

{
    "uri": "ak.wwise.core.getInfo",
    "options": {},
    "args": {}
}
```

### 原始 HTTP 响应

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "displayName": "Wwise",
    "version": {
        "displayName": "2024.1.14.9084"
    }
}
```

## 最大连接数

> The current maximum number of active connections to WAAPI is 20 for WAMP, with another 20 for HTTP POST.

HTTP POST 最大并发连接数: **20**。

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)
