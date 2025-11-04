# VARGG MCP Tools Reference

Complete API documentation for all VARGG MCP tools.

---

## 📋 Table of Contents

1. [Project Management Tools](#project-management-tools)
2. [Variable Management Tools](#variable-management-tools)
3. [Common Patterns](#common-patterns)
4. [Error Handling](#error-handling)

---

## 🗂️ Project Management Tools

### `projects` - List Projects

List all projects accessible to the user (including read-only projects).

**Authentication**: Required (but can work with valid API key)

**Parameters**: None

**Response Format**:
```json
{
  "projects": [
    {
      "id": "proj_123",
      "name": "E-Commerce Payment",
      "description": "Payment processing module",
      "is_public": true,
      "language": "en",
      "permissions": ["CREATE", "UPDATE", "DELETE"]
    },
    {
      "id": "proj_456",
      "name": "Internal Tools",
      "description": "Internal development tools",
      "is_public": false,
      "language": "ko",
      "permissions": []
    }
  ]
}
```

**Permission Interpretation**:
- `permissions: []` = Read-only access
- `permissions: ["CREATE", ...]` = Write/edit/delete access

**Example Usage**:
```
List my projects
```

---

### `create_project` - Create Project

Create a new project with specified name and description.

**Authentication**: Required

**Parameters**:
- `projectName` (string, required): Project name (min 1, max 200 characters)
- `description` (string, required): Project description (min 1 character)
- `isPublic` (boolean, optional): Public visibility (default: true)

**Language**: Automatically detected from MCP path locale (`/mcp/{locale}/project`)

**Response Format**:
```json
{
  "id": "proj_789",
  "name": "E-Commerce Payment",
  "description": "Payment processing module for e-commerce platform",
  "is_public": true,
  "language": "en",
  "created_at": "2025-01-20T10:00:00Z"
}
```

**Example Usage**:
```
Create a new project named "E-Commerce Payment" with description "Payment processing module for e-commerce platform"
```

---

### `update_project` - Update Project

Update project information (name, description, or visibility).

**Authentication**: Required (project owner or UPDATE permission)

**Parameters**:
- `projectId` (string, required): Project ID
- `projectName` (string, optional): Project name (min 1, max 200 characters)
- `description` (string, optional): Project description (min 1 character)
- `isPublic` (boolean, optional): Public visibility

**Note**: Include only fields you want to update. All update fields are optional.

**Language**: Automatically detected from MCP path locale (`/mcp/{locale}/project`)

**Response Format**:
```json
{
  "id": "proj_123",
  "name": "Updated Project Name",
  "description": "Updated description",
  "is_public": false,
  "language": "en",
  "updated_at": "2025-01-20T11:00:00Z"
}
```

**Example Usage**:
```
Update project proj_123 with description "New description for the project"
```

---

### `open_project_admin` - Open Project Admin Page

Returns a URL to open the project admin page for permissions management or user invitations.

**Authentication**: Required (project owner or admin)

**Parameters**:
- `projectId` (string, required): Project ID
- `action` (string, required): Either `"permission"` or `"invite"`

**Response Format**:
```json
{
  "url": "https://var.gg/en/projects/proj_123",
  "action": "permission",
  "actionDescription": "Permission Management",
  "message": {
    "en": "Please open the following URL in a web browser for Permission Management: https://var.gg/en/projects/proj_123",
    "ko": "권한 관리를 위해 다음 URL을 웹 브라우저에서 열어주세요: https://var.gg/ko/projects/proj_123"
  }
}
```

**Note**: This tool returns a URL that must be opened in a web browser. Email dispatch is not automatic - invited users receive notifications on the web and must accept invitations. Initial permissions are read-only until an administrator grants separate permissions.

**Example Usage**:
```
Open project admin page for project proj_123 with action "invite"
```

---

## 🔍 Variable Management Tools

### `search_variables` - Search Variables

Search for variables within a project by keyword (partial match on name or definition).

**Authentication**: Required (but accessible with valid API key for public projects)

**Parameters**:
- `keyword` (string, required): Search keyword
  - **Korean (ko)**: 2-15 chars, 한글+영문+숫자+공백+괄호()
  - **English (en)**: 2-32 chars, English letters+numbers+spaces, noun phrases only (avoid verbs, auxiliaries, articles at start)
  - **Japanese (ja)**: 2-18 chars, ひらがな+カタカナ+漢字+영문+숫자
  - **Chinese (zh)**: 2-12 chars, 汉字+영문+숫자
  - **Vietnamese (vi)**: 2-24 chars, Vietnamese+영문+숫자
  - **Common**: No consecutive 5+ digits
- `projectId` (string, required): Project ID
- `locale` (string, optional): Language code (ko, en, ja, zh, vi) - defaults to MCP path locale

**Response Format**:
```json
{
  "variables": [
    {
      "project_detail_id": "pd_123",
      "variableName": "TOTAL_COUNT",
      "definition": "total count",
      "isAbbreviation": false,
      "project_id": "proj_123"
    }
  ]
}
```

**Important**: 
- `variableName` is returned in **SNAKE_CASE** (e.g., `TOTAL_COUNT`)
- Convert to camelCase, PascalCase, etc. in your code as needed
- `project_detail_id` is required for variable deletion

**Example Usage**:
```
Search for variables related to "user account" in project proj_123
```

**English Keyword Best Practices**:
✅ Good: `"user account"`, `"transaction history"`, `"scheduled collection amount"`  
❌ Bad: `"to check user"`, `"this is for appraisal"`, `"the payment amount"`

---

### `create_variables` - Create Variables

Create a new variable in a project.

**Authentication**: Required

**Parameters**:
- `projectId` (string, required): Project ID
- `variableName` (string, required): Variable name in SNAKE_CASE (e.g., `TOTAL_COUNT`)
  - Pattern: `^[A-Z][A-Z0-9_]*$`
  - Min: 1 char, Max: 100 chars
- `definition` (string, required): Variable definition
  - **Korean (ko)**: 2-15 chars, 한글+영문+숫자+공백
  - **English (en)**: 2-24 chars, English letters+numbers+spaces
  - **Japanese (ja)**: 2-18 chars, ひらがな+カタカナ+漢字+영문+숫자
  - **Chinese (zh)**: 2-12 chars, 汉字+영문+숫자
  - **Vietnamese (vi)**: 2-24 chars, Vietnamese+영문+숫자
- `isAbbreviation` (boolean, required): Whether this is an abbreviation

**Language**: Automatically detected from MCP path locale (`/mcp/{locale}/project`)

**Response Format**:
```json
{
  "project_detail_id": "pd_456",
  "variableName": "PAYMENT_AMOUNT",
  "definition": "payment amount",
  "isAbbreviation": false,
  "project_id": "proj_123"
}
```

**Note**: If a variable was previously deleted from the project, it will be automatically restored.

**Example Usage**:
```
Create variable PAYMENT_AMOUNT with definition "payment amount" for abbreviation in project proj_123
```

**Variable Name Format**:
- ✅ `TOTAL_COUNT`
- ✅ `USER_ACCOUNT_ID`
- ✅ `PAYMENT_AMOUNT`
- ❌ `totalCount` (convert to SNAKE_CASE first)
- ❌ `PaymentAmount` (convert to SNAKE_CASE first)

---

### `list_variables` - List Variables

List all variables in a project with cursor-based pagination.

**Authentication**: Required (but accessible with valid API key for public projects)

**Parameters**:
- `projectId` (string, required): Project ID
- `cursor` (string, optional): Cursor for next page (last `project_detail_id` from previous response)
- `limit` (integer, optional): Number of items (default: 100, min: 1, max: 100)

**Response Format**:
```json
{
  "variables": [
    {
      "project_detail_id": "pd_123",
      "variableName": "TOTAL_COUNT",
      "definition": "total count",
      "isAbbreviation": false,
      "project_id": "proj_123"
    }
  ],
  "has_next": true,
  "next_cursor": "pd_123"
}
```

**Pagination**:
- Use `next_cursor` value as `cursor` parameter for next page
- `has_next: true` indicates more pages available
- `next_cursor` uses `project_detail_id` values

**Important**: 
- `variableName` is returned in **SNAKE_CASE**
- Convert to camelCase, PascalCase, etc. in your code as needed

**Example Usage**:
```
List all variables in project proj_123
```

**Fetching Next Page**:
```
List variables in project proj_123 starting from cursor pd_123
```

---

### `remove_variables` - Remove Variables

Remove a variable from a project (removes project-variable mapping, not the variable itself).

**Authentication**: Required (project owner or DELETE permission)

**Parameters**:
- `projectId` (string, required): Project ID
- `projectDetailId` (string, required): Project Detail ID (from search/list responses)

**Response Format**:
```json
{
  "success": true,
  "message": "Variable removed from project"
}
```

**Important Notes**:
- Only removes the project-variable mapping
- The variable itself remains in the system
- Other projects using the same variable are not affected
- To modify a variable, delete it first and re-register with new values

**Example Usage**:
```
Remove variable with project_detail_id pd_123 from project proj_123
```

---

## 🔄 Common Patterns

### Pattern 1: Search Then Create

If searching doesn't find what you need, create it:

```
Search for variables related to "payment processing" in project proj_123
[If not found:]
Create variable PAYMENT_PROCESSING with definition "payment processing" for abbreviation in project proj_123
```

### Pattern 2: List Then Filter

For projects with many variables, list and filter:

```
List all variables in project proj_123
[Then filter or search the results]
```

### Pattern 3: Batch Operations

To work with multiple variables:

```
1. List variables in project proj_123
2. For each variable that needs updating:
   - Remove the variable (remove_variables)
   - Create with new definition (create_variables)
```

---

## ⚠️ Error Handling

### Common Errors

#### Authentication Required
```json
{
  "error": "Authentication required",
  "code": "AUTH_REQUIRED"
}
```
**Solution**: Verify API key is set correctly in Cursor configuration.

#### Project Not Found
```json
{
  "error": "Project not found",
  "code": "PROJECT_NOT_FOUND"
}
```
**Solution**: Verify project ID is correct. List projects first to get valid IDs.

#### Invalid Parameter
```json
{
  "error": "Parameter validation failed: 'keyword' is invalid",
  "code": "VALIDATION_ERROR"
}
```
**Solution**: Check parameter requirements and validation rules per language.

#### Permission Denied
```json
{
  "error": "Permission denied",
  "code": "PERMISSION_DENIED"
}
```
**Solution**: Verify you have the required permissions for the operation.

---

## 📝 Notes

### Variable Name Convention

VARGG MCP stores variables in **SNAKE_CASE** format:
- Database storage: `TOTAL_COUNT`
- Your code can use: `totalCount` (camelCase) or `TotalCount` (PascalCase)
- Conversion is your responsibility in generated code

### Language Detection

Language (`locale`) is automatically detected from the MCP endpoint path `/mcp/{locale}/project`:
- `/mcp/ko/project` → Korean (locale: "ko")
- `/mcp/en/project` → English (locale: "en")
- `/mcp/ja/project` → Japanese (locale: "ja")
- `/mcp/zh/project` → Chinese (locale: "zh")
- `/mcp/vi/project` → Vietnamese (locale: "vi")

**Note**: Some tools require explicit `locale` parameter even when using locale-specific endpoints, while others automatically use the endpoint locale.

### Pagination

For large projects:
- Use `list_variables` with pagination (`limit`, `cursor`)
- Use `search_variables` for targeted searches
- Avoid fetching all variables at once if the project is large

---

## 🔗 Related Documentation

- [Getting Started](getting-started.md) - Initial setup
- [Integration Guide](integration-guide.md) - Cursor IDE configuration
- [Best Practices](best-practices.md) - Recommended workflows
- [Use Cases](../examples/use-cases.md) - Real-world examples

---

**Last Updated**: 2025-01-20

