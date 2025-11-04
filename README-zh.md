# VARGG MCP

[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Discussions](https://img.shields.io/badge/discussions-welcome-blue)](https://github.com/var-gg/mcp/discussions)

**Languages / 语言 / 言語 / 언어 / Ngôn ngữ:**
- [![English](https://img.shields.io/badge/English-Click-yellow)](README.md)
- [![한국어](https://img.shields.io/badge/한국어-클릭-yellow)](README-ko.md)
- [![日本語](https://img.shields.io/badge/日本語-クリック-blue)](README-ja.md)
- [![简体中文](https://img.shields.io/badge/简体中文-点击查看-orange)](README-zh.md)
- [![Tiếng Việt](https://img.shields.io/badge/Tiếng_Việt-Nhấn_vào-green)](README-vi.md)

> **通过 Model Context Protocol 进行项目元数据管理工具**

系统地管理每个项目的变量名、常量和标准术语，并与 Cursor IDE 集成，帮助 LLM 使用一致的命名约定。

---

## 🎯 概述

VARGG MCP 是一个 Model Context Protocol 实现，可实现开发环境与集中式项目元数据管理系统之间的无缝集成。它帮助团队在项目间保持一致的命名约定，尤其是在使用 Cursor IDE 等 AI 助手时。

### 解决的问题

- **命名不一致**: 不同开发者为相同概念使用不同的变量名
- **语言障碍**: 使用多种语言工作的团队难以保持术语一致性
- **AI 上下文丢失**: LLM 在不知道团队已建立约定的情况下生成代码
- **知识孤岛**: 项目特定的命名模式未共享或无法被发现
- **入职困难**: 新团队成员不知道应遵循哪些命名约定

### 主要功能摘要

- **基于项目的组织**: 按项目管理变量和常量
- **多语言支持**: 原生支持韩语、英语、日语、中文和越南语
- **Cursor IDE 集成**: 通过 MCP 协议与 Cursor IDE 直接集成
- **实时搜索**: 即时搜索现有变量和定义
- **标准术语**: 在项目间保持一致的定义
- **团队协作**: 在团队内共享和发现命名模式

### 目标用户

- **开发团队**: 希望保持一致命名约定的团队
- **多语言项目**: 涉及多种语言和地区的项目
- **AI 辅助开发**: 使用 Cursor IDE 或类似 AI 编码助手的开发者
- **项目经理**: 在项目间管理标准化术语的团队

---

## ✨ 主要功能

### 🗂️ 基于项目的变量管理
按项目组织变量和常量，便于维护项目特定的命名约定，同时在团队间共享通用模式。

### 🌐 多语言支持
完全支持 5 种语言:
- 🇰🇷 韩语 (ko)
- 🇺🇸 英语 (en)
- 🇯🇵 日语 (ja)
- 🇨🇳 中文 (zh)
- 🇻🇳 越南语 (vi)

每种语言都有其自己的变量名和定义验证规则和字符集。

### 🔌 Cursor IDE 集成
通过 Model Context Protocol 与 Cursor IDE 无缝集成。LLM 在生成代码时可以自动搜索并使用您团队的标准术语。

### 🔍 自动标准术语搜索和建议
当 LLM 生成代码时，它们可以搜索您项目的变量库，并建议使用现有标准术语，而不是创建新术语。

### ⚡ 实时变量搜索和注册
即时搜索现有变量，并在工作时注册新变量。所有操作都通过 MCP 协议实时执行。

---

## 🚀 快速开始

### 先决条件

- 已安装 Cursor IDE
- VARGG 账户 ([var.gg](https://var.gg) 创建)
- VARGG 网站上的 API 密钥

### 1. 获取您的 API 密钥

1. 访问 [var.gg](https://var.gg) 并登录
2. 导航到您的账户设置
3. 生成用于 MCP 访问的 API 密钥

### 2. 配置 Cursor IDE

在 Cursor IDE 设置中添加 VARGG MCP:

**文件(F) > 首选项 > Cursor 设置**

添加以下配置:

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/mcp/zh/project",
      "headers": {
        "X-API-KEY": "your-api-key-here"
      }
    }
  }
}
```

**注意**: 将 `zh` 替换为您首选的区域设置(`en`, `ko`, `ja`, `vi`)。

将 `your-api-key-here` 替换为步骤 1 中获取的实际 API 密钥。

### 3. 创建您的第一个项目

在 Cursor IDE 中，询问 AI 助手:

```
创建一个名为 "E-Commerce Payment" 的新项目，描述为 "电子商务平台的支付处理模块"
```

或使用 [var.gg/projects](https://var.gg/projects) 上的 Web 界面。

### 4. 开始使用变量

要求 Cursor 搜索或创建变量:

```
在项目中搜索与 "用户账户" 相关的变量
```

```
在项目中创建一个变量 TOTAL_COUNT，定义为 "total count"，作为缩写
```

---

## 🛠️ 可用工具

VARGG MCP 提供以下工具来管理项目和变量:

### 项目管理
- **`projects`** - 列出您可访问的所有项目
- **`create_project`** - 创建新项目
- **`update_project`** - 更新项目信息
- **`open_project_admin`** - 打开项目管理页面以进行权限和用户邀请

### 变量管理
- **`search_variables`** - 在项目内搜索变量
- **`create_variables`** - 在项目中创建新变量
- **`list_variables`** - 列出项目中的所有变量（分页）
- **`remove_variables`** - 从项目中删除变量

有关每个工具的详细文档，请参阅 [工具参考](docs/tools-reference.md)。

---

## 📖 文档

- **[入门指南](docs/getting-started.md)** - 详细设置指南
- **[工具参考](docs/tools-reference.md)** - 所有工具的完整 API 文档
- **[Cursor 集成指南](docs/integration-guide.md)** - 分步 Cursor IDE 设置
- **[最佳实践](docs/best-practices.md)** - 推荐工作流和模式
- **[使用案例](examples/use-cases.md)** - 实际示例和场景
- **[官方网站](https://var.gg)** - 交互式演示和详细指南

---

## 💡 使用案例

### 统一团队内的命名约定
确保所有团队成员对共同概念使用相同的变量名。例如，始终使用 `USER_ACCOUNT`，而不是混合使用 `UserAccount`、`userAccount`、`user_account` 等。

### 按项目管理标准术语
每个项目可以有自己的标准术语集。"Payment" 项目可能有 `PAYMENT_AMOUNT`，而 "Shipping" 项目可能有 `SHIPPING_COST`。

### 确保 LLM 代码生成的一致性
当您要求 Cursor 生成代码时，它会搜索您项目的变量库并使用现有标准术语，在所有生成的代码中保持一致性。

### 管理多语言项目中的变量名
多语言支持意味着您可以用母语定义变量，同时保持代码的英语变量名。例如，带有中文定义 "总数" 的 `TOTAL_COUNT`。

---

## 🤝 社区

- **[Issues](https://github.com/var-gg/mcp/issues)**: 报告错误、建议功能、提问
- **[Discussions](https://github.com/var-gg/mcp/discussions)**: 分享技巧、问答、讨论想法
- **路线图**: 查看计划的功能和改进（检查问题标签）

### 如何贡献

1. 在 [Discussions](https://github.com/var-gg/mcp/discussions) 中分享您的使用案例
2. 通过 [Issues](https://github.com/var-gg/mcp/issues) 报告错误或请求功能
3. 在 "Show and Tell" 类别中分享最佳实践

---

## 🌐 多语言支持

VARGG MCP 支持以下具有原生验证和字符集的语言:

| Language | Code | Character Set |
|----------|------|---------------|
| 🇰🇷 韩语 | `ko` | 한글 + 영문 + 숫자 + 공백 + 괄호 |
| 🇺🇸 英语 | `en` | English letters + numbers + spaces |
| 🇯🇵 日语 | `ja` | ひらがな + カタカナ + 漢字 + 영문 + 숫자 |
| 🇨🇳 中文 | `zh` | 汉字 + 영문 + 숫자 |
| 🇻🇳 越南语 | `vi` | Vietnamese + 영문 + 숫자 |

每种语言都有变量名和定义的特定验证规则。有关详细信息，请参阅 [工具参考](docs/tools-reference.md)。

---

## 🔗 链接

- **网站**: [https://var.gg](https://var.gg)
- **MCP 指南**: [https://var.gg/zh/mcp](https://var.gg/zh/mcp) (en, ko, ja, vi 也可用)
- **交互式演示**: [https://var.gg/[locale]/mcp](https://var.gg/zh/mcp) - 在浏览器中试用工具
- **问题报告**: [https://github.com/var-gg/mcp/issues](https://github.com/var-gg/mcp/issues)
- **讨论**: [https://github.com/var-gg/mcp/discussions](https://github.com/var-gg/mcp/discussions)

---

## 📝 许可证

本项目根据 MIT 许可证授权 - 详情请参阅 [LICENSE](LICENSE) 文件。

---

## ⚠️ 重要注意事项

### 代码发布

目前，此存储库仅包含文档和社区资源。MCP 服务器实现代码尚未开源，但我们将来可能会发布。请回来查看更新！

### 架构说明

VARGG MCP 实现使用 JSON-RPC 2.0 协议接口。Cursor IDE 使用 JSON-RPC 2.0 与 MCP 服务器通信，然后将其转换为对后端的 REST API 调用。前端充当 Cursor 的 MCP 协议和后端 REST API 之间的代理层。

### 版本管理

即使代码未发布，我们也会在 [CHANGELOG.md](CHANGELOG.md) 中跟踪 MCP 工具版本和功能更改。

### 隐私

报告问题或讨论功能时，请避免分享个人信息或 API 密钥。如果您需要分享敏感信息，请私下联系我们。

---

**由 VARGG 团队用 ❤️ 制作**

