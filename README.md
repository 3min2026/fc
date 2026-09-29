# fc · 快捷命令

内网 IT 运维速查工具 —— 命令速查、软件链接、脚本工具，一套 SQLite 数据库，一个 HTML 文件。

纯静态、零后端、零外部依赖。浏览器打开即用，可离线部署，适合内网分发。

---

## 功能概览

| 模块 | 说明 |
|------|------|
| 命令速查 | 按平台/分类/Shell 筛选，关键字多词 AND 搜索，一键复制命令 |
| 软件链接 | 按分类/平台筛选，一键打开或复制下载地址 |
| 脚本工具 | 浏览 Python / PowerShell / bat / vbs / Shell 脚本，支持下载为对应后缀文件 |

数据统一存储在 `commands.db`（SQLite）中，刷新页面即可看到最新内容。

---

## 目录结构

fc/
├── index.html # 主页面（含内置 CSS，深色主题）
├── sql-wasm.js # sql.js 主文件（浏览器端 SQLite 引擎）
├── sql-wasm.wasm # sql.js WASM 二进制
├── commands.db # SQLite 数据库（三张表）
├── README.md
├── LICENSE
└── THIRD_PARTY_LICENSES.md


> `sql-wasm.js`、`sql-wasm.wasm` 和 `commands.db` 必须与 `index.html` 放在同一目录。

---

## 快速开始

### 1. 启动静态服务器

浏览器对 `file://` 协议下的 `fetch` 和 WASM 加载有严格限制，**不能直接双击打开 HTML**，必须通过 HTTP 访问。

最简方式（Python 3 自带）：

```bash
python -m http.server 8080