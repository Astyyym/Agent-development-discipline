# Python 运行时依赖与导入验证

## MCP Server 依赖

源码若使用 `from mcp.server.fastmcp import FastMCP, Context`，项目应声明：

```bash
uv add "mcp>=1.3"
uv sync
```

不要只依赖当前机器的全局 Python 环境。检查结果应能在新 clone 的项目虚拟环境中复现。

## FastMCP API 兼容性

MCP SDK 版本升级后，先查询实际签名：

```bash
uv run python -c "import inspect; from mcp.server.fastmcp import FastMCP; print(inspect.signature(FastMCP))"
```

部分版本不接受 `description=`，可使用当前签名支持的 `instructions=`。不要凭旧代码或记忆判断参数名。

## 最小验证链

```bash
python3 -m compileall -q qgis_mcp_plugin src scripts
PYTHONPATH=src uv run python -c \
  "from qgis_mcp.qgis_mcp_server import mcp; print(type(mcp).__name__); print(len(mcp._tool_manager._tools))"
git diff --check
git status --short --branch
```

导入成功和工具注册成功只证明 Python/MCP 层可用；QGIS 插件加载、TCP 连接和真实 GIS 操作仍需在已安装 QGIS 的 Windows 环境单独验收。

## MCP stdio 协议冒烟测试

启动 Server 后，使用 stdio 发送真实 JSON-RPC 请求，至少验证：

```json
{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-03-26","capabilities":{},"clientInfo":{"name":"smoke-test","version":"1.0"}}}
{"jsonrpc":"2.0","id":2,"method":"tools/list","params":{}}
```

应分别确认：

- `initialize` 返回 `result.serverInfo` 和协议版本；
- `tools/list` 返回工具描述、参数 schema 和工具列表；
- 没有 QGIS 插件运行时，连接 `9876` 的超时只记录为外部运行时前置条件未满足；不能把它误报成 MCP 协议失败；
- 最终报告明确区分“Python 导入层”“MCP 协议层”“QGIS TCP/真实工具层”。
