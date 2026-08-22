# Bindfort CLI

Account-free installed-tree vulnerability scanning for MCP server dependencies.

The Free CLI runs locally and checks the dependency versions actually installed on disk against public OSV advisory data. It does not require a Bindfort account or API key.

## Download

Download the archive for your platform from the [latest release](https://github.com/bindfort/cli/releases/latest):

- Windows x64
- Linux x64 or ARM64
- macOS Intel or Apple Silicon

Every release includes `checksums.sha256`. The public package contains the scanner-only binary, not the Bindfort gateway or its source code.

On macOS or Linux, install and update it with Homebrew:

```sh
brew install bindfort/tap/bindfort
```

## Run a scan

Install the MCP server or project dependencies first, then point Bindfort at the installed tree:

```text
bindfort scan /path/to/installed/mcp-server
```

From an npm project directory:

```text
bindfort scan .
```

For JSON output or a CI failure threshold:

```text
bindfort scan . --format json
bindfort scan . --fail-on high
```

The default output reports the number of installed dependencies checked and any matched advisory IDs, packages, installed versions, and normalized severities.

## Privacy

Dependency discovery runs locally. Source files and lockfiles are not uploaded. The CLI sends normalized package names, versions, and ecosystems to the public OSV API to look up advisory matches.

## Scope and limitations

- npm installed trees are supported when `npm` and `node_modules` are available.
- Local Go binaries and supported Python environments can also be inspected when their runtime tooling is available.
- Advisory matching is a point-in-time check of public data, not a guarantee that a package or MCP server is safe.
- The Free package scans dependencies. Gateway policy enforcement and receipt evidence are separate Bindfort packages.

Pricing and product availability: [bindfort.com/pricing](https://bindfort.com/pricing)

Security reports: [security@bindfort.com](mailto:security@bindfort.com)
