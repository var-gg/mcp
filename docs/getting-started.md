# Getting Started with VARGG MCP

This guide will walk you through setting up VARGG MCP with Cursor IDE and creating your first project.

---

## 📋 Prerequisites

Before you begin, ensure you have:

- **Cursor IDE** installed ([download here](https://cursor.sh))
- **VARGG Account** - Sign up at [var.gg](https://var.gg) if you don't have one
- **API Key** - You'll generate this in the setup process below

---

## 🚀 Step 1: Create Your VARGG Account

1. Visit [https://var.gg](https://var.gg)
2. Sign up for a new account (or sign in if you already have one)
3. Complete your profile setup

---

## 🔑 Step 2: Generate Your API Key

1. After signing in, navigate to your account settings
2. Look for the "API Keys" or "MCP Settings" section
3. Click "Generate New API Key"
4. **Important**: Copy and securely store your API key - you won't be able to see it again!

   > 💡 **Security Tip**: Treat your API key like a password. Never share it publicly or commit it to version control.

---

## ⚙️ Step 3: Configure Cursor IDE

### 3.1 Open Cursor Settings

In Cursor IDE:
- **Windows/Linux**: `File (F) > Preferences > Cursor Settings`
- **macOS**: `Cursor > Preferences > Cursor Settings`

Or use the keyboard shortcut:
- **Windows/Linux**: `Ctrl + ,`
- **macOS**: `Cmd + ,`

### 3.2 Add MCP Server Configuration

1. In the settings, search for "MCP" or "Model Context Protocol"
2. Look for the "MCP Servers" section
3. Click "Add Server" or edit the JSON configuration directly

### 3.3 Enter VARGG MCP Configuration

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

**Replace `your-api-key-here` with your actual API key from Step 2.**

### 3.4 Save and Restart

1. Save the configuration
2. Restart Cursor IDE to apply the changes
3. Verify the connection by checking Cursor's MCP status indicator

---

## 📁 Step 4: Create Your First Project

### Option A: Using Cursor IDE (Recommended)

Open Cursor's chat and ask:

```
Create a new project named "E-Commerce Payment" with description "Payment processing module for e-commerce platform"
```

The AI assistant will use the `create_project` tool to set up your project.

### Option B: Using Web Interface

1. Visit [https://var.gg/projects](https://var.gg/projects)
2. Click "Create New Project"
3. Fill in:
   - **Project Name**: e.g., "E-Commerce Payment"
   - **Description**: e.g., "Payment processing module for e-commerce platform"
   - **Visibility**: Public or Private
4. Click "Create"

---

## 🎯 Step 5: Add Your First Variables

Now that you have a project, let's add some standard variables.

### Example: Creating Variables for Payment System

In Cursor IDE, try these commands:

```
Search for variables related to "payment amount" in the project
```

If no results, create one:

```
Create a variable PAYMENT_AMOUNT with definition "payment amount" for abbreviation in the project
```

Or for a regular variable:

```
Create a variable TOTAL_COUNT with definition "total count" as a regular variable (not abbreviation) in the project
```

### Variable Naming Convention

VARGG MCP uses **SNAKE_CASE** for variable names:
- ✅ `PAYMENT_AMOUNT`
- ✅ `TOTAL_COUNT`
- ✅ `USER_ACCOUNT_ID`
- ❌ `paymentAmount` (use camelCase in your code, but store as SNAKE_CASE)
- ❌ `PaymentAmount` (use PascalCase in your code, but store as SNAKE_CASE)

The definitions can be in your preferred language, but variable names should be in English.

---

## 🔍 Step 6: Search and Use Variables

Once you have variables in your project, you can search for them:

```
Search for variables containing "user" in the project
```

The AI will find matching variables and can suggest using them in generated code.

---

## 📚 Next Steps

- Read the [Tools Reference](tools-reference.md) for detailed API documentation
- Check out [Best Practices](best-practices.md) for recommended workflows
- Explore [Use Cases](../examples/use-cases.md) for real-world examples
- Visit the [Integration Guide](integration-guide.md) for advanced configuration

---

## ❓ Troubleshooting

### MCP Connection Issues

**Problem**: Cursor IDE shows "MCP server disconnected"

**Solutions**:
1. Verify your API key is correct (no extra spaces)
2. Check that the URL is `https://var.gg/api/mcp`
3. Ensure you're using the correct header name: `API_KEY`
4. Restart Cursor IDE
5. Check your internet connection

### API Key Not Working

**Problem**: Tools fail with "authentication required" error

**Solutions**:
1. Regenerate your API key from the website
2. Update the API key in Cursor settings
3. Restart Cursor IDE
4. Verify you're logged in at [var.gg](https://var.gg)

### Project Not Found

**Problem**: Cannot find your project when listing

**Solutions**:
1. Verify you're using the correct project ID
2. Check project visibility (private projects require authentication)
3. Ensure you have access permissions to the project

---

## 🆘 Need Help?

- Check [Issues](https://github.com/var-gg/mcp/issues) for known problems
- Ask questions in [Discussions](https://github.com/var-gg/mcp/discussions)
- Visit the [official website](https://var.gg) for support

---

**Congratulations!** You're now set up with VARGG MCP. Start managing your project's standard terminology and enjoy consistent naming conventions in your AI-generated code! 🎉

