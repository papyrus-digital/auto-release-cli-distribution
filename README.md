# Auto Release Note CLI

<div align="center">

```
 █████╗ ██████╗ ███╗   ██╗
██╔══██╗██╔══██╗████╗  ██║
███████║██████╔╝██╔██╗ ██║
██╔══██║██╔══██╗██║╚██╗██║
██║  ██║██║  ██║██║ ╚████║
╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═══╝
```

**Generate release notes automatically with AI-powered templates**

Built with ❤️ by [Papyrus Digital](https://www.autoreleasenote.com)

[![Platforms](https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-blue.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📖 Table of Contents

- [About](#-about)
- [Quick Install](#-quick-install)
- [Installation Methods](#-installation-methods)
- [Getting Started](#-getting-started)
- [Usage Guide](#-usage-guide)
- [Workflows](#-workflows)
- [Configuration](#-configuration)
- [Best Practices](#-best-practices)
- [Troubleshooting](#-troubleshooting)
- [Security & Verification](#-security--verification)
- [Support](#-support)

---

## 🎯 About

Auto Release Note CLI (`arn`) is a powerful command-line tool that automates the generation of release notes for your software projects using AI-powered templates. It analyzes your Git repository's commit history and creates professional, comprehensive release notes automatically.

### ✨ Key Features

- 🤖 **AI-Powered Generation**: Uses intelligent templates to create meaningful release notes
- 🔄 **Multiple Selection Methods**: Choose from branches, tags, commits, or pull requests
- 🎨 **Beautiful UI**: Interactive terminal interface with spinners and progress indicators
- 🔐 **Secure Authentication**: API token-based authentication for secure operations
- 🧩 **Template Support**: Multiple release note templates to choose from
- 💻 **Cross-Platform**: Works on Linux, macOS, and Windows

### 🖥 Supported Platforms

- **macOS**: amd64 (Intel), arm64 (Apple Silicon)
- **Linux**: amd64, arm64
- **Windows**: amd64

---

## 🚀 Quick Install

### macOS (Homebrew)

```bash
brew tap papyrus-digital/auto-release-cli-distribution
brew install arn
```

### Linux

```bash
# Download the latest release
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/latest/download/arn_linux_amd64.tar.gz

# Extract and install
tar -xzf arn_linux_amd64.tar.gz
sudo mv arn /usr/local/bin/
```

### Windows (Scoop)

```bash
scoop bucket add arn https://github.com/papyrus-digital/auto-release-cli-distribution
scoop install arn
```

### Verify Installation

```bash
arn version
```

---

## 📥 Installation Methods

### macOS

#### Homebrew (Recommended)

```bash
# Add the tap
brew tap papyrus-digital/auto-release-cli-distribution

# Install
brew install arn

# Verify
arn version
```

#### Direct Download

```bash
# Download the latest release (Apple Silicon)
VERSION="v1.0.0"  # Replace with actual version
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/arn_${VERSION}_darwin_arm64.tar.gz

# Or for Intel Macs
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/arn_${VERSION}_darwin_amd64.tar.gz

# Extract and install
tar -xzf arn_${VERSION}_darwin_*.tar.gz
sudo mv arn /usr/local/bin/

# Make executable
chmod +x /usr/local/bin/arn
```

### Linux

#### Direct Download

```bash
# Download the latest release
VERSION="v1.0.0"  # Replace with actual version
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/arn_${VERSION}_linux_amd64.tar.gz

# Download checksums for verification (optional)
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/arn_${VERSION}_checksums.txt

# Verify checksum (optional)
sha256sum -c arn_${VERSION}_checksums.txt --ignore-missing

# Extract and install
tar -xzf arn_${VERSION}_linux_amd64.tar.gz
sudo mv arn /usr/local/bin/

# Make executable
chmod +x /usr/local/bin/arn
```

### Windows

#### Scoop (Recommended)

```powershell
# Add the bucket
scoop bucket add arn https://github.com/papyrus-digital/auto-release-cli-distribution

# Install
scoop install arn

# Verify
arn version
```

#### Direct Download

1. Visit [GitHub Releases](https://github.com/papyrus-digital/auto-release-cli-distribution/releases)
2. Download the latest `arn_*_windows_amd64.zip` file
3. Extract the ZIP file
4. If Windows SmartScreen shows a warning:
   - Click **"More info"**
   - Click **"Run anyway"**
   - Or: Right-click the `.exe` → Properties → Check **"Unblock"** → OK
5. Add the extracted directory to your PATH:
   - Press `Win + X` → System → Advanced system settings
   - Click "Environment Variables"
   - Under "System variables", find "Path" and click "Edit"
   - Click "New" and add the directory path
   - Click "OK" on all dialogs

---

## 🎬 Getting Started

### Step 1: Initialize Configuration

After installation, initialize the CLI in your project:

```bash
arn init
```

You'll be prompted for:

1. **API Token**: Your authentication token
   - Get one at [autoreleasenote.com](https://www.autoreleasenote.com)
   - The token is stored securely in `.autorelease/config.json`

2. **Project Name**: Your project identifier
   - Format: `organization/repository`
   - Example: `papyrus-digital/my-project`

**Example:**

```bash
$ arn init

╔══════════════════════════════════════════════════╗
║    Welcome to Auto Release Note CLI v1.0.0      ║
╚══════════════════════════════════════════════════╝

? Enter your API token: ****************************
? Enter your project name: papyrus-digital/my-project

✓ Configuration saved successfully!
✓ Authentication successful!
```

### Step 2: Generate Release Notes

Navigate to your Git repository and run:

```bash
arn generate
```

The CLI will guide you through an interactive process:

1. **Choose Selection Method**: Branch, Tags, or Commits
2. **Select Range**: Pick your branches, tags, or commit range
3. **Review Commits**: Select which commits to include
4. **Choose Template**: Pick a release note template
5. **Generate**: Get your release notes URL

---

## 📚 Usage Guide

### Commands

#### `arn init`

Initialize the configuration for your project.

```bash
arn init
```

Creates `.autorelease/config.json` with your API token and project name.

---

#### `arn generate`

Generate release notes interactively.

```bash
arn generate
```

**Prerequisites:**
- Must run `arn init` first
- Must be in a Git repository
- API token must be valid

**Selection Methods:**

##### 1. Branch Selection
Shows all branches in your repository. Select one to generate notes from its commits.

```
? Select a branch:
  main
  develop
> feature/new-ui
  release/v1.0.0
```

##### 2. Tag Selection
Choose "from" and "to" tags to define a release range.

```
? Select FROM tag:
  (none)
  v0.9.0
> v1.0.0

? Select TO tag:
  v1.1.0
> (HEAD)
```

##### 3. Commit Selection
Manually specify commit hashes for custom ranges.

```
? Enter FROM commit hash: abc123def456
? Enter TO commit hash: HEAD
```

**Commit Review:**

```
Found 15 commits:

[x] feat: Add new dashboard UI (abc123d)
[x] fix: Resolve login issue (def456e)
[ ] chore: Update dependencies (ghi789f)
[x] docs: Update README (jkl012g)

Use ↑/↓ to navigate, Space to toggle, Enter to confirm
```

**Template Selection:**

```
? Select a template:
> Standard Release Notes
  Detailed Changelog
  Executive Summary
  Technical Release Notes
  Marketing Release
```

**Result:**

```
✓ Generating release notes...
✓ Release notes generated successfully!

🧩 Your release notes are ready:
https://www.autoreleasenote.com/view/abc123xyz
```

---

#### `arn version`

Display version information.

```bash
arn version
```

**Output:**

```
Auto Release Note CLI
Version: v1.0.0
Build Date: 2024-01-15
Platform: darwin/arm64

For more information:
https://www.autoreleasenote.com
```

---

## 🔄 Workflows

### Workflow 1: Release from Tags

Perfect for versioned releases:

```bash
# Initialize (first time only)
arn init

# Generate release notes between tags
arn generate
# → Select: Tags
# → From: v1.0.0
# → To: v1.1.0
```

### Workflow 2: Feature Branch Release

For feature-based releases:

```bash
arn generate
# → Select: Branch
# → Choose: feature/new-ui
# → Review and select commits
# → Choose template
```

### Workflow 3: Custom Commit Range

For specific commit ranges:

```bash
# Find your commit hashes
git log --oneline

# Generate notes
arn generate
# → Select: Commits
# → From: abc123d
# → To: def456e
```

### Workflow 4: Quick Latest Changes

Get notes for recent changes since last tag:

```bash
arn generate
# → Select: Tags
# → From: (last tag)
# → To: (HEAD)
```

---

## ⚙️ Configuration

### Configuration File

Location: `.autorelease/config.json`

```json
{
  "token": "your_api_token_here",
  "project": "organization/repository"
}
```

### Environment Variables

You can also configure using environment variables:

```bash
export ARN_API_TOKEN="your_token_here"
export ARN_PROJECT="organization/repository"

arn generate
```

### Configuration Priority

1. Environment variables (highest)
2. Configuration file (`.autorelease/config.json`)
3. Command-line flags (if applicable)

---

## ✅ Best Practices

### 1. Commit Message Format

Use conventional commit format for best results:

```
type(scope): description

Types:
- feat: New feature
- fix: Bug fix
- docs: Documentation changes
- chore: Maintenance tasks
- refactor: Code refactoring
- test: Testing updates
- perf: Performance improvements
```

**Examples:**
```
feat(auth): Add OAuth2 authentication
fix(ui): Resolve mobile layout issues
docs(readme): Update installation instructions
```

### 2. Generate Regularly

Create release notes:
- After each sprint
- Before each release
- For major feature launches

### 3. Template Selection

Choose templates based on your audience:

| Template | Best For | Details |
|----------|----------|---------|
| **Standard Release Notes** | General purpose | Balanced detail for most audiences |
| **Detailed Changelog** | Technical teams | Complete commit history |
| **Executive Summary** | Stakeholders | High-level overview |
| **Technical Release Notes** | Developers | API changes, breaking changes |
| **Marketing Release** | End users | Customer-facing features |

### 4. Commit Selection

Be selective:
- ✅ Include user-facing changes
- ✅ Include important fixes
- ❌ Exclude minor formatting changes
- ❌ Exclude dependency updates (unless significant)

### 5. Version Control

- Tag releases consistently
- Use semantic versioning (`v1.0.0`)
- Keep tags synchronized with releases

---

## 🔧 Troubleshooting

### Installation Issues

#### macOS Gatekeeper Warning

**Problem:** macOS blocks the binary when first running it.

**Solution:**

**Option 1: Remove quarantine attribute (recommended)**
```bash
xattr -d com.apple.quarantine /usr/local/bin/arn
```

**Option 2: System Preferences**
1. Go to System Preferences → Security & Privacy
2. Click "Open Anyway" if prompted
3. Or right-click the binary and select "Open"

**Note:** Distribution without Apple Developer account is fully supported. GPG signatures provide security verification. Apple code signing is optional and only improves UX.

---

#### Windows SmartScreen Warning

**Problem:** Windows shows a SmartScreen warning.

**Solution:**

1. Click **"More info"** on the warning dialog
2. Click **"Run anyway"**

**Or:**
1. Right-click the `.exe` file
2. Select **Properties**
3. Check **"Unblock"**
4. Click **OK**

**Note:** Distribution without code signing certificate is fully supported. GPG signatures provide security verification. Windows Authenticode signing is optional.

---

#### Permission Denied (Linux/macOS)

**Problem:** "Permission denied" when running `arn`.

**Solution:**
```bash
# Make executable
chmod +x /usr/local/bin/arn

# Or if you installed elsewhere
chmod +x /path/to/arn
```

---

#### Command Not Found

**Problem:** Terminal doesn't recognize `arn` command.

**Solution:**

**Verify installation:**
```bash
which arn  # Linux/macOS
where arn  # Windows
```

**Add to PATH if needed:**

**Linux/macOS:**
```bash
# Add to ~/.bashrc or ~/.zshrc
export PATH="/usr/local/bin:$PATH"

# Reload shell
source ~/.bashrc  # or ~/.zshrc
```

**Windows:**
1. Press `Win + X` → System
2. Click "Advanced system settings"
3. Click "Environment Variables"
4. Under "System variables", find "Path"
5. Click "Edit" → "New"
6. Add the directory containing `arn.exe`
7. Click OK on all dialogs
8. Restart your terminal

---

### Usage Issues

#### "Not a git repository"

**Problem:** Running `arn generate` outside a Git repository.

**Solution:**
```bash
# Ensure you're in a Git repository
git status

# Or initialize one
git init
```

---

#### "Invalid API token"

**Problem:** API token is expired or invalid.

**Solution:**
```bash
# Re-initialize with a new token
arn init

# Or manually edit the config
nano .autorelease/config.json
```

---

#### "No commits found"

**Problem:** The selected range doesn't contain commits.

**Solution:**
```bash
# Check tag names
git tag -l

# Check branch names
git branch -a

# Verify commits exist
git log --oneline
```

---

#### "Configuration not found"

**Problem:** Running `arn generate` before initialization.

**Solution:**
```bash
# Initialize first
arn init

# Then generate
arn generate
```

---

#### "Network error"

**Problem:** Cannot connect to the API.

**Solution:**
1. Check your internet connection
2. Verify API status at [autoreleasenote.com](https://www.autoreleasenote.com)
3. Check firewall/proxy settings
4. Ensure your API token is valid

---

#### Template Selection Not Showing

**Problem:** No templates available to select.

**Solution:**
1. Verify API token is valid
2. Check account permissions at [autoreleasenote.com](https://www.autoreleasenote.com)
3. Contact support if issue persists

---

## 🔐 Security & Verification

### Verify Checksums

All releases include SHA256 checksums for verification.

**Linux/macOS:**
```bash
# Download checksum file
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/v1.0.0/arn_v1.0.0_checksums.txt

# Verify
sha256sum -c arn_v1.0.0_checksums.txt --ignore-missing
```

**Windows PowerShell:**
```powershell
# Calculate hash
Get-FileHash -Algorithm SHA256 arn.exe

# Compare with checksums.txt
```

### Verify GPG Signature

All releases are signed with GPG for security.

```bash
# Import GPG public key (first time only)
curl -s https://raw.githubusercontent.com/papyrus-digital/auto-release-cli-distribution/main/GPG_PUBLIC_KEY.asc | gpg --import

# Download signature file
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/v1.0.0/arn_v1.0.0_checksums.txt.sig

# Verify signature
gpg --verify arn_v1.0.0_checksums.txt.sig arn_v1.0.0_checksums.txt
```

**Expected output:**
```
gpg: Good signature from "Papyrus Digital Release Bot <release@papyrus.digital>"
```

---

## 💡 Advanced Usage

### Scripting and Automation

Integrate `arn` into CI/CD pipelines using environment variables:

```bash
#!/bin/bash
# Example: Automated release notes generation

# Set credentials via environment
export ARN_API_TOKEN="${SECRET_ARN_TOKEN}"
export ARN_PROJECT="myorg/myrepo"

# Get latest tag
LATEST_TAG=$(git describe --tags --abbrev=0)

# Generate release notes (interactive for now)
# Non-interactive mode coming in future releases
arn generate
```

**Note:** Non-interactive/CLI flags mode is planned for future releases.

### Getting Help

**In-CLI:**
```bash
# General help
arn --help

# Command-specific help
arn init --help
arn generate --help
```

**Online:**
- **Documentation**: [autoreleasenote.com/docs](https://www.autoreleasenote.com/docs)
- **Issues**: [GitHub Issues](https://github.com/papyrus-digital/auto-release-cli/issues)
- **Email**: support@papyrus.digital

---

## 📦 Releases

All releases are available in the [Releases](https://github.com/papyrus-digital/auto-release-cli-distribution/releases) section.

Each release includes:
- ✅ Cross-platform binaries (Linux, macOS, Windows)
- ✅ SHA256 checksums
- ✅ GPG signatures
- ✅ Archive files (`.tar.gz` for Unix, `.zip` for Windows)
- ✅ Documentation (README, installation guides)

---

## 🆘 Support

### Resources

- **Website**: [autoreleasenote.com](https://www.autoreleasenote.com)
- **Documentation**: [autoreleasenote.com/docs](https://www.autoreleasenote.com/docs)
- **GitHub Issues**: [Report bugs or request features](https://github.com/papyrus-digital/auto-release-cli/issues)
- **Email Support**: support@papyrus.digital

### Community

- Follow us on Twitter: [@papyrusdigital](https://twitter.com/papyrusdigital)
- Join our community forum
- Subscribe to our newsletter for updates

---

## 📄 License

This distribution repository contains binaries and manifests. For source code and license information, please contact Papyrus Digital.

---

<div align="center">

**Made with ❤️ by the Papyrus Digital Team**

[Website](https://www.autoreleasenote.com) • [Documentation](https://www.autoreleasenote.com/docs) • [Support](mailto:support@papyrus.digital)

</div>