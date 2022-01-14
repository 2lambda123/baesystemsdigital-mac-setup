# mac-setup

## Prerequisites

* MDM enrolled Mac

---

1. Set system architecture

```
if [[ "$( uname -m )" == "arm64" ]]; then
  export APPLE_SILICON="true"
  export BREW_BINARY="/opt/homebrew/bin/brew"
else
  export APPLE_SILICON="false"
  export BREW_BINARY="brew"
fi
```

2. Install Xcode

```
xcode-select --install
```

3. Install Rosetta 2 if Apple Silicon

```
if [[ "${APPLE_SILICON}" == "true" ]]; then
  softwareupdate --install-rosetta --agree-to-license
fi
```

4. Install Homebrew

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

5. Clone this repository

```
git clone https://github.com/baesystemsai/mac-setup.git
```

6. Run Brew

```
${BREW_BINARY} bundle --file mac-setup/Brewfile

# If you're a developer, also run this
${BREW_BINARY} bundle --file mac-setup/Brewfile.developer
```
