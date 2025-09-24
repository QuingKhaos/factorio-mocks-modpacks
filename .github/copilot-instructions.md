# Copilot Instructions for Factorio Mocks Modpacks

## Project Overview

The **Factorio Mocks Modpacks** repository provides curated modpack configurations and automation for comprehensive
Factorio mod testing scenarios. This repository contains both modpack configurations and Lua-based automation systems
for ORAS artifact management and dual distribution workflows.

**Architecture**: Curated modpack configurations with Lua automation and dual distribution
**Philosophy**: Community-driven modpack curation with maintainer oversight for quality assurance

### Core Architecture

The modpacks repository operates with two primary components:

1. **Modpack Configurations** (`/modpacks` directory) - Curated modpack definitions
2. **Automation Systems** (`/src`, `/bin` directories) - Lua-based mod manager and build automation

### Key Architectural Decisions

- **Latest Mod Versions Strategy**: Only Factorio version pinned; all mods use latest compatible versions (ADR-0010)
- **Dual Distribution**: Both Git-based and ORAS artifact distribution for flexibility
- **Maintainer Curation**: Community requests via issues, maintainer-curated configurations
- **Automated Builds**: GitHub Actions workflows for builds, extraction and distribution

## Development Philosophy

### Community-First Curation

- Maintainer-curated approach ensures quality and community value
- Community requests welcome via centralized issue system
- Focus on popular and testing-valuable modpack combinations
- Support for both simple and complex modpack scenarios

### Lua Development Focus

- Sophisticated mod manager for ORAS integration
- Build system automation with proper error handling
- Integration with GitHub Container Registry
- Dual distribution workflow management

## Technical Context

### Current Implementation Status

- **Phase**: Foundation complete, ready for modpack curation and automation implementation
- **Architecture**: `/modpacks`, `/src`, `/bin` directory structure established
- **Distribution**: Dual workflow (Git + ORAS) designed for flexibility
- **Curation**: Issue-based community request system with maintainer evaluation
- **Automation**: GitHub Actions workflows for build and distribution

### Key Technologies

- **Lua Development**: Core automation and mod management systems
- **ORAS Distribution**: Container-based artifact distribution via GitHub Container Registry
- **Git Distribution**: Alternative distribution method for direct access
- **GitHub Actions**: Automated build, validation, and distribution workflows

### Integration Points

#### Factorio Game Integration

- **Custom modpack.json**: Semantic modpack definitions with dependency resolution
- **Mod Portal Integration**: Automatic resolution of mod dependencies to official sources
- **Latest Versions**: Always uses current mod versions for up-to-date testing
- **Factorio Version Pinning**: Only Factorio version controlled for stability

#### Ecosystem Integration

- **Generator Integration**: Data extraction pipeline integrated within this repository for modpack-specific builds
- **Data Repository**: Generated artifacts distributed via ORAS to data repository
- **Loader Integration**: Modpack contexts available for runtime mock selection
- **Centralized Issues**: All requests and issues managed in main hub repository

## Code Standards and Conventions

### Lua Development Standards

**Style Guidelines:**

- **Indentation**: 2 spaces (matches `.editorconfig`)
- **Line Length**: 120 characters for Lua code
- **Naming**: snake_case for variables and functions
- **Quotes**: Double quotes for strings
- **Comments**: Explain WHY, not WHAT (follow self-explanatory code instructions)

### Modpack Configuration Standards

**Directory Structure:**

```bash
modpacks/
├── vanilla/                    # Vanilla Factorio (base game only)
├── pyanodons/                  # Pyanodons modpack
├── space-exploration/          # Space Exploration modpack
└── [modpack-name]/             # Additional modpack configurations
```

**Configuration Format:**

- `modpack.json` - Custom modpack definition with metadata and dependencies
- `mod-settings.dat` - Binary mod settings (optional)

### GitHub Integration Standards

- **Issue Templates**: Community requests via main repository modpack request template
- **PR Reviews**: All configurations require maintainer review
- **Conventional Commits**: Standard commit message format for automation
- **Branch Protection**: Main branch protected with required status checks

## Development Workflow

### Modpack Curation Process

**Community Requests:**

1. **Issue Creation**: Community uses modpack request template in main repository
2. **Evaluation**: Maintainers assess community value and testing relevance
3. **Implementation**: Maintainers create configuration directly in modpacks directory
4. **Validation**: Automated testing ensures configuration works correctly
5. **Documentation**: README and metadata updated for discoverability

**Configuration Structure:**

```bash
modpacks/modpack-name/
├── modpack.json               # Custom modpack definition with metadata and dependencies
└── mod-settings.dat           # Binary mod settings (optional)
```

### Lua Automation Development

**Mod Manager Development:**

- **ORAS Operations**: Push/pull operations with GitHub Container Registry
- **Configuration Management**: Dynamic modpack loading and validation
- **Build Coordination**: Integration with GitHub Actions workflows
- **Error Handling**: Robust error handling with clear user feedback

### Testing Strategy

- **Configuration Testing**: All modpack configurations validated in clean environments
- **Automation Testing**: Lua systems tested with mock ORAS operations
- **Integration Testing**: End-to-end workflow validation

## Common Patterns and Helpers

### Modpack Configuration Patterns

**`modpack.json`:**

```json
{
  "name": "pyanodons-full",
  "title": "Full Pyanodons",
  "description": "Full pyanodons with additional quality of life mods",
  "dependencies": [
    "base >= 2.0.66",
    "cranes_pyanodon >= 2.0.0",
    "pyalienlife >= 3.0.58",
    "pyalternativeenergy >= 3.1.34",
    "pycoalprocessing >= 3.0.28",
    "pyfusionenergy >= 3.0.16",
    "pyhightech >= 3.0.17",
    "pyindustry >= 3.0.19",
    "pypetroleumhandling >= 3.0.21",
    "pypostprocessing >= 3.0.39",
    "pyrawores >= 3.0.24"
  ]
}
```

## Security Considerations

### Modpack Security

- **Official Sources**: All mods resolved against official Factorio Mod Portal
- **Build Isolation**: All automation runs in isolated GitHub Actions environments
- **Path Validation**: File system operations validated to prevent traversal attacks

### Automation Security

- **ORAS Security**: Container registry authentication and secure operations
- **Process Isolation**: Build processes run in sandboxed environments
- **Error Handling**: Secure error handling without exposing sensitive information
- **Clean Artifacts**: Generated artifacts contain only validated content

## Troubleshooting and Common Issues

### Configuration Issues

- **JSON Format**: Validate JSON syntax and required fields
- **Missing Mods**: Verify all referenced mods exist on Factorio Mod Portal

### Automation Issues

- **ORAS Authentication**: Verify GitHub Container Registry authentication
- **Build Failures**: Check GitHub Actions logs for automation errors
- **Network Issues**: Handle temporary mod portal or registry unavailability
- **Path Issues**: Ensure proper path handling across different operating systems

---

## Quick Reference

**Main Commands**: Lua-based mod manager
**Architecture**: Curated configurations + Lua automation with dual distribution
**Distribution**: Git repository + ORAS artifacts via GitHub Container Registry
**Curation**: Community requests via main repository, maintainer evaluation
**Integration**: Direct mod directory placement with latest mod versions

## Technical References

### Factorio Integration

- **[Mod Portal API](https://wiki.factorio.com/Mod_portal_API)** - Official API for mod discovery and metadata
- **[Mod Structure](https://lua-api.factorio.com/latest/auxiliary/mod-structure.html)** - Standard mod file structure
- **[Command Line Parameters](https://wiki.factorio.com/Command_line_parameters)** - Essential for automated
  Factorio operations

### Distribution Technology

- **[ORAS Specification](https://oras.land/)** - Container-based artifact distribution technology
- **[GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)**
  \- Artifact hosting and distribution platform

## Ecosystem Context

**Main Repository**: [factorio-mocks](https://github.com/QuingKhaos/factorio-mocks) - Central coordination and documentation
**Data Generation**: [factorio-mocks-generator](https://github.com/QuingKhaos/factorio-mocks-generator) - Automated
data extraction from modpack configurations
**Data Storage**: [factorio-mocks-data](https://github.com/QuingKhaos/factorio-mocks-data) - Generated mock data
artifacts and distribution
**Data Consumption**: [factorio-mocks-loader](https://github.com/QuingKhaos/factorio-mocks-loader) - Runtime library
for mock data consumption
**Issue Tracking**: Centralized in main repository with `ecosystem: modpacks` labels
