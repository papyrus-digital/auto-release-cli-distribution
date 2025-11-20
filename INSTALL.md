# Installation Guide

## Auto Release CLI

Generate release notes automatically with AI-powered templates.

### Supported Platforms

- macOS (amd64, arm64)
- Linux (amd64, arm64)
- Windows (amd64)

---

## Installation Methods

### macOS (Homebrew)

```bash
brew tap papyrus-digital/auto-release-cli-distribution/homebrew
brew install auto-release-cli
```

### Linux (Direct Download)

```bash
# Download the latest release
VERSION="v1.0.0"  # Replace with actual version
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/auto-release-cli_${VERSION}_linux_amd64.tar.gz

# Download checksums
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/${VERSION}/auto-release-cli_${VERSION}_checksums.txt

# Verify checksum
sha256sum -c auto-release-cli_${VERSION}_checksums.txt

# Extract and install
sudo tar -C /usr/local/bin -xzf auto-release-cli_${VERSION}_linux_amd64.tar.gz releasenote
```

### Windows (Scoop)

```bash
scoop bucket add auto-release-cli https://github.com/papyrus-digital/auto-release-cli-distribution/scoop-bucket
scoop install auto-release-cli
```

### Windows (Direct Download)

1. Download the latest release from [GitHub Releases](https://github.com/papyrus-digital/auto-release-cli-distribution/releases)
2. Extract the ZIP file
3. If Windows SmartScreen shows a warning:
   - Click "More info"
   - Click "Run anyway"
   - Or: Right-click the .exe → Properties → Unblock
4. Add the extracted directory to your PATH

---

## Verification

### Verify Checksums

```bash
# Download checksums file
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/v1.0.0/auto-release-cli_v1.0.0_checksums.txt

# Verify (Linux/macOS)
sha256sum -c auto-release-cli_v1.0.0_checksums.txt

# Verify (Windows PowerShell)
Get-FileHash -Algorithm SHA256 releasenote-windows-amd64.exe
```

### Verify GPG Signature

```bash
# Import GPG public key (first time only)
curl -s https://github.com/papyrus-digital.gpg | gpg --import

# Download signature file
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/download/v1.0.0/auto-release-cli_v1.0.0_checksums.txt.asc

# Verify signature
gpg --verify auto-release-cli_v1.0.0_checksums.txt.asc auto-release-cli_v1.0.0_checksums.txt
```

---

## Troubleshooting

### macOS Gatekeeper

**Important:** You can distribute macOS binaries **without** an Apple Developer account. The binaries are signed with GPG (not Apple code signing), which provides security verification.

If macOS shows a Gatekeeper warning when running the binary:

1. **Remove quarantine attribute:**
   ```bash
   xattr -d com.apple.quarantine /usr/local/bin/releasenote
   ```

2. **Allow in System Preferences:**
   - Go to System Preferences > Security & Privacy
   - Click "Open Anyway" if prompted
   - Or right-click the binary and select "Open"

**Note:** 
- ✅ **Distribution without Apple Developer account is fully supported**
- ✅ GPG signatures provide security verification
- ✅ Homebrew can distribute unsigned binaries
- ℹ️ Apple code signing is **optional** - it improves UX by eliminating Gatekeeper warnings, but is not required
- 💰 Apple Developer account ($99/year) is only needed if you want code signing/notarization

### Windows SmartScreen Warning

**Important:** You can distribute Windows binaries **without** a code signing certificate. The binaries are signed with GPG (not Windows Authenticode), which provides security verification.

If Windows shows a SmartScreen warning:

1. **Click "More info"** on the warning dialog
2. **Click "Run anyway"**
3. **Or**: Right-click the .exe file → Properties → Unblock → OK

**Note:**
- ✅ **Distribution without code signing certificate is fully supported**
- ✅ GPG signatures provide security verification
- ✅ Scoop/Chocolatey can distribute unsigned binaries
- ℹ️ Windows Authenticode signing is **optional** - it improves UX by eliminating SmartScreen warnings, but is not required
- 💰 Code signing certificates ($200-400/year) are only needed if you want Authenticode signing

### Permission Denied

If you get a "permission denied" error:

```bash
# Make executable (Linux/macOS)
chmod +x /usr/local/bin/releasenote
```

### Command Not Found

If the command is not found after installation:

1. Verify the binary is in your PATH:
   ```bash
   which releasenote  # Linux/macOS
   where releasenote   # Windows
   ```

2. Add to PATH if needed:
   - Linux/macOS: Add `/usr/local/bin` to your PATH in `~/.bashrc` or `~/.zshrc`
   - Windows: Add the installation directory to System Environment Variables

---

## Quick Start

After installation, initialize the CLI:

```bash
releasenote init
```

Then generate release notes:

```bash
releasenote generate
```

For more information, visit [https://autoreleasenote.com](https://autoreleasenote.com)

