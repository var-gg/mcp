# Cursor IDE Integration Guide

Complete guide to integrating VARGG MCP with Cursor IDE, including advanced configuration and troubleshooting.

---

## 📋 Table of Contents

1. [Basic Setup](#basic-setup)
2. [Advanced Configuration](#advanced-configuration)
3. [Network Configuration](#network-configuration)
4. [API Key Management](#api-key-management)
5. [Troubleshooting](#troubleshooting)
6. [Security Best Practices](#security-best-practices)

---

## 🔧 Basic Setup

### Step 1: Locate Cursor Settings

The path to Cursor settings depends on your platform:

| Platform | Path |
|----------|------|
| **Windows** | `File (F) > Preferences > Cursor Settings` |
| **macOS** | `Cursor > Preferences > Cursor Settings` |
| **Linux** | `File (F) > Preferences > Cursor Settings` |

**Keyboard Shortcut**: 
- Windows/Linux: `Ctrl + ,`
- macOS: `Cmd + ,`

### Step 2: Access MCP Configuration

1. In Cursor settings, search for "MCP" or navigate to the MCP section
2. You'll see either:
   - A UI form to add MCP servers
   - A JSON editor for direct configuration

### Step 3: Add VARGG MCP Server

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

**Important**: Replace `your-api-key-here` with your actual API key.

### Step 4: Verify Connection

1. Save the configuration
2. Restart Cursor IDE
3. Open Cursor's chat panel
4. The MCP connection status should show as "Connected" or similar
5. Try a simple command: `List my projects`

---

## 🔐 Advanced Configuration

### Multiple API Keys

If you need to use different API keys for different projects or teams:

```json
{
  "mcpServers": {
    "vargg-production": {
      "url": "https://var.gg/api/mcp",
      "headers": {
        "API_KEY": "production-api-key"
      }
    },
    "vargg-staging": {
      "url": "https://var.gg/api/mcp",
      "headers": {
        "API_KEY": "staging-api-key"
      }
    }
  }
}
```

### Custom Endpoints

For local development or custom deployments:

```json
{
  "mcpServers": {
    "vargg-local": {
      "url": "http://localhost:8082/api/mcp",
      "headers": {
        "API_KEY": "your-local-api-key"
      }
    }
  }
}
```

### Timeout Configuration

If you experience timeout issues, you can configure timeouts (if supported by Cursor):

```json
{
  "mcpServers": {
    "vargg": {
      "url": "https://var.gg/api/mcp",
      "headers": {
        "API_KEY": "your-api-key"
      },
      "timeout": 30000
    }
  }
}
```

---

## 🌐 Network Configuration

### Local Development

If you're running VARGG MCP locally:

1. Start your local VARGG server (typically on `http://localhost:8082`)
2. Update the MCP configuration:
   ```json
   {
     "mcpServers": {
       "vargg": {
         "url": "http://localhost:8082/api/mcp",
         "headers": {
           "API_KEY": "your-local-api-key"
         }
       }
     }
   }
   ```
3. Ensure Cursor IDE can access `localhost:8082`

### Corporate Network / VPN

If you're behind a corporate firewall:

1. **Check Proxy Settings**: Cursor IDE may need proxy configuration
2. **Whitelist Domains**: Ensure `var.gg` and `*.var.gg` are whitelisted
3. **Certificate Issues**: Some corporate proxies use custom certificates - you may need to configure certificate trust

### Firewall Rules

Required outbound connections:
- **HTTPS**: `https://var.gg` (port 443)
- **API Endpoint**: `https://var.gg/api/mcp` (port 443)

---

## 🔑 API Key Management

### Generating API Keys

1. Visit [https://var.gg](https://var.gg)
2. Navigate to Account Settings
3. Find "API Keys" or "MCP Settings"
4. Click "Generate New API Key"
5. **Copy immediately** - the key won't be shown again!

### Rotating API Keys

For security, regularly rotate your API keys:

1. Generate a new API key
2. Update Cursor IDE configuration with the new key
3. Test the connection
4. Revoke the old API key from the website

### Key Scoping

API keys inherit your user permissions:
- You can access projects you own
- You can access projects you've been invited to (read-only or with permissions)
- You cannot access private projects you're not a member of

### Key Security

**DO**:
- ✅ Store API keys securely (use a password manager)
- ✅ Rotate keys regularly
- ✅ Revoke keys if compromised
- ✅ Use different keys for different environments

**DON'T**:
- ❌ Commit API keys to version control
- ❌ Share API keys publicly
- ❌ Include keys in screenshots
- ❌ Use production keys for development

---

## 🐛 Troubleshooting

### Connection Issues

#### Problem: "MCP server disconnected"

**Checklist**:
1. ✅ API key is correct (no extra spaces or line breaks)
2. ✅ URL is exactly `https://var.gg/api/mcp`
3. ✅ Header name is `API_KEY` (case-sensitive)
4. ✅ Internet connection is active
5. ✅ Cursor IDE is restarted after configuration change

**Solutions**:
- Double-check the JSON syntax (valid JSON required)
- Try regenerating the API key
- Check Cursor IDE console for error messages
- Verify the API endpoint is accessible: `curl https://var.gg/api/mcp`

#### Problem: "Authentication failed"

**Causes**:
- Invalid API key
- Expired API key (if keys have expiration)
- API key revoked

**Solutions**:
1. Generate a new API key
2. Update Cursor configuration
3. Restart Cursor IDE

#### Problem: "Timeout" or "Connection timeout"

**Causes**:
- Slow internet connection
- Network latency
- Server overload (rare)

**Solutions**:
1. Check your internet speed
2. Try again after a few seconds
3. Check [var.gg status](https://var.gg) (if available)
4. Use a wired connection if on WiFi

### Tool Execution Issues

#### Problem: Tools return "authentication required"

**Cause**: The tool requires authentication, but your API key is missing or invalid.

**Solutions**:
1. Verify API key is set correctly
2. Regenerate API key if needed
3. Check tool documentation for authentication requirements

#### Problem: "Project not found"

**Cause**: Incorrect project ID or insufficient permissions.

**Solutions**:
1. List your projects first: `List my projects`
2. Use the exact project ID from the list
3. Verify you have access to the project
4. Check project visibility (private vs public)

#### Problem: "Invalid parameter" or validation errors

**Cause**: Parameter doesn't match the required schema.

**Solutions**:
1. Check [Tools Reference](tools-reference.md) for parameter requirements
2. Verify variable names are in SNAKE_CASE
3. Check character limits and validation rules per language
4. Review error message for specific validation failure

### Performance Issues

#### Problem: Slow tool execution

**Possible causes**:
- Large project with many variables
- Network latency
- Server load

**Solutions**:
1. Use pagination when listing variables (`limit` parameter)
2. Use specific search keywords instead of broad searches
3. Check your network connection

---

## 🔒 Security Best Practices

### 1. API Key Protection

- **Never commit keys to git**: Use environment variables or secure storage
- **Rotate regularly**: Change keys every 90 days
- **Use different keys**: Separate keys for development and production
- **Monitor usage**: Check your API key usage logs regularly

### 2. Network Security

- **Use HTTPS**: Always use `https://var.gg` (never HTTP)
- **Verify certificates**: Ensure SSL certificates are valid
- **Avoid public WiFi**: Use secure networks when possible

### 3. Project Access Control

- **Private projects**: Keep sensitive projects private
- **Permission management**: Regularly review who has access to your projects
- **Remove access**: Revoke access for team members who no longer need it

### 4. Data Privacy

- **Variable naming**: Avoid including sensitive data in variable names
- **Definitions**: Keep definitions descriptive but not revealing sensitive information
- **Project names**: Use clear but non-sensitive project names

---

## 📞 Getting Help

If you've tried the troubleshooting steps above and still have issues:

1. **Check Documentation**: Review [Tools Reference](tools-reference.md) and [Best Practices](best-practices.md)
2. **Search Issues**: Look for similar problems in [GitHub Issues](https://github.com/var-gg/mcp/issues)
3. **Ask Community**: Post your question in [Discussions](https://github.com/var-gg/mcp/discussions)
4. **Report Bugs**: Create a new [Issue](https://github.com/var-gg/mcp/issues/new) with detailed information

---

## ✅ Verification Checklist

After setup, verify everything works:

- [ ] Cursor IDE shows MCP connection as "Connected"
- [ ] Can list projects: `List my projects`
- [ ] Can create a project: `Create a new project named "Test"`
- [ ] Can search variables: `Search for variables related to "test" in the project`
- [ ] Can create variables: `Create variable TEST_VAR with definition "test variable"`
- [ ] No authentication errors in Cursor console

---

**Congratulations!** You're now fully integrated with VARGG MCP. Happy coding! 🚀

