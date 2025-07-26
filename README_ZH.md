# 🔍 WHOIS MCP 服务器

**中文版** | **[English](./README.md)**

> 用于域名、IP、TLD 和 ASN 的 WHOIS 查询的综合 MCP 服务器

## 🎯 项目概述

一个模型上下文协议（MCP）服务器，提供域名、IP 地址、顶级域名（TLD）和自治系统号（ASN）的 WHOIS 查询功能。使用 TypeScript 构建，基于 `whoiser` 库实现可靠快速的 WHOIS 查询。

## ✨ 功能特性

- 🌐 **域名 WHOIS**: 查找任何域名的注册信息
- 🖥️ **IP WHOIS**: 获取 IP 地址的网络信息和所有权详情
- 🏷️ **TLD WHOIS**: 检索顶级域名信息
- 🔢 **ASN WHOIS**: 查找自治系统号详情
- 🔒 **类型安全**: 使用 Zod 验证的完整 TypeScript 实现
- 🎨 **彩色日志**: 彩色控制台输出，提高可见性
- ⚡ **高性能**: 基于可靠的 `whoiser` 库构建
- 🛡️ **错误处理**: 全面的错误处理和友好的错误消息

## 📦 安装

```bash
npm install @szemeng76/whois-mcp
```

或者克隆并本地安装：

```bash
git clone https://github.com/SzeMeng76/whois-mcp.git
cd whois-mcp
npm install
npm run build
```

## 🔧 配置

### Claude Desktop

```json
{
  "mcpServers": {
    "whois": {
      "command": "npx",
      "args": ["@szemeng76/whois-mcp@latest"]
    }
  }
}
```

### Cursor IDE

```json
{
  "mcpServers": {
    "whois": {
      "command": "npx",
      "args": ["@szemeng76/whois-mcp@latest"]
    }
  }
}
```

### VS Code 与 GitHub Copilot

```json
{
  "mcp.servers": {
    "whois": {
      "command": "npx",
      "args": ["@szemeng76/whois-mcp@latest"],
      "transport": "stdio"
    }
  }
}
```

### 本地开发

```json
{
  "mcpServers": {
    "whois": {
      "command": "node",
      "args": ["path/to/whois-mcp/dist/index.js"]
    }
  }
}
```

## 🛠️ 可用工具

### `whois_domain`
查找域名的 WHOIS 信息。

**参数：**
- `domain`（必需）: 要查询的域名（如 "example.com"、"github.com"）

**使用示例：**
```
"查找 google.com 的 WHOIS 信息"
"获取 stackoverflow.com 的域名注册详情"
"检查 github.com 域名的所有者"
```

**返回内容：**
- 域名注册信息
- 注册商详情
- 名称服务器
- 创建和到期日期
- 注册人联系信息（如果可用）

### `whois_ip`
查找 IP 地址的 WHOIS 信息。

**参数：**
- `ip`（必需）: 要查询的 IPv4 或 IPv6 地址（如 "8.8.8.8"、"1.1.1.1"）

**使用示例：**
```
"获取 IP 地址 8.8.8.8 的 WHOIS 信息"
"查找 IP 1.1.1.1 的所有者"
"检查 192.168.1.1 的网络详情"
```

**返回内容：**
- 网络所有权信息
- IP 地址范围分配
- 组织详情
- 地理位置数据
- 联系信息

### `whois_tld`
查找顶级域名的 WHOIS 信息。

**参数：**
- `tld`（必需）: 要查询的顶级域名（如 "com"、"org"、"io"）

**使用示例：**
```
"获取 .com 顶级域名的信息"
"查找 .io 域名的详情"
"检查谁管理 .org 顶级域名"
```

**返回内容：**
- TLD 注册机构信息
- 管理组织
- 政策详情
- 联系信息
- 技术详情

### `whois_as`
查找自治系统号的 WHOIS 信息。

**参数：**
- `asn`（必需）: "AS####" 格式的 ASN（如 "AS15169"、"AS13335"）

**使用示例：**
```
"查找 ASN AS15169"
"获取 AS13335 的信息"
"检查自治系统 AS8075 的详情"
```

**返回内容：**
- ASN 所有权信息
- 组织详情
- 网络路由
- 联系信息
- 技术详情

## 🎮 使用示例

### 安全研究
```
"查找域名 suspicious-site.com 来检查其注册详情"
"获取 IP 203.0.113.1 的 WHOIS 信息以识别网络所有者"
```

### 网络故障排除
```
"检查 ASN AS15169 查看谷歌运营的网络"
"查找 IP 1.1.1.1 验证它属于 Cloudflare"
```

### 域名调查
```
"获取 example.com 的注册详情查看到期时间"
"查找 .io 顶级域名信息了解注册机构政策"
```

### 竞争分析
```
"检查 competitor-domain.com 的 WHOIS 查看注册模式"
"查找多个域名：example1.com、example2.org、example3.net"
```

## 🏗️ 开发

### 本地设置

```bash
# 克隆仓库
git clone https://github.com/SzeMeng76/whois-mcp.git
cd whois-mcp

# 安装依赖
npm install

# 构建项目
npm run build

# 启动服务器
npm start
```

### 项目结构

```
whois-mcp/
├── src/
│   ├── index.ts          # 主 MCP 服务器实现
│   └── utils.ts          # 工具函数（彩色控制台输出）
├── dist/                 # 编译后的 JavaScript 文件
├── package.json          # 依赖和脚本
├── tsconfig.json         # TypeScript 配置
└── README.md            # 文档
```

### 核心依赖

- **@modelcontextprotocol/sdk**: 官方 MCP 服务器框架
- **whoiser**: 可靠的 WHOIS 查询库
- **zod**: 运行时类型验证和模式定义

## 🔧 技术细节

### 输入验证
- **域名**: 基本的非空字符串验证
- **IP 地址**: 基本的非空字符串验证（库处理格式验证）
- **TLD**: 非空字符串验证
- **ASN**: "AS####" 格式的正则表达式验证，自动数字转换

### 错误处理
- 所有 WHOIS 操作的全面 try-catch 块
- 常见问题的友好错误消息
- 网络超时和无效输入的优雅处理
- 错误响应包含 `isError: true` 标志

### 日志和输出
- 使用自定义工具函数的彩色控制台输出
- 成功启动的绿色勾选标记
- 关闭程序的黄色警告
- 失败的红色错误消息
- 所有 WHOIS 数据的结构化 JSON 响应

### 信号处理
- SIGINT（Ctrl+C）和 SIGTERM 的优雅关闭
- 传输连接的正确清理
- 用户友好的关闭消息

## ⚠️ 重要提示

### 速率限制
- WHOIS 服务器有速率限制以防止滥用
- 避免过于频繁的连续查询
- 某些服务器可能暂时阻止过度请求

### 数据准确性
- WHOIS 数据准确性取决于注册商合规性
- 某些域名可能启用了隐私保护
- 历史数据可能不总是可用

### 法律考虑
- WHOIS 数据受各种隐私法律和法规约束
- 负责任地使用数据并遵守适用法律
- 尊重注册商服务条款和速率限制

## 🚀 常见用例

### 网络安全
- **威胁情报**: 调查可疑域名和 IP 地址
- **事件响应**: 收集恶意基础设施信息
- **域名监控**: 跟踪域名注册变化

### 网络管理
- **IP 管理**: 验证 IP 地址所有权和分配
- **路由分析**: 了解 ASN 关系和网络路径
- **基础设施规划**: 研究网络提供商和 ASN 详情

### 商业智能
- **竞争研究**: 监控竞争对手域名注册
- **尽职调查**: 在合作前验证域名所有权
- **品牌保护**: 监控类似域名注册

### 开发和测试
- **API 集成**: 在应用中测试 WHOIS 功能
- **网络调试**: 排除连接和路由问题
- **教育目的**: 了解互联网基础设施

## 🤝 贡献

1. Fork 仓库
2. 创建功能分支：`git checkout -b feature-name`
3. 使用适当的 TypeScript 类型进行更改
4. 使用各种域名、IP、TLD 和 ASN 进行测试
5. 确保错误处理正常工作
6. 提交带有清晰描述的 pull request

### 开发指南

- 保持 TypeScript 严格模式合规
- 为新功能添加适当的错误处理
- 使用现有的颜色工具函数进行控制台输出
- 使用有效和无效输入进行测试
- 记录任何新参数或返回格式

## 📄 许可证

MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。

## ⚖️ 法律和隐私

- **数据来源**: WHOIS 数据从公共注册机构检索
- **隐私**: 某些 WHOIS 数据可能因隐私政策而被编辑
- **合规**: 用户必须遵守适用的隐私法律和法规
- **速率限制**: 尊重 WHOIS 服务器速率限制和服务条款
- **负责使用**: 仅将 WHOIS 数据用于合法目的

## 🙏 致谢

- **whoiser**: 优秀的 WHOIS 查询库
- **MCP 社区**: 标准化协议
- **互联网注册机构**: 维护公共 WHOIS 服务
- **贡献者**: 所有帮助改进这个项目的人

---

*为网络研究、安全分析和互联网基础设施理解而构建* 🔍🌐
