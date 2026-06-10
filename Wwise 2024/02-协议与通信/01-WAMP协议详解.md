# 01 - WAMP 协议详解

## 概述

WAMP (Web Application Messaging Protocol) 是 WAAPI 的主要通信协议。它是一个开放标准的 WebSocket 子协议，提供统一的应用路由功能。

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)

## 为什么使用 WAMP

> WAMP uses WebSocket as its default transport, which allows for ordered, reliable, bidirectional, and message-oriented communications. WAMP allows the clients to call functions with JSON arguments and retrieve structured JSON results. WAMP also allows clients to subscribe to notifications.

WAMP 相比纯 WebSocket 的优势：
- **统一路由**: 提供标准化的 RPC 和 Pub/Sub 模式
- **双向通信**: 客户端既可以调用函数，也可以订阅通知
- **连接复用**: 整个会话复用同一个 WebSocket 连接
- **性能最优**: 相比 HTTP POST，WAMP 提供最佳性能和体验
- **多语言支持**: WAMP 实现在大多数流行编程语言中可用

> WAMP is an open standard WebSocket subprotocol that provides unified application routing. WAMP implementations are available in the most popular programming languages. Read more about WAMP at https://wamp-proto.org.
>
> WAMP provides the best performance and experience because it reuses the same WebSocket connection for the whole session and provides bidirectional communications.

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)

## 连接建立

### WebSocket 握手

WAAPI 的 WAMP 连接通过 WebSocket 建立，连接参数如下：

| 参数 | 值 | 说明 |
|------|-----|------|
| URL | `ws://127.0.0.1:8080/waapi` | WebSocket 端点（本地连接） |
| URL (浏览器) | `ws://localhost:8080/waapi` | 浏览器中使用 localhost |
| Realm | `realm1` | WAMP 域 |
| Protocol | `wamp.2.json` | WAMP v2，JSON 序列化 |

> WaapiWampPort 的默认值为 8080。

### 默认端口

WAMP 默认使用端口 **8080**。此端口在 Wwise 的 User Preferences 中配置。

> WAAPI provides access to two ports for WAMP and HTTP (by default: 8080 and 8090).

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)

### 连接示例 (Node.js)

以下代码来自官方示例 `<Wwise installation path>/SDK/samples/WwiseAuthoringAPI/js/hello-wwise-node-wamp/index.js`：

```javascript
var ak = require('../../../../include/AK/WwiseAuthoringAPI/js/waapi.js').ak;
var autobahn = require('autobahn');

// 创建 WAMP 连接
var connection = new autobahn.Connection({
    url: 'ws://127.0.0.1:8080/waapi',
    realm: 'realm1',
    protocols: ['wamp.2.json']
});

// 连接打开时的处理
connection.onopen = function (session) {
    // 调用 getInfo
    session.call(ak.wwise.core.getInfo, [], {}).then(
        function (res) {
            console.log(`Hello ${res.kwargs.displayName} ${res.kwargs.version.displayName}!`);
        },
        function (error) {
            console.log(`Error: ${error}`);
        }
    ).then(
        function() {
            connection.close();
        }
    );
};

// 连接关闭时的处理
connection.onclose = function (reason, details) {
    if (reason !== 'lost') {
        console.log("Connection closed. Reason: " + reason);
    }
    process.exit();
};

// 打开连接
connection.open();
```

> **来源**: [JavaScript, Node.js - WAMP](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wamp_js_node.html)

### 浏览器连接示例

浏览器中使用 `autobahn-browser` 库：

```javascript
var connection = new autobahn.Connection({
    url: 'ws://localhost:8080/waapi',
    realm: 'realm1',
    protocols: ['wamp.2.json']
});

connection.onopen = function (session) {
    session.call(ak.wwise.core.getInfo, [], {}).then(
        function (res) {
            showMessage(`Hello ${res.kwargs.displayName} ${res.kwargs.version.displayName}`);
        },
        function (error) {
            showMessage(`error: ${error}`);
        }
    );
};

connection.open();
```

HTML 页面需要包含：
```html
<script src="node_modules/autobahn-browser/autobahn.min.js"></script>
<script src="../../../../include/AK/WwiseAuthoringAPI/js/waapi.js"></script>
```

> **来源**: [JavaScript, In browser - WAMP](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=wamp_js_browser.html)

## RPC（远程过程调用）模式

### 调用格式

WAMP RPC 调用使用 `session.call()` 方法：

```javascript
session.call(uri, args, options)
```

| 参数 | 类型 | 说明 |
|------|------|------|
| `uri` | string | 函数 URI，如 `ak.wwise.core.getInfo` |
| `args` | object/array | 函数参数，通常为空对象 `{}` 或空数组 `[]` |
| `options` | object | 调用选项，通常为空对象 `{}` |

### 返回值处理

调用返回一个 Promise，resolve 时返回结果对象，reject 时返回错误。

## 订阅/发布模式

WAAPI 通过 WAMP 的 Pub/Sub 模式支持**订阅通知**。客户端可以订阅特定的 Topic，当 Wwise 中发生相关事件时自动接收通知。

> WAAPI supports bidirectional communications, allowing processes to invoke remote procedure calls and to subscribe to their topics of interest so as to be notified when changes occur in Wwise.

> **来源**: [Using the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi.html)

### 如何订阅

参考 [Subscribing to Topics in the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_subscribe.html) 获取详细的订阅方法。

### 可订阅的 Topic 示例

以下来自官网列出的部分 Topic：

| Topic URI | 触发条件 |
|-----------|----------|
| `ak.wwise.core.object.created` | 对象被创建时 |
| `ak.wwise.core.object.preDeleted` | 对象被删除前 |
| `ak.wwise.core.object.postDeleted` | 对象被删除后 |
| `ak.wwise.core.object.nameChanged` | 对象被重命名时 |
| `ak.wwise.core.object.propertyChanged` | 对象属性变更时 |
| `ak.wwise.core.object.childAdded` | 子对象被添加时 |
| `ak.wwise.core.object.childRemoved` | 子对象被移除时 |
| `ak.wwise.core.project.loaded` | 工程加载完成时 |
| `ak.wwise.core.project.saved` | 工程保存时 |
| `ak.wwise.core.transport.stateChanged` | 传输状态变更时 |
| `ak.wwise.ui.selectionChanged` | UI 选择变更时 |
| `ak.wwise.core.soundbank.generated` | 单个 SoundBank 生成时 |

> **来源**: [Wwise Authoring API Reference - Topics](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_topics_index.html)

### 取消订阅

取消订阅的具体方法待补充（官网 WAAPI 文档中未找到专门的取消订阅页面，相关信息可能在具体的语言 SDK 文档中）。

## 会话管理

### 连接生命周期

1. **建立连接**: 通过 `connection.open()` 发起 WebSocket 连接
2. **会话活跃**: `connection.onopen` 回调中获取 `session` 对象
3. **执行操作**: 通过 `session.call()` 进行 RPC 调用，通过 `session.subscribe()` 订阅通知
4. **关闭连接**: 通过 `connection.close()` 主动关闭

### 多客户端支持

> WAAPI supports usage from multiple connections at once. The current maximum number of active connections to WAAPI is 20 for WAMP, with another 20 for HTTP POST.

WAMP 最大连接数: **20** 个并发连接。

> **来源**: [Preparing to use the Wwise Authoring API](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html)

### 连接关闭回调

```javascript
connection.onclose = function (reason, details) {
    if (reason !== 'lost') {
        console.log("Connection closed. Reason: " + reason);
    }
};
```

`reason` 可能的值为 `'lost'`（连接丢失）或其他关闭原因。

## 心跳/保活机制

WAAPI 提供了 ping 功能来验证连接状态，对应函数为 `ak.wwise.core.ping`。官方示例中有一个专门的页面：

> [Verify the status of WAAPI](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=ak_wwise_core_ping_example_verify_the_status_of_waapi.html)

具体的 WAMP 协议层心跳机制（如 WebSocket ping/pong 帧）由底层的 WAMP 实现库（如 Autobahn）处理，WAAPI 本身未在文档中详细说明。

## 编程语言支持

WAAPI 推荐以下语言和库：

| 语言 | 推荐库 | 说明 |
|------|--------|------|
| C++ | AkAutobahn | Autobahn C++ 分支，减少依赖，提供简化接口 |
| C# | WaapiClientCore / WaapiClientJson | .NET 4.5 兼容；WaapiClientCore 无第三方依赖，兼容 Unity |
| JavaScript/TypeScript (Node.js) | waapi-client | 基于 Autobahn JS，添加 Promise 和 async/await |
| JavaScript (Browser) | autobahn-browser | 浏览器中使用的 WAMP 实现 |
| Python 3.7+ | waapi-client Python | 简化接口，仅暴露所需 WAMP 功能 |
| 其他语言 | wamp-proto.org 上的实现 | 直接使用 WAMP 实现或 HTTP 方式 |

> **来源**: [Getting Started with the Wwise Authoring API (WAAPI)](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html)
