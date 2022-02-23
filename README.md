# mac-setup

## Baseline Install

1. Set system architecture

```bash
if [[ "$( uname -m )" == "arm64" ]]; then
  export APPLE_SILICON="true"
  export BREW_BINARY="/opt/homebrew/bin/brew"
else
  export APPLE_SILICON="false"
  export BREW_BINARY="brew"
fi
```

2. Install Xcode

```bash
xcode-select --install
```

3. Install Rosetta 2 if Apple Silicon

```bash
if [[ "${APPLE_SILICON}" == "true" ]]; then
  softwareupdate --install-rosetta --agree-to-license
fi
```

4. Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

5. Clone this repository

```bash
git clone https://github.com/baesystemsdigitalintelligence/mac-setup.git
```

6. Run Brew

```bash
${BREW_BINARY} bundle --file mac-setup/Brewfile
```

## Developer Tooling

1. Run Brew

```bash
${BREW_BINARY} bundle --file mac-setup/Brewfile.developer
```
