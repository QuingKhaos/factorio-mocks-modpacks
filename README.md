[![GitHub build status: Quality Assurance](https://img.shields.io/github/actions/workflow/status/QuingKhaos/factorio-mocks-modpacks/qa.yml?branch=main&label=QA&style=for-the-badge)](https://github.com/QuingKhaos/factorio-mocks-modpacks/actions?query=workflow%3A%22Quality+Assurance%22)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/QuingKhaos/factorio-mocks-modpacks?label=Pull%20Requests&style=for-the-badge)](https://github.com/QuingKhaos/factorio-mocks-modpacks/pulls)
[![Ko-fi](https://img.shields.io/badge/Ko--fi-support%20me-hotpink?logo=kofi&logoColor=white&style=for-the-badge)](https://ko-fi.com/quingkhaos)

# Factorio Mocks Modpacks - Curated Mod Configurations

## Overview

Curated collection of Factorio modpack configurations designed for comprehensive mock data generation and testing
scenarios.

Part of the [Factorio Mocks Ecosystem](https://github.com/QuingKhaos/factorio-mocks) - a five-repository system
providing complete testing infrastructure for Factorio mod development.

## 🎯 Purpose

The `factorio-mocks-modpacks` repository maintains carefully curated modpack configurations representing common
modpacks played in the Factorio community. These configurations drive automated mock data generation using the
[factorio-mocks-generator](https://github.com/QuingKhaos/factorio-mocks-generator) to produce comprehensive mock data
for robust mod testing across diverse environments.

**Key Benefits:**

- **Community Alignment**: Focus on modpacks actually played by the Factorio community
- **Automated Data Generation**: CI/CD workflows automatically generate mock data using latest mod versions
- **ORAS Distribution**: Container-based artifact distribution for efficient data consumption
- **Zero Maintenance**: Latest mod versions eliminate manual version management overhead

## 🏗️ Architecture

### Modpack Organization

```text
modpacks/
├── vanilla/
│   ├── modpack.json
├── spaceage/
│   ├── modpack.json
├── krastorio2/
│   ├── modpack.json
│   └── mod-settings.dat
├── pyanodons/
└── [other-modpacks]/
```

### Configuration Structure

Each modpack configuration includes:

- **`modpack.json`**: Custom modpack definition with metadata and dependencies for mod manager resolution
- **`mod-settings.dat`**: Binary mod settings (when non-default settings are needed)

**Latest Mod Versions Strategy**: Only Factorio version is pinned to latest stable version. All mods use latest available
versions from the Mod Portal, eliminating maintenance overhead while ensuring current test data.

### `modpack.json` Format

The `modpack.json` format follows Factorio's `info.json` structure but serves as a dependency specification rather than a
complete mod definition:

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

## 🚀 Current Status

**Phase**: Early Development - Planning and Architecture Complete

**Implementation Status:**

- ✅ **Foundation Setup** - Repository infrastructure and documentation
- ⏳ **Vanilla Configurations** - Base Factorio version setups
- ⏳ **Popular Mod Collections** - Common single-mod and small-set configurations
- ⏳ **Comprehensive Modpacks** - Full-scale modpack configurations
- ⏳ **Community Modpacks** - Additional popular modpack configurations
- ⏳ **Automated Build Workflows** - CI/CD pipelines for artifact generation

## 🎮 How It Works

### Mock Data Generation Workflow

Following the ecosystem's data flow architecture, modpack configurations drive the complete mock data generation process:

1. **Modpack Preparation**: Resolve latest compatible mod versions and create ORAS artifacts
2. **Environment Setup**: GitHub Actions pulls modpack artifacts and sets up extraction environment
3. **Data Extraction**: `factorio-mocks-generator` runs in headless Factorio instance with the modpack
4. **Data Processing**: Extract, validate, and format all exportable globals and localization
5. **Dual Distribution**: Update `factorio-mocks-data` Git repository AND create ORAS artifacts with dual tagging
6. **Artifact Linking**: Use `oras attach` to link mock data artifacts to their source modpack digest
7. **Consumption**: `factorio-mocks-loader` fetches and caches data for consumer projects

### ORAS Artifact Structure

```bash
# Modpack artifact
ghcr.io/quingkhaos/factorio-mocks-modpacks/vanilla:2.0.66

# Generated mock data artifact (linked via oras attach)
ghcr.io/quingkhaos/factorio-mocks-data/vanilla:2.0.66-2024.12.15
```

### Automated Update Cycle

- **Daily Builds**: Automated GitHub Actions resolve latest mod versions and regenerate artifacts
- **Version Capture**: Each artifact snapshot contains exact mod versions used at build time
- **Dependency Resolution**: Always fetch latest versions that satisfy dependency constraints

### Latest Versions Strategy

- **Factorio Version**: Pinned to specific stable release (e.g. 2.0.66)
- **Mod Versions**: Always use latest available versions from Mod Portal
- **Automated Updates**: Daily builds capture mod ecosystem evolution automatically
- **Build Immutability**: Each artifact captures exact versions used at build time

## 🔧 Development Setup

### Prerequisites

- **Git** and **GitHub CLI** for repository management
- **Lua** development environment for mod manager scripts

### Quick Start

For detailed development setup, see the [Contributing Guide](CONTRIBUTING.md#development-environment-setup).

**Basic Setup**:

1. Clone the repository
2. Review existing modpack configurations

### Automated Build Process

- **CI/CD Workflows**: Automated build processing for all modpack configurations
- **ORAS Artifact Generation**: Automated artifact creation and distribution

## 📚 Documentation

### For Contributors

- **[Contributing Guide](CONTRIBUTING.md)** - How to contribute modpack configurations
- **[Code of Conduct](CODE_OF_CONDUCT.md)** - Community standards and expectations
- **[Security Policy](SECURITY.md)** - Reporting security issues

### For Ecosystem

- **[Main Documentation](https://github.com/QuingKhaos/factorio-mocks)** - Full ecosystem overview
- **[Architecture Decisions](https://github.com/QuingKhaos/factorio-mocks/tree/main/planning/decisions)** - Technical
  decision records
- **[Implementation Roadmap](https://github.com/QuingKhaos/factorio-mocks/blob/main/planning/implementation-roadmap.md)**
  - Development phases

## 🤝 Contributing

We welcome contributions from Factorio modpack creators, mod developers, and the broader community! Your modpack
configurations help ensure comprehensive testing coverage for the entire ecosystem.

### Ways to Contribute

- **Modpack Configurations**: Add new documented modpack setups
- **Build Process Enhancement**: Improve automated build workflows and artifact generation
- **Documentation**: Improve configuration guides and usage notes
- **Community Feedback**: Share experiences with different modpack combinations

### Getting Started

1. Read the [Contributing Guide](CONTRIBUTING.md)
2. Check [open issues](https://github.com/QuingKhaos/factorio-mocks/issues?q=is%3Aopen+label%3A%22ecosystem%3A+modpacks%22)
   for modpack-specific tasks
3. Look for [`good-first-issue`](https://github.com/QuingKhaos/factorio-mocks/issues?q=is%3Aopen+label%3A%22good-first-issue%22+label%3A%22ecosystem%3A+modpacks%22)
   labels for beginner-friendly tasks

**Note**: Issues are tracked centrally in the [main repository](https://github.com/QuingKhaos/factorio-mocks/issues)
with `ecosystem: modpacks` labels.

## 📄 License

This project is licensed under the GNU General Public License v3.0 (GPLv3). See [LICENSE](LICENSE) for details.

**Why GPLv3?** This license ensures that the project's tooling remain open source while maintaining strong copyleft
protections for the community.

## 🔗 Ecosystem Links

- **[factorio-mocks](https://github.com/QuingKhaos/factorio-mocks)** - Central hub and main documentation
- **[factorio-mocks-generator](https://github.com/QuingKhaos/factorio-mocks-generator)** - Data extraction engine
- **[factorio-mocks-data](https://github.com/QuingKhaos/factorio-mocks-data)** - Generated mock data artifacts
- **[factorio-mocks-loader](https://github.com/QuingKhaos/factorio-mocks-loader)** - Runtime library for consuming
  mock data

## 💖 Support

If this project helps your Factorio mod development, consider supporting its development:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-support%20this%20project-hotpink?logo=kofi&logoColor=white&style=for-the-badge)](https://ko-fi.com/quingkhaos)

---

**Status**: 🚧 Early Development Phase - Infrastructure setup and planning complete, configuration creation beginning.
