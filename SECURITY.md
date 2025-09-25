# Security Policy

## Supported Versions

This project is currently in early development phase. Security updates will be provided for:

| Version | Supported          |
| ------- | ------------------ |
| main    | :white_check_mark: |

## Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security vulnerability, please report it by:

1. **DO NOT** open a public issue
2. Use GitHub's private vulnerability reporting feature in this repository: [Security Advisories](https://github.com/QuingKhaos/factorio-mocks-modpacks/security/advisories)

### What to Include

Please include as much information as possible:

- Description of the vulnerability
- Steps to reproduce the issue
- Factorio version and modpack configuration (if applicable)
- Potential impact and affected components
- Suggested fix (if any)
- Your contact information for follow-up

### Response Timeline

- **Acknowledgment**: Within 72 hours
- **Initial Assessment**: Within 7 days
- **Resolution**: Varies based on complexity and severity

## Security Considerations

The Factorio Mocks Modpacks repository provides curated modpack configurations and automation for comprehensive
Factorio mod testing scenarios.

### Architecture Overview

- **Modpack Curation**: Lua-based mod manager for ORAS artifact management
- **Build Automation**: GitHub Actions workflows for modpack build and data extraction
- **ORAS Integration**: Secure artifact distribution via GitHub Container Registry
- **Git Distribution**: Alternative distribution method alongside ORAS

### Security Features

- **Build Isolation**: All automation runs in isolated GitHub Actions environments
- **Path Validation**: File system operations validated to prevent traversal attacks
- **ORAS Security**: Container registry authentication and secure artifact distribution

### Security Practices

- **Automated Validation**: All configurations validated through automated testing
- **Process Isolation**: Build and extraction processes run in sandboxed environments
- **Clean Artifacts**: Generated modpack artifacts contain only validated content

### For Contributors

- **Path Safety**: Validate all file system operations and paths
- **Build Security**: Ensure automation scripts handle errors securely without exposing sensitive information
- **ORAS Security**: Follow secure practices for container registry operations
- **Error Handling**: Ensure error messages don't leak sensitive paths or system information

## Security Contacts

For security-related questions or concerns:

- **GitHub Security**: Use private vulnerability reporting in [this repository](https://github.com/QuingKhaos/factorio-mocks-modpacks/security/advisories)
- **Community**: General security discussions in [GitHub Discussions](https://github.com/QuingKhaos/factorio-mocks/discussions)

---

*This security policy reflects the Phase 2 implementation as a curated modpack automation system.*
