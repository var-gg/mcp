# Changelog

All notable changes to VARGG MCP will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial GitHub community setup
- Documentation structure
- Issue templates
- Discussion categories

## [1.0.0] - 2025-01-20

### Added
- **Project Management**
  - Create new projects with name, description, and visibility settings
  - List all accessible projects (including read-only)
  - Update project information (name, description, visibility)
  - Open project admin page for permissions and user invitations

- **Variable Management**
  - Search variables within projects by keyword (name/definition partial match)
  - Create new variables with SNAKE_CASE names and definitions
  - List all variables in a project with cursor-based pagination
  - Remove variables from projects (removes mapping, not the variable itself)

- **Cursor IDE Integration**
  - Full MCP protocol support
  - JSON-RPC 2.0 compliant endpoints
  - API key-based authentication
  - Automatic locale detection from MCP path

- **Multi-language Support**
  - Korean (ko) - 한글 + 영문 + 숫자 + 공백 + 괄호
  - English (en) - English letters + numbers + spaces
  - Japanese (ja) - ひら가나 + カタカナ + 漢字 + 영문 + 숫자
  - Chinese (zh) - 汉字 + 영문 + 숫자
  - Vietnamese (vi) - Vietnamese + 영문 + 숫자

- **Language-specific Validations**
  - Character set restrictions per language
  - Length limits per language (keyword: 2-32 chars, definition: 2-24 chars)
  - Pattern validation for variable names (SNAKE_CASE)
  - English keyword validation (noun phrases only, no verbs/auxiliaries/articles)

- **Permissions System**
  - Anonymous read access for public projects
  - Authentication required for write operations
  - Project-level permissions (read-only vs write/edit/delete)
  - Project owner and admin role support

### Technical Details

- **MCP Protocol Version**: 2024-11-05
- **Server Version**: 1.0.0
- **API Endpoint**: `/mcp/{locale}/project` (locale-specific JSON-RPC 2.0)
  - Example: `https://var.gg/mcp/ko/project` for Korean
  - Example: `https://var.gg/mcp/en/project` for English
  - Supported locales: `ko`, `en`, `ja`, `zh`, `vi`
- **Authentication**: API key via `X-API-KEY` header (required for App Engine, also supports `Authorization: Bearer <token>`)
- **Response Format**: JSON-RPC 2.0 format (JSON)

### Known Limitations

- Variable deletion removes project-variable mapping only, not the variable itself
- Project deletion is currently disabled for safety
- Some advanced features (variable usage tracking, bulk operations) are planned for future releases
- The following endpoints exist in the backend but are not exposed via MCP tools:
  - `/api/mcp/variables/register` - Variable registration to projects (deprecated)
  - `/api/mcp/variables/usage` - Variable usage tracking (deprecated)

---

[Unreleased]: https://github.com/var-gg/mcp/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/var-gg/mcp/releases/tag/v1.0.0

