# NEBULA CLI Introduction

Welcome to **NEBULA CLI**, the official command-line interface for interacting with **Zyxel Nebula OpenAPI**. Designed for developers and platform engineers, NEBULA CLI brings the power of the Nebula Control Center directly to your terminal—and integrates seamlessly with AI agents out of the box with zero Model Context Protocol (MCP) server setup overhead.

---

## Key Features

* **AI Agent Ready:** Can be directly utilized by AI agents, eliminating configuration complexity and MCP server setup overhead.
* **Under-the-Hood API Integration:** Seamlessly translates your terminal commands into efficient calls using the underlying Zyxel Nebula OpenAPI.
* **Environment-Based Authentication:** Securely manages your access credentials using standard environment variables.
* **Self-Documenting Interface:** Built-in help options ensure you always know what commands and flags are available at a glance.

---

## Installation & Setup

### 1. Download the Compressed Binary
1. Go to the [Nebula CLI Releases Page](https://github.com/ZyxelNetworks/NebulaOpenAPI/releases/latest).
2. Download the compressed archive for Windows x64: `nebula-cli-x64.zip`.
### 2. Verify File Integrity (Optional)
To ensure your download has not been corrupted or tampered with, you can check its SHA-256 hash in PowerShell:
```powershell
Get-FileHash -Path "nebula-cli-x64.zip" -Algorithm SHA256
```
Compare the resulting hash against the value published in the release notes. Extract the executable once verified and place it in a directory included in your system's `PATH`.

### 3. Obtain Your API Key
Before using the CLI, you must obtain an active API key from the **Nebula Control Center**. 

### 4. Configure Your Environment Variable
Because GUI applications and certain desktop environments do not inherit temporary environment variables set in individual command prompt windows, you should configure `NEBULA_API_KEY` at the user environment level.

You can open the Windows Environment Variables editor instantly by pressing `Win + R` and running:
```cmd
rundll32 sysdm.cpl,EditEnvironmentVariables
```

Alternatively, configure it via your active terminal session:
**PowerShell:**
```powershell
$env:NEBULA_API_KEY="your_api_key_here"
```

**Command Prompt (CMD):**
```cmd
set NEBULA_API_KEY=your_api_key_here
```

---

## Usage & Discovery

### Exploring Available Options
NEBULA CLI features built-in documentation. If you are unsure about available commands, arguments, or flags, simply append the `--help` option:

```cmd
nebula-cli.exe --help
```

For command-specific help and available sub-options, pass `--help` to any subcommand:

```cmd
nebula-cli.exe [subcommand] --help
