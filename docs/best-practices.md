# Best Practices for VARGG MCP

Recommended workflows, patterns, and tips for effectively using VARGG MCP in your development workflow.

---

## 📋 Table of Contents

1. [Project Structure Design](#project-structure-design)
2. [Variable Naming Conventions](#variable-naming-conventions)
3. [Team Collaboration Workflows](#team-collaboration-workflows)
4. [Multilingual Project Management](#multilingual-project-management)
5. [Integration with AI Assistants](#integration-with-ai-assistants)
6. [Performance Optimization](#performance-optimization)

---

## 🏗️ Project Structure Design

### Organize by Domain or Module

**Recommended**: Create projects that align with your codebase structure.

**Example**:
```
E-Commerce Payment → payment/, checkout/, billing/ modules
E-Commerce Shipping → shipping/, delivery/, tracking/ modules
E-Commerce User → user/, account/, profile/ modules
```

**Benefits**:
- Easier to discover relevant variables
- Better separation of concerns
- Clearer ownership and permissions

### Project Naming Conventions

**Best Practices**:
- ✅ Use clear, descriptive names: "E-Commerce Payment", "Admin Dashboard"
- ✅ Include domain context: "Payment Processing", "User Authentication"
- ✅ Avoid overly generic names: "Project 1", "Test Project"
- ✅ Consider team visibility: Name should indicate project purpose

### Project Visibility

**When to Use Public Projects**:
- ✅ Standard terminology shared across teams
- ✅ Common abbreviations and definitions
- ✅ Reusable patterns across projects

**When to Use Private Projects**:
- ✅ Proprietary or sensitive terminology
- ✅ Project-specific conventions
- ✅ Experimental or temporary projects

---

## 📝 Variable Naming Conventions

### SNAKE_CASE Storage

VARGG MCP stores variables in **SNAKE_CASE** format. This is consistent across all projects and languages.

**Correct Format**:
- ✅ `TOTAL_COUNT`
- ✅ `USER_ACCOUNT_ID`
- ✅ `PAYMENT_AMOUNT`
- ✅ `MAX_RETRY_ATTEMPTS`

**Incorrect Format**:
- ❌ `totalCount` (should be `TOTAL_COUNT`)
- ❌ `PaymentAmount` (should be `PAYMENT_AMOUNT`)
- ❌ `user-account-id` (should be `USER_ACCOUNT_ID`)

### Code Conversion

In your generated code, convert SNAKE_CASE to your preferred convention:

**JavaScript/TypeScript (camelCase)**:
```typescript
// VARGG: TOTAL_COUNT
const totalCount = ...;

// VARGG: USER_ACCOUNT_ID
const userAccountId = ...;
```

**C#/Java (PascalCase)**:
```csharp
// VARGG: TOTAL_COUNT
int TotalCount = ...;

// VARGG: USER_ACCOUNT_ID
string UserAccountId = ...;
```

**Python (SNAKE_CASE)**:
```python
# VARGG: TOTAL_COUNT
total_count = ...

# VARGG: USER_ACCOUNT_ID
user_account_id = ...
```

### Definition Guidelines

**Good Definitions**:
- ✅ Clear and concise: "total count", "user account ID"
- ✅ Language-appropriate: Use your native language for definitions
- ✅ Consistent terminology: Use the same phrases across related variables

**Poor Definitions**:
- ❌ Too vague: "count", "ID"
- ❌ Too verbose: "this is the total count of all items in the collection"
- ❌ Inconsistent: "total count" vs "total number" vs "total quantity"

### Abbreviation vs Regular Variables

**Use Abbreviations For**:
- Common abbreviations: "API", "ID", "URL", "HTTP"
- Standard industry terms: "GDPR", "OAuth", "JWT"
- Team-specific abbreviations: "CRM", "ERP", "POS"

**Use Regular Variables For**:
- Full descriptive names: "payment amount", "user account"
- Domain-specific terms: "shipping address", "order status"
- Multi-word concepts: "maximum retry attempts"

---

## 👥 Team Collaboration Workflows

### Onboarding New Team Members

**Step 1**: Share your project
- Use `open_project_admin` tool to get invitation URL
- Invite team members through the web interface
- Grant appropriate permissions

**Step 2**: Share project context
- Point new members to your project's variable library
- Explain naming conventions in project description
- Share relevant documentation

**Step 3**: Set expectations
- Establish review process for new variables
- Define when to search vs. when to create
- Document team-specific conventions

### Code Review Integration

**Before Creating New Variables**:
1. Search existing variables first
2. Check if similar concept already exists
3. Reuse when possible, create only when necessary

**Variable Creation Checklist**:
- [ ] Searched existing variables
- [ ] Used correct SNAKE_CASE format
- [ ] Added clear, concise definition
- [ ] Categorized as abbreviation or regular
- [ ] Followed team naming conventions

### Permission Management

**Recommended Permissions Structure**:
- **Project Owners**: Full access (CREATE, UPDATE, DELETE)
- **Core Contributors**: Write access (CREATE, UPDATE)
- **Team Members**: Read-only for discovery
- **External Collaborators**: Specific project access only

**Best Practice**: Start with read-only access, grant write access as needed.

---

## 🌐 Multilingual Project Management

### Language Selection Strategy

**Option 1: Single Language Per Project**
- One project per language
- Example: "Payment (Korean)", "Payment (English)"
- ✅ Clear separation
- ❌ Duplication of concepts

**Option 2: Multi-language Definitions**
- One project with variables in one language, definitions in multiple languages
- Example: `PAYMENT_AMOUNT` with definitions in ko, en, ja, zh, vi
- ✅ Centralized management
- ❌ Current VARGG MCP stores one definition per variable

**Recommended**: Use separate projects per language for now, consolidate later if multi-language definitions are supported.

### Definition Language Guidelines

**Use Native Language for Definitions**:
- Korean projects: Use Korean definitions
- English projects: Use English definitions
- Mixed teams: Use team's primary working language

**Variable Names Always in English**:
- Even for non-English projects, use English variable names
- Example: Korean project with `TOTAL_COUNT` and definition "전체 개수"

### Cross-Language Consistency

**Maintain Consistent Variable Names**:
- Use same English variable names across language projects
- Example: Both Korean and English projects use `PAYMENT_AMOUNT`
- Only definitions differ: "결제 금액" vs "payment amount"

---

## 🤖 Integration with AI Assistants

### Prompt Engineering for VARGG MCP

**Best Practice**: Always search before creating

```
Search for variables related to "user authentication" in project proj_123
```

**If found**: Use existing variable
**If not found**: Create new variable

### Context-Aware Generation

**Provide Project Context**:
```
I'm working on the "E-Commerce Payment" project. 
When generating code, use variables from this project's standard terminology.
```

**Search and Suggest Pattern**:
```
Search for variables related to "payment" in project proj_123, 
then generate payment processing code using those variables.
```

### Variable Discovery

**Regular Discovery Sessions**:
- Periodically list all variables in your project
- Review and clean up unused or duplicate variables
- Document common patterns

**Use Search Effectively**:
- Start with specific keywords
- Broaden search if needed
- Use project-specific context

---

## ⚡ Performance Optimization

### Efficient Searching

**Be Specific**:
- ✅ `"user account"` instead of `"user"`
- ✅ `"payment amount"` instead of `"amount"`
- ✅ `"shipping address"` instead of `"address"`

**Use Project Scope**:
- Always specify `projectId` for project-scoped searches
- Avoid global searches when project context is available

### Pagination Best Practices

**For Large Projects**:
- Use `limit` parameter (default 100, max 100)
- Fetch pages incrementally as needed
- Don't fetch all variables at once if project is large

**Example**:
```
List first 50 variables in project proj_123
[If has_next: true, fetch next page]
List variables in project proj_123 starting from cursor pd_456
```

### Caching Strategy

**Cache Frequently Used Variables**:
- Store commonly used variables locally
- Update cache when variables change
- Invalidate cache on project updates

### Batch Operations

**Minimize API Calls**:
- Search once, use results multiple times
- List variables once per session if possible
- Batch creates/deletes when appropriate

---

## 🎯 Common Patterns and Workflows

### Pattern 1: New Feature Development

```
1. Create/identify project: "Feature: User Authentication"
2. Search for existing related variables
3. Create missing variables as needed
4. Use variables in code generation
5. Document new patterns for team
```

### Pattern 2: Refactoring Existing Code

```
1. List variables in project
2. Identify variables to update/remove
3. Search for variable usage (if supported)
4. Update variable definitions
5. Remove obsolete variables
```

### Pattern 3: Team Standardization

```
1. Review existing codebase for naming patterns
2. Extract common variables to project
3. Share project with team
4. Gradually migrate code to use standard variables
5. Enforce via code review
```

### Pattern 4: Multilingual Support

```
1. Create project per language: "Payment (Korean)", "Payment (English)"
2. Use consistent variable names across projects
3. Localize definitions per language
4. Cross-reference projects for consistency
```

---

## ⚠️ Common Pitfalls to Avoid

### ❌ Creating Duplicate Variables

**Problem**: Multiple variables for the same concept
- `TOTAL_COUNT`, `TOTAL_NUMBER`, `TOTAL_QUANTITY`

**Solution**: 
- Always search before creating
- Review project variables regularly
- Remove duplicates and consolidate

### ❌ Inconsistent Naming

**Problem**: Mixing naming conventions
- `paymentAmount`, `PAYMENT_AMOUNT`, `Payment_Amount`

**Solution**:
- Always use SNAKE_CASE in VARGG
- Convert in code generation
- Document conversion rules for team

### ❌ Too Generic Definitions

**Problem**: Vague definitions
- Definition: "count" (what count?)
- Definition: "ID" (what ID?)

**Solution**:
- Be specific: "total item count", "user account ID"
- Include context: "payment amount in USD"
- Use full phrases: "maximum retry attempts"

### ❌ Ignoring Project Structure

**Problem**: One large project for everything
- Project: "All Variables" with 1000+ variables

**Solution**:
- Split by domain/module
- Create focused projects
- Use public projects for shared standards

---

## 📊 Project Health Metrics

### Regular Maintenance

**Weekly**:
- Review new variables added
- Check for duplicates or conflicts

**Monthly**:
- Audit variable definitions for clarity
- Remove unused or obsolete variables
- Update project descriptions

**Quarterly**:
- Review project structure
- Consolidate related projects
- Archive completed projects

### Quality Indicators

**Healthy Project**:
- ✅ Clear, descriptive variable names
- ✅ Consistent naming patterns
- ✅ Well-documented definitions
- ✅ Active team usage
- ✅ Regular updates

**Needs Attention**:
- ⚠️ Many duplicate variables
- ⚠️ Vague or inconsistent definitions
- ⚠️ Low usage or stale variables
- ⚠️ Missing project description

---

## 🔗 Related Documentation

- [Getting Started](getting-started.md) - Initial setup
- [Tools Reference](tools-reference.md) - API documentation
- [Integration Guide](integration-guide.md) - Cursor IDE setup
- [Use Cases](../examples/use-cases.md) - Real-world examples

---

**Remember**: VARGG MCP is a tool to help maintain consistency. The best practices evolve with your team's needs. Start simple, iterate based on feedback, and don't over-engineer!

---

**Last Updated**: 2025-01-20

