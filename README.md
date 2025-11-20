# Auto Release CLI Distribution

This repository contains distribution artifacts for [Auto Release CLI](https://github.com/papyrus-digital/auto-release-cli).

## About

Auto Release CLI is a powerful command-line tool that automates the generation of release notes for your software projects using AI-powered templates.

## Installation

See [INSTALL.md](./INSTALL.md) for detailed installation instructions for all supported platforms.

### Quick Install

**macOS (Homebrew):**
```bash
brew tap papyrus-digital/auto-release-cli-distribution/homebrew
brew install auto-release-cli
```

**Linux:**
```bash
curl -LO https://github.com/papyrus-digital/auto-release-cli-distribution/releases/latest/download/auto-release-cli_*_linux_amd64.tar.gz
tar -xzf auto-release-cli_*_linux_amd64.tar.gz
sudo mv releasenote /usr/local/bin/
```

**Windows (Scoop):**
```bash
scoop bucket add auto-release-cli https://github.com/papyrus-digital/auto-release-cli-distribution/scoop-bucket
scoop install auto-release-cli
```

## Repository Structure

```
├── homebrew/          # Homebrew tap formula
│   └── Formula/
├── scoop/             # Scoop bucket manifests
├── winget/            # Windows Package Manager manifests
├── INSTALL.md         # Installation guide
└── README.md          # This file
```

## Releases

All releases are available in the [Releases](https://github.com/papyrus-digital/auto-release-cli-distribution/releases) section.

Each release includes:
- Cross-platform binaries (Linux, macOS, Windows)
- Checksums (SHA256)
- GPG signatures
- Archive files (tar.gz for Unix, zip for Windows)

## Verification

All releases are signed with GPG. See [INSTALL.md](./INSTALL.md) for verification instructions.

## Support

- **Documentation**: [https://autoreleasenote.com/docs](https://autoreleasenote.com/docs)
- **Issues**: [GitHub Issues](https://github.com/papyrus-digital/auto-release-cli/issues)
- **Email**: support@papyrus.digital

## License

This distribution repository contains only binaries and manifests. The source code is available in the [private repository](https://github.com/papyrus-digital/auto-release-cli).

---

Built with ❤️ by [Papyrus Digital](https://autoreleasenote.com)

