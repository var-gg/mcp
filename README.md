# VARGG MCP

[![MCP Protocol](https://img.shields.io/badge/MCP-Protocol-blue)](https://modelcontextprotocol.io)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Discussions](https://img.shields.io/badge/discussions-welcome-blue)](https://github.com/var-gg/mcp/discussions)

> **Project metadata management tool through Model Context Protocol**

Manage variable names, constants, and standard terminology per project systematically, and integrate with Cursor IDE to help LLMs use consistent naming conventions.

---

## 🎯 Overview

VARGG MCP is a Model Context Protocol implementation that enables seamless integration between your development environment and a centralized project metadata management system. It helps teams maintain consistent naming conventions across projects, especially when working with AI assistants like Cursor IDE.

### Problems It Solves

- **Inconsistent Naming**: Different developers use different variable names for the same concepts
- **Language Barriers**: Teams working in multiple languages struggle with terminology consistency
- **AI Context Loss**: LLMs generate code without knowledge of your team's established conventions
- **Knowledge Silos**: Project-specific naming patterns aren't shared or discoverable
- **Onboarding Friction**: New team members don't know what naming conventions to follow

### Key Features Summary

- **Project-based Organization**: Manage variables and constants per project
- **Multi-language Support**: Native support for Korean, English, Japanese, Chinese, and Vietnamese
- **Cursor IDE Integration**: Direct integration with Cursor IDE through MCP protocol
- **Real-time Search**: Search for existing variables and definitions instantly
- **Standard Terminology**: Maintain consistent definitions across projects
- **Team Collaboration**: Share and discover naming patterns within teams

### Target Users

- **Development Teams**: Teams that want to maintain consistent naming conventions
- **Multi-language Projects**: Projects involving multiple languages and locales
- **AI-Assisted Development**: Developers using Cursor IDE or similar AI coding assistants
- **Project Managers**: Teams managing standardized terminology across projects

---

## ✨ Key Features

### 🗂️ Project-based Variable Management
Organize variables and constants by project, making it easy to maintain project-specific naming conventions while sharing common patterns across teams.

### 🌐 Multi-language Support
Full support for 5 languages:
- 🇰🇷 Korean (ko)
- 🇺🇸 English (en)
- 🇯🇵 Japanese (ja)
- 🇨🇳 Chinese (zh)
- 🇻🇳 Vietnamese (vi)

Each language has its own validation rules and character sets for variable names and definitions.

### 🔌 Cursor IDE Integration
Seamless integration with Cursor IDE through the Model Context Protocol. LLMs can automatically search for and use your team's standard terminology when generating code.

### 🔍 Automatic Standard Terminology Search and Suggestions
When LLMs generate code, they can search your project's variable library and suggest existing standard terms instead of creating new ones.

### ⚡ Real-time Variable Search and Registration
Search for existing variables instantly and register new ones as you work. All operations are performed in real-time through the MCP protocol.

---

## 🚀 Quick Start

### Prerequisites

- Cursor IDE installed
- VARGG account (create one at [var.gg](https://var.gg))
- API key from VARGG website

### 1. Get Your API Key

1. Visit [var.gg](https://var.gg) and sign in
2. Navigate to your account settings
3. Generate an API key for MCP access

### 2. Configure Cursor IDE

Add VARGG MCP to your Cursor IDE settings:

**File (F) > Preferences > Cursor Settings**

Add the following configuration:

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/api/mcp",
      "headers": {
        "API_KEY": "your-api-key-here"
      }
    }
  }
}
```

Replace `your-api-key-here` with your actual API key from step 1.

### 3. Create Your First Project

In Cursor IDE, ask the AI assistant:

```
Create a new project named "E-Commerce Payment" with description "Payment processing module for e-commerce platform"
```

Or use the web interface at [var.gg/projects](https://var.gg/projects).

### 4. Start Using Variables

Ask Cursor to search for or create variables:

```
Search for variables related to "user account" in the project
```

```
Create a variable TOTAL_COUNT with definition "total count" for abbreviation in the project
```

---

## 🛠️ Available Tools

VARGG MCP provides the following tools for managing projects and variables:

### Project Management
- **`projects`** - List all projects accessible to you
- **`create_project`** - Create a new project
- **`update_project`** - Update project information
- **`open_project_admin`** - Open project admin page for permissions and user invitations

### Variable Management
- **`search_variables`** - Search for variables within a project
- **`create_variables`** - Create new variables in a project
- **`list_variables`** - List all variables in a project (paginated)
- **`remove_variables`** - Remove variables from a project

For detailed documentation on each tool, see [Tools Reference](docs/tools-reference.md).

---

## 📖 Documentation

- **[Getting Started](docs/getting-started.md)** - Detailed setup guide
- **[Tools Reference](docs/tools-reference.md)** - Complete API documentation for all tools
- **[Cursor Integration Guide](docs/integration-guide.md)** - Step-by-step Cursor IDE setup
- **[Best Practices](docs/best-practices.md)** - Recommended workflows and patterns
- **[Use Cases](examples/use-cases.md)** - Real-world examples and scenarios
- **[Official Website](https://var.gg)** - Interactive demo and detailed guides

---

## 💡 Use Cases

### Unifying Naming Conventions Within Teams
Ensure all team members use the same variable names for common concepts. For example, always use `USER_ACCOUNT` instead of mixing `UserAccount`, `userAccount`, `user_account`, etc.

### Managing Standard Terminology Per Project
Each project can have its own set of standard terms. A "Payment" project might have `PAYMENT_AMOUNT`, while a "Shipping" project might have `SHIPPING_COST`.

### Ensuring Consistency in LLM Code Generation
When you ask Cursor to generate code, it searches your project's variable library and uses existing standard terms, maintaining consistency across all generated code.

### Managing Variable Names in Multilingual Projects
Support for multiple languages means you can define variables in your native language while maintaining English variable names for code. For example, `TOTAL_COUNT` with a Korean definition "전체 개수".

---

## 🤝 Community

- **[Issues](https://github.com/var-gg/mcp/issues)**: Report bugs, suggest features, ask questions
- **[Discussions](https://github.com/var-gg/mcp/discussions)**: Share tips, Q&A, discuss ideas
- **Roadmap**: See planned features and improvements (check issue labels)

### How to Contribute

1. Share your use cases in [Discussions](https://github.com/var-gg/mcp/discussions)
2. Report bugs or request features via [Issues](https://github.com/var-gg/mcp/issues)
3. Share best practices in the "Show and Tell" category

---

## 🌐 Multi-language Support

VARGG MCP supports the following languages with native validation and character sets:

| Language | Code | Character Set |
|----------|------|---------------|
| 🇰🇷 Korean | `ko` | 한글 + 영문 + 숫자 + 공백 + 괄호 |
| 🇺🇸 English | `en` | English letters + numbers + spaces |
| 🇯🇵 Japanese | `ja` | ひらがな + カタカナ + 漢字 + 영문 + 숫자 |
| 🇨🇳 Chinese | `zh` | 汉字 + 영문 + 숫자 |
| 🇻🇳 Vietnamese | `vi` | Vietnamese + 영문 + 숫자 |

Each language has specific validation rules for variable names and definitions. See [Tools Reference](docs/tools-reference.md) for details.

---

## 🔗 Links

- **Website**: [https://var.gg](https://var.gg)
- **MCP Guide**: [https://var.gg/en/mcp](https://var.gg/en/mcp) (also available in ko, ja, zh, vi)
- **Interactive Demo**: [https://var.gg/[locale]/mcp](https://var.gg/en/mcp) - Try the tools in your browser
- **Issue Reports**: [https://github.com/var-gg/mcp/issues](https://github.com/var-gg/mcp/issues)
- **Discussions**: [https://github.com/var-gg/mcp/discussions](https://github.com/var-gg/mcp/discussions)

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## ⚠️ Important Notes

### Code Publication
Currently, this repository contains documentation and community resources only. The MCP server implementation code is not yet open source, but we may publish it in the future. Check back for updates!

### Version Management
Even though the code is not published, we track MCP tool versions and feature changes in [CHANGELOG.md](CHANGELOG.md).

### Privacy
When reporting issues or discussing features, please avoid sharing personal information or API keys. If you need to share sensitive information, contact us privately.

---

**Made with ❤️ by the VARGG team**

