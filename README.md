# 🔍 WHOIS MCP Server

**[中文版](./README_ZH.md)** | **English**

> A comprehensive MCP server for WHOIS lookups of domains, IPs, TLDs, and ASNs

## 🎯 Overview

A Model Context Protocol (MCP) server that provides WHOIS lookup capabilities for domains, IP addresses, Top Level Domains (TLDs), and Autonomous System Numbers (ASNs). Built with TypeScript and the `whoiser` library for reliable and fast WHOIS queries.

## ✨ Features

- 🌐 **Domain WHOIS**: Look up registration information for any domain
- 🖥️ **IP WHOIS**: Get network information and ownership details for IP addresses
- 🏷️ **TLD WHOIS**: Retrieve information about Top Level Domains
- 🔢 **ASN WHOIS**: Look up Autonomous System Number details
- 🔒 **Type Safety**: Full TypeScript implementation with Zod validation
- 🎨 **Colorful Logging**: Colored console output for better visibility
- ⚡ **Fast Performance**: Built on the reliable `whoiser` library
- 🛡️ **Error Handling**: Comprehensive error handling with friendly messages

## 📦 Installation

```bash
npm install @szemeng76/whois-mcp
```

Or clone and install locally:

```bash
git clone https://github.com/SzeMeng76/whois-mcp.git
cd whois-mcp
npm install
npm run build
```

## 🔧 Configuration

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

### VS Code with GitHub Copilot

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

### Local Development

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

## 🛠️ Available Tools

### `whois_domain`
Looks up WHOIS information for a domain name.

**Parameters:**
- `domain` (required): Domain name to query (e.g., "example.com", "github.com")

**Example Usage:**
```
"Look up WHOIS information for google.com"
"Get domain registration details for stackoverflow.com"
"Check who owns the domain github.com"
```

**Returns:**
- Domain registration information
- Registrar details
- Name servers
- Creation and expiration dates
- Registrant contact information (if available)

### `whois_ip`
Looks up WHOIS information for an IP address.

**Parameters:**
- `ip` (required): IPv4 or IPv6 address to query (e.g., "8.8.8.8", "1.1.1.1")

**Example Usage:**
```
"Get WHOIS information for IP address 8.8.8.8"
"Look up the owner of IP 1.1.1.1" 
"Check network details for 192.168.1.1"
```

**Returns:**
- Network ownership information
- IP address range allocation
- Organization details
- Geographic location data
- Contact information

### `whois_tld`
Looks up WHOIS information for a Top Level Domain.

**Parameters:**
- `tld` (required): Top Level Domain to query (e.g., "com", "org", "io")

**Example Usage:**
```
"Get information about the .com TLD"
"Look up details for the .io domain"
"Check who manages the .org TLD"
```

**Returns:**
- TLD registry information
- Managing organization
- Policy details
- Contact information
- Technical details

### `whois_as`
Looks up WHOIS information for an Autonomous System Number.

**Parameters:**
- `asn` (required): ASN in format "AS####" (e.g., "AS15169", "AS13335")

**Example Usage:**
```
"Look up ASN AS15169"
"Get information about AS13335"
"Check details for autonomous system AS8075"
```

**Returns:**
- ASN ownership information
- Organization details
- Network routes
- Contact information
- Technical details

## 🎮 Usage Examples

### Security Research
```
"Look up the domain suspicious-site.com to check its registration details"
"Get WHOIS info for IP 203.0.113.1 to identify the network owner"
```

### Network Troubleshooting
```
"Check ASN AS15169 to see what networks Google operates"
"Look up IP 1.1.1.1 to verify it belongs to Cloudflare"
```

### Domain Investigation
```
"Get registration details for example.com to see when it expires"
"Look up .io TLD information to understand the registry policies"
```

### Competitive Analysis
```
"Check WHOIS for competitor-domain.com to see registration patterns"
"Look up multiple domains: example1.com, example2.org, example3.net"
```

## 🏗️ Development

### Local Setup

```bash
# Clone the repository
git clone https://github.com/SzeMeng76/whois-mcp.git
cd whois-mcp

# Install dependencies
npm install

# Build the project
npm run build

# Start the server
npm start
```

### Project Structure

```
whois-mcp/
├── src/
│   ├── index.ts          # Main MCP server implementation
│   └── utils.ts          # Utility functions (colored console output)
├── dist/                 # Compiled JavaScript files
├── package.json          # Dependencies and scripts
├── tsconfig.json         # TypeScript configuration
└── README.md            # Documentation
```

### Core Dependencies

- **@modelcontextprotocol/sdk**: Official MCP server framework
- **whoiser**: Reliable WHOIS lookup library
- **zod**: Runtime type validation and schema definition

## 🔧 Technical Details

### Input Validation
- **Domain names**: Basic non-empty string validation
- **IP addresses**: Basic non-empty string validation (library handles format validation)
- **TLDs**: Non-empty string validation
- **ASNs**: Regex validation for "AS####" format with automatic number conversion

### Error Handling
- Comprehensive try-catch blocks for all WHOIS operations
- Friendly error messages for common issues
- Graceful handling of network timeouts and invalid inputs
- Error responses include `isError: true` flag

### Logging and Output
- Colored console output using custom utility functions
- Green checkmark for successful startup
- Yellow warnings for shutdown procedures
- Red error messages for failures
- Structured JSON responses for all WHOIS data

### Signal Handling
- Graceful shutdown on SIGINT (Ctrl+C) and SIGTERM
- Proper cleanup of transport connections
- User-friendly shutdown messages

## ⚠️ Important Notes

### Rate Limiting
- WHOIS servers have rate limits to prevent abuse
- Avoid making too many rapid consecutive queries
- Some servers may temporarily block excessive requests

### Data Accuracy
- WHOIS data accuracy depends on registrar compliance
- Some domains may have privacy protection enabled
- Historical data may not always be available

### Legal Considerations
- WHOIS data is subject to various privacy laws and regulations
- Use data responsibly and in compliance with applicable laws
- Respect registrar terms of service and rate limits

## 🚀 Common Use Cases

### Cybersecurity
- **Threat Intelligence**: Investigate suspicious domains and IP addresses
- **Incident Response**: Gather information about malicious infrastructure
- **Domain Monitoring**: Track domain registration changes

### Network Administration
- **IP Management**: Verify IP address ownership and allocation
- **Routing Analysis**: Understand ASN relationships and network paths
- **Infrastructure Planning**: Research network providers and ASN details

### Business Intelligence
- **Competitive Research**: Monitor competitor domain registrations
- **Due Diligence**: Verify domain ownership before partnerships
- **Brand Protection**: Monitor similar domain registrations

### Development and Testing
- **API Integration**: Test WHOIS functionality in applications
- **Network Debugging**: Troubleshoot connectivity and routing issues
- **Educational Purposes**: Learn about internet infrastructure

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes with proper TypeScript types
4. Test with various domains, IPs, TLDs, and ASNs
5. Ensure error handling works correctly
6. Submit a pull request with clear description

### Development Guidelines

- Maintain TypeScript strict mode compliance
- Add proper error handling for new features
- Use the existing color utility functions for console output
- Test with both valid and invalid inputs
- Document any new parameters or return formats

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## ⚖️ Legal and Privacy

- **Data Source**: WHOIS data is retrieved from public registries
- **Privacy**: Some WHOIS data may be redacted due to privacy policies
- **Compliance**: Users must comply with applicable privacy laws and regulations
- **Rate Limits**: Respect WHOIS server rate limits and terms of service
- **Responsible Use**: Use WHOIS data for legitimate purposes only

## 🙏 Acknowledgments

- **whoiser**: Excellent WHOIS lookup library
- **MCP Community**: For the standardized protocol
- **Internet Registries**: For maintaining public WHOIS services
- **Contributors**: Everyone who helps improve this project

---

*Built for network research, security analysis, and internet infrastructure understanding* 🔍🌐
