# Contributing to Factorio Mocks Modpacks

Thank you for your interest in contributing to the Factorio Mocks Modpacks! This repository is part of the
[Factorio Mocks Ecosystem](https://github.com/QuingKhaos/factorio-mocks) and serves as the curated collection of
modpack configurations for comprehensive mock data generation.

## Table of Contents

- [Getting Started](#getting-started)
- [Development Environment Setup](#development-environment-setup)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Documentation Guidelines](#documentation-guidelines)
- [Issue and Pull Request Process](#issue-and-pull-request-process)
- [Community Guidelines](#community-guidelines)
- [Useful Resources](#useful-resources)

## Getting Started

### Prerequisites

**Core Requirements:**

- **Git**: For version control
- **GitHub Account**: For collaboration
- **GitHub CLI** (recommended): For easier repository management
- **Factorio**: At least version 2.0.66 installed for modpack testing
- **Lua 5.2**: For mod manager scripts (matches Factorio's version)
- **Text Editor/IDE**: VS Code recommended with JSON extensions

**Development Tools:**

- **markdownlint-cli**: For documentation linting (`npm install -g markdownlint-cli`)
- **Lua**: Lua 5.2 interpreter for local testing
- **LuaRocks**: For Lua dependency management

### Factorio Setup Requirements

The modpacks requires specific Factorio configuration to run and modpack configurations:

1. **Factorio Installation**: Steam, standalone or headless version
2. **Instrument Mode**: All installations must run with `--instrument-mod` flag for data extraction

### First-Time Setup

1. **Fork and Clone Repository**

   ```bash
   gh repo fork QuingKhaos/factorio-mocks-modpacks --clone
   cd factorio-mocks-modpacks
   ```

2. **Set Up Development Environment**

   ```bash
   # Install documentation tools
   npm install -g markdownlint-cli

   # Verify Lua installation (should be 5.2.x)
   lua -v

   # Verify Factorio installation
   factorio --version
   ```

3. **Review Project Structure**
   - Read `README.md` for modpacks overview
   - Review [ecosystem documentation](https://github.com/QuingKhaos/factorio-mocks)
   - Understand modpack configuration architecture

## Development Environment Setup

### Local Development Environment

1. **Install Dependencies**:

   ```bash
   # Install Lua dependencies using rockspec
   luarocks install --only-deps factorio-mocks-modpacks-dev-1.rockspec
   ```

2. **Test Build Environment**:

   ```bash
   # Test modpack processing when available
   # Commands will be documented as development progresses
   ```

### Development Tools Setup

**Required for Development:**

- Lua 5.2 interpreter for mod manager testing
- Text editor with JSON syntax highlighting
- Git with proper configuration for commits

**Recommended Extensions (VS Code):**

- Lua language server
- markdownlint

## Development Workflow

### Branch Strategy

- **main**: Stable, tested code and curated modpack configurations
- **feature branches**: `feat/mod-manager-improvements` for Lua development
- **fix branches**: `fix/oras-artifact-generation` for bug fixes
- **docs branches**: `docs/api-documentation` for documentation updates

**Note**: Modpack configurations (`modpack.json`, `mod-settings.dat`) are curated by maintainers. To request a new
modpack, please open an issue with the modpack details rather than submitting a PR.

### Standard Workflow

1. **Create Feature Branch**

   ```bash
   git checkout -b feat/mod-manager-improvements
   ```

2. **Develop and Test**
   - Write Lua code for mod manager enhancements
   - Test with local Factorio installation
   - Verify build system functionality

3. **Quality Checks**

   ```bash
   # Run documentation linting
   markdownlint --config .markdownlint.json --dot **/*.md
   ```

4. **Commit and Push**

   ```bash
   git add .
   git commit -m "feat(mod-manager): improve dependency resolution for optional dependencies"
   git push origin feat/mod-manager-improvements
   ```

5. **Create Pull Request**

   ```bash
   # Push your changes first
   git push origin feat/mod-manager-improvements
   ```

   Then create a pull request through the GitHub web interface to ensure the PR template is properly applied:
   `https://github.com/QuingKhaos/factorio-mocks-modpacks/compare/main...your-branch-name`

## Requesting Modpack Configurations

**Modpack configurations are curated by maintainers.** If you'd like to see a specific modpack included in the ecosystem:

1. **Open an Issue**: Use the [modpack request template](https://github.com/QuingKhaos/factorio-mocks/issues/new?template=modpack_request.yml)
2. **Provide Details**:
   - Modpack name and purpose
   - Community relevance and usage
   - Key mods included
   - Special configuration requirements
3. **Maintainer Review**: Maintainers will evaluate and add approved configurations

## Coding Standards

### Lua Code Standards

**Style Guidelines:**

- **Indentation**: 2 spaces (no tabs)
- **Line Length**: 120 characters
- **Naming**: snake_case for variables and functions
- **Quotes**: Double quotes for strings
- **Comments**: Explain WHY, not WHAT (see self-explanatory code instructions)

### Commit Message Format

Use [Conventional Commits](https://www.conventionalcommits.org/) format:

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Modpacks-Specific Types:**

- `feat`: New Lua functionality for mod manager
- `fix`: Bug fixes in Lua code, ORAS operations, or dependency resolution
- `ci`: Changes to CI workflows and build automation
- `test`: Adding or updating Lua unit tests and integration tests
- `docs`: Documentation changes for APIs and development guides

**Examples:**

```text
feat(mod-manager): implement ORAS artifact download with retry logic
fix(validation): handle missing dependency fields in modpack.json parsing
test(mod-manager): add unit tests for dependency resolution algorithm
```

## Testing Guidelines

### Test Categories

#### Code Quality

- Lua syntax validation
- Code style compliance
- Function correctness

#### Integration Tests

- Test complete mod manager workflows
- Verify ORAS artifact generation
- Test with automated build system

### Testing Requirements

**Before Submitting PRs:**

- [ ] Lua code passes syntax validation
- [ ] Code follows established style guidelines
- [ ] Documentation updated for new features

## Documentation Guidelines

### Markdown Standards

Follow the repository's `.markdownlint.json` configuration:

- Maximum line length: 120 characters
- Use ATX headings (`#`, `##`, `###`)
- Consistent list formatting with dashes (`-`)
- Proper noun capitalization (Factorio, GitHub, Lua, ORAS)

### Code Documentation

**Lua Code Documentation:**

- Document function purposes and expected parameters
- Explain complex algorithms and business logic
- Provide examples for API usage and integration

## Issue and Pull Request Process

### Reporting Issues

**Important**: Report all issues in the [main ecosystem repository](https://github.com/QuingKhaos/factorio-mocks/issues)
for centralized tracking. Use the component selector to specify "Modpacks" as the affected component.

**Issue Categories:**

- **Configuration Bugs**: Incorrect or invalid modpack configurations
- **Build Problems**: Issues with automated processing or artifact generation
- **Feature Requests**: New modpack configurations or build improvements

### Pull Request Guidelines

1. **Use Conventional Commit Format** in PR titles
2. **Include Test Results**: Show modpacks tooling works as expected
3. **Document Breaking Changes**: Highlight any API or format changes

### Review Criteria

**Code Quality:**

- Follows Lua coding standards
- Includes appropriate error handling

**Testing:**

- Unit tests for new functionality
- Integration test compatibility

**Documentation:**

- Documentation updates for new features
- Inline code documentation

## Community Guidelines

### Code of Conduct

We follow the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). Key principles:

- **Be Respectful**: Treat all contributors with respect
- **Be Inclusive**: Welcome people of all backgrounds and experience levels
- **Be Collaborative**: Work together constructively
- **Be Professional**: Maintain professional conduct in all interactions

### Getting Help

- **New Contributors**: Look for `good-first-issue` labels
- **Questions**: Use [GitHub Discussions](https://github.com/QuingKhaos/factorio-mocks/discussions) in the main repository
- **Technical Issues**: Reference modpacks documentation and existing issues
- **Stuck?**: Ask for help in discussions or comment on relevant issues

## Security Considerations

### Reporting Security Issues

- **Never** create public issues for security vulnerabilities
- Use GitHub's private vulnerability reporting feature
- Follow responsible disclosure practices

## Useful Resources

- [Main Ecosystem Repository](https://github.com/QuingKhaos/factorio-mocks)
- [Factorio Mod Portal](https://mods.factorio.com/)
- [Factorio Mod List Format](https://wiki.factorio.com/Application_directory#User_data_directory)
- [Conventional Commits](https://www.conventionalcommits.org/)

Thank you for contributing to the Factorio Mocks Modpacks! 🏭⚙️
