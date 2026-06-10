# 常见问题 FAQ

> 本章节汇总了 Wwise Authoring API (WAAPI) 使用过程中的常见问题及解决方案。所有内容基于 Wwise 2024.1.14 官方文档。

---

## 连接与配置

### Q1: 如何启用 WAAPI？

**问题描述**：我不确定 WAAPI 是否已在我的 Wwise 中启用。

**原因**：WAAPI 默认是启用的，但用户可能手动禁用了它。

**解决方案**：
1. 在 Wwise 中选择 **Project > User Preferences**（快捷键 `Shift+U`）
2. 在 **Wwise Authoring API** 组框中，勾选 **Enable Wwise Authoring API**
3. 点击 **OK**

> 来自官方文档：*"The Wwise Authoring API is normally enabled by default."*（WAAPI 通常默认启用。）

---

### Q2: WAAPI 使用哪些端口？

**问题描述**：我不知道应该连接哪个端口。

**解决方案**：

| 协议 | 默认端口 | 端点路径 | 说明 |
|------|---------|----------|------|
| WAMP (WebSocket) | **8080** | `/waapi` | 推荐使用，支持双向通信和订阅 |
| HTTP POST | **8090** | `/waapi` | 适用于不支持 WebSocket 的环境 |

> 来自官方文档：*"WAAPI provides access to two ports for WAMP and HTTP (by default: 8080 and 8090)."*

---

### Q3: 如何从远程计算机连接到 WAAPI？

**问题描述**：我在另一台计算机上运行客户端，无法连接到运行 Wwise 的主机。

**原因**：默认情况下，WAAPI **仅接受来自 localhost（127.0.0.1 或 ::1）** 的连接。

**解决方案**：
1. 在 Wwise 中打开 **Project > User Preferences**
2. 在 **Allow connections from** 字段中添加远程计算机的 IP 地址
3. 确保防火墙允许访问 8080（WAMP）和 8090（HTTP）端口
4. 点击 **OK**

> ⚠️ 官方文档警告：*"You can add \* to allow connections from any IP address. But, this is insecure and, therefore, unrecommended."*（可以添加 \* 允许任意 IP，但不安全且不推荐。）

---

### Q4: 如何在浏览器中使用 WAAPI？

**问题描述**：我在网页中使用 JavaScript 调用 WAAPI，但浏览器报 CORS 错误。

**原因**：WAAPI 有跨站脚本（XSS）安全层。默认情况下，浏览器中只有从**本地文件系统**打开的 HTML 文件才能访问 WAAPI。从远程 web 服务器加载的页面会被阻止。

**解决方案**（来自官方文档）：
1. 确保远程主机的 **IP 地址**已添加到 **Allow connections from** 字段
2. 在 **Allow browser connections from origins** 字段中添加 web 页面的完整 origin URI。例如 `http://www.myhost.com` 或 `http://www.myhost.com:1234`
3. 两个字段**都必须**配置

> 来自官方文档：*"If you are connecting to WAAPI through a browser, both the IP address and origin of the web server must be added for the connection to be allowed."*

---

### Q5: WAAPI 支持多少个并发连接？

**问题描述**：多个客户端同时连接时，部分连接被拒绝。

**原因**：WAAPI 有最大并发连接数限制。

**解决方案**：

| 协议 | 最大连接数 |
|------|-----------|
| WAMP | 20 |
| HTTP POST | 20 |

> 来自官方文档：*"The current maximum number of active connections to WAAPI is 20 for WAMP, with another 20 for HTTP POST."*

- 确保客户端正常关闭不再使用的连接
- 对于 WAMP，使用连接池复用 session
- HTTP POST 为无状态请求，通常不会占用长连接

---

### Q6: WAMP 连接时需要什么 Realm？

**问题描述**：WAMP 客户端连接时认证失败。

**解决方案**：WAAPI 固定使用 Realm 名称 **`realm1`**。这是 WAAPI 唯一支持的 Realm。

```javascript
// JavaScript (autobahn) 示例
const connection = new autobahn.Connection({
  url: 'ws://127.0.0.1:8080/waapi',
  realm: 'realm1'  // 必须是 'realm1'
});
```

（官网未提供修改 Realm 的选项。）

---

### Q7: WAMP 和 HTTP POST 有什么区别？我应该用哪个？

**问题描述**：不确定选择哪种协议。

**解决方案**：

| 特性 | WAMP | HTTP POST |
|------|------|-----------|
| 远程过程调用 (RPC) | ✅ 支持 | ✅ 支持 |
| 发布与订阅 (Pub/Sub) | ✅ 支持 | ❌ 不支持 |
| 最佳性能 | ✅ 是 | ❌ 否 |
| 双向通信 | ✅ 是 | ❌ 否 |
| 连接复用 | ✅ 整个 session 复用同一 WebSocket | ❌ 每个请求独立 |

> 来自官方文档：*"WAMP provides the best performance and experience because it reuses the same WebSocket connection for the whole session and provides bidirectional communications."*

**建议**：如果语言支持 WebSocket，优先使用 WAMP；简单的一次性调用或 curl 测试可用 HTTP POST。

---

## 编程语言

### Q8: 支持哪些编程语言？

**问题描述**：我想知道我的项目使用的语言是否能调用 WAAPI。

**解决方案**（来自官方文档的推荐）：

| 语言 | 推荐方案 | 难度 |
|------|---------|------|
| **C++** | AkAutobahn（Autobahn C++ 的 fork） | 中级 |
| **C#** | WaapiClientCore 或 WaapiClientJson | 初级 |
| **JavaScript/TypeScript (Node.js)** | waapi-client（npm 包） | 初级~中级 |
| **JavaScript (浏览器)** | autobahn-browser | 中级 |
| **Python 3.7+** | waapi-client-python（PyPI 包） | 初级 |
| **其他语言** | 使用标准 WAMP 实现或直接 HTTP POST | 视实现而定 |

> 来自官方文档：*"WAMP and HTTP protocols can be used with a variety of languages, such as C++, C#, JavaScript, Python, and other languages with HTTP or WebSocket support."*

---

## Mac 平台

### Q9: 在 Mac 上如何正确使用 WAAPI 路径？

**问题描述**：在 Mac 上使用 WAAPI 加载项目或导入文件时，路径无效。

**原因**：WAAPI 使用 Windows 风格的路径格式。

**解决方案**（来自官方文档）：

| Mac 路径 | WAAPI 路径 |
|----------|-----------|
| 根目录 `/` | `Z:\` |
| `/Volumes/path/to/file.wproj` | `Z:\Volumes\path\to\file.wproj` |

> 来自官方文档：*"WAAPI uses Windows-style paths to access files, with the root folder '/' represented by drive Z and the home folder drive Y. In case of doubt, you can refer to the project path as displayed in the recent projects in Wwise."*

---

## 故障排除

### Q10: 如何快速检查 WAAPI 是否正常工作？

**问题描述**：我想确认 WAAPI 是否可用，但不清楚如何测试。

**解决方案**：使用 `ak.wwise.core.ping` 函数。它不需要任何参数，返回空对象 `{}` 即表示 WAAPI 正常运行。

**WAMP (JavaScript)**:
```javascript
const result = await session.call('ak.wwise.core.ping');
// result = {}  表示成功
```

**HTTP POST (curl)**:
```bash
curl -X POST http://localhost:8090/waapi \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"ak.wwise.core.ping"}'
```

**Python**:
```python
from waapi import WaapiClient
client = WaapiClient()
result = client.call("ak.wwise.core.ping")
# result = {}  表示成功
```

---

### Q11: 模态对话框弹出时 WAAPI 无响应怎么办？

**问题描述**：当 Wwise 弹出模态对话框时，WAAPI 请求超时或无响应。

**原因**：模态对话框（如项目迁移确认、EULA 接受、错误消息框等）会阻塞 Wwise 的消息循环，导致 WAAPI 服务器无法处理请求。

**解决方案**：
1. 调用 `ak.wwise.debug.enableAutomationMode` 启用自动化模式，减少对话框弹出：
   ```json
   {
     "method": "ak.wwise.debug.enableAutomationMode",
     "params": {"enable": true}
   }
   ```
   启用后以下对话框将被静默处理：项目迁移、项目加载日志、EULA 接受、许可证显示、通用消息框。

2. 在客户端实现请求超时和重试逻辑
3. 定期使用 `ak.wwise.core.ping` 检测可用性

---

### Q12: 为什么我的函数调用返回 "Method not found"（-32601）错误？

**问题描述**：调用的函数明明在文档中存在，但返回 -32601 错误。

**可能原因和解决方案**：

| 原因 | 解决方案 |
|------|---------|
| 函数名拼写错误 | 仔细检查函数 URI（如 `ak.wwise.core.getInfo` 而非 `ak.wwise.core.getinfo`） |
| 使用了 HTTP POST 调用仅 WAMP 支持的功能（如 Pub/Sub） | 订阅和通知功能仅支持 WAMP 协议，使用 HTTP POST 会返回 -32601 |
| 函数在当前 Wwise 版本中不存在 | 使用 `ak.wwise.waapi.getFunctions` 查询所有可用函数 |

---

### Q13: 创建对象时提示参数错误（-32602）怎么办？

**问题描述**：调用 `ak.wwise.core.object.create` 返回 -32602 错误。

**解决方案**：
1. 使用 `ak.wwise.waapi.getSchema` 查询函数的完整参数 schema：
   ```json
   {
     "method": "ak.wwise.waapi.getSchema",
     "params": {"uri": "ak.wwise.core.object.create"}
   }
   ```
2. 确认所有带 `*` 标记的必需参数已提供
3. 使用 `ak.wwise.core.object.getTypes` 获取所有有效的对象类型名称
4. 确认父对象的 GUID 或路径正确存在

---

### Q14: 如何查看 WAAPI 操作的详细日志？

**问题描述**：WAAPI 调用失败，但错误信息不够详细，需要更多上下文。

**解决方案**：
1. Wwise 的 **General** 日志标签页会显示 WAAPI 相关的消息
2. 使用 WAAPI 编程访问日志：
   - `ak.wwise.core.log.get` — 检索指定 channel 的最新日志
   - 订阅 `ak.wwise.core.log.itemAdded` 主题（仅 WAMP）获取实时日志通知
3. 使用 `ak.wwise.core.log.addItem` 在日志中添加自定义消息以辅助调试

**注意**：在 WwiseConsole（命令行模式）中，日志为空。日志仅在 Wwise Authoring UI 中可用。

---

### Q15: 音频导入失败但不报错怎么办？

**问题描述**：调用 `ak.wwise.core.audio.import` 后，部分文件没有导入成功，但函数没有返回错误。

**原因**（来自官方文档）：*"This function does not return an error when something fails during the import process, please refer to the log for the result of each import command."*

**解决方案**：
1. 检查函数的返回数组，确认哪些对象被创建、替换或复用
2. 使用 `ak.wwise.core.log.get` 查看导入日志，获取每个导入命令的详细结果
3. 确保音频文件路径正确（Mac 上使用 Windows 风格路径）
4. 验证音频文件格式是否受支持

---

### Q16: 如何安全地配置 WAAPI 的网络访问？

**问题描述**：我需要在团队环境中使用 WAAPI，但担心安全风险。

**解决方案**（来自官方文档的安全建议）：

1. **使用防火墙**：阻止未授权的远程计算机访问 8080 和 8090 端口
2. **白名单 IP**：仅将需要访问的特定 IP 地址添加到 "Allow connections from" 字段，而非使用 `*`
3. **白名单 Origin**：浏览器场景下，仅添加可信的 Origin URI 到 "Allow browser connections from origins" 字段
4. **本地优先**：尽可能通过 localhost 连接，避免暴露到网络

> 来自官方文档：*"Since WAAPI allows you to control Wwise remotely, it must be used in a secure environment in order to prevent other people from gaining control of your computer."*

---

### Q17: 如何通过命令行配置 WAAPI？

**问题描述**：我需要在自动化脚本中配置 WAAPI 参数，不想手动打开 User Preferences。

**解决方案**（来自官方文档）：使用 Wwise 的命令行 `-Waapi` 参数。具体参数格式请参考 [Using the Command Line](https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=using_command_line.html) 文档。（详细的命令行参数列表官网未在 WAAPI Prepare 页面中提供，需要查阅命令行参考文档。）

---

### Q18: Wwise 项目未加载时哪些 WAAPI 函数可以正常工作？

**问题描述**：在没有打开项目的情况下，不确定哪些函数可以调用。

**解决方案**：

以下函数**不需要**打开项目即可使用：
- `ak.wwise.core.ping` — 检查 WAAPI 可用性
- `ak.wwise.core.getInfo` — 获取 Wwise 信息
- `ak.wwise.waapi.getFunctions` — 获取函数列表
- `ak.wwise.waapi.getSchema` — 获取函数 Schema
- `ak.wwise.waapi.getTopics` — 获取订阅主题列表
- `ak.wwise.ui.project.open` — 打开项目
- `ak.wwise.ui.project.create` — 创建项目
- `ak.wwise.ui.bringToForeground` — 将 Wwise 窗口置前

（官网未提供完整的"无项目状态下可用函数"列表，以上为基于函数定义的合理推断。）

---

## 参考

- Preparing to use the Wwise Authoring API：https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_prepare.html
- Getting Started with WAAPI：https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_gettingstarted.html
- Wwise Authoring API Reference - Functions：https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_functions_index.html
- WAAPI Samples：https://www.audiokinetic.com/library/2024.1.14_9084/?source=SDK&id=waapi_samples.html
