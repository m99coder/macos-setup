# Opinionated macOS Setup

## General Defaults

**Reset System Update Badge**

In case you are not obliged or allowed to update to macOS Big Sur yet, you can reset the system preferences update notification badge and then turn of automatic updates, if wanted.

```bash
defaults write com.apple.systempreferences AttentionPrefBundleIDs 0
killall Dock
```

To undo this just re-enable automatic updates.

**Enable Tap-Clicking for Trackpad**

Go to `System Preferences` > `Trackpad` and enable `Tap to click`. Usually I increase the tracking speed to the third most right setting as well.

**Reset Dock Auto-Delay**

To make the Dock appearing and disappearing instantly:

```bash
defaults write com.apple.Dock autohide-delay -float 0
killall Dock
```

To undo this:

```bash
defaults delete com.apple.Dock autohide-delay
killall Dock
```

## XCode

Install Command Line Developer Tools like this:

```bash
xcode-select --install
```

## Homebrew

Install [Homebrew](https://brew.sh) – “The Missing Package Manager” for macOS like this:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Use the following command so that [Homebrew Cask](https://github.com/Homebrew/homebrew-cask) is tapped once.

## Shell

**iTerm2**

```bash
brew install iTerm2
```

Configure color preset under `Preferences` > `Profiles` > `Colors` as you wish. I prefer “Solarized Dark”.

**Oh My Zsh**

Oh My Zsh is installed by running the following command in your terminal:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Edit the `~/.zshrc` configuration file as needed. The default template can be found [here](https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/templates/zshrc.zsh-template).

I usually add the following config options and aliases:

```bash
# Don’t share history between terminal sessions
unsetopt share_history

# Use `nano` as default editor
export EDITOR='nano'

# To update, upgrade and cleanup brew, upgrade casks and run doctor in one command
alias brewup="brew update && brew upgrade && brew cleanup; brew upgrade --cask; brew doctor"

# To include directory entries whose names begin with a dot (.)
# To show results as list in long format
alias ll="ls -al"

# To reload configuration for current terminal session
alias refresh=". ~/.zshrc"

# To enforce English
alias git="LANG=C git"
```

**Zsh Theme**

I prefer [Powerlevel10k](https://github.com/romkatv/powerlevel10k) as my Zsh Theme.

```bash
brew install romkatv/powerlevel10k/powerlevel10k
echo 'source /usr/local/opt/powerlevel10k/powerlevel10k.zsh-theme' >> ~/.zshrc
```

Configure the prompt as you wish. At last I activate `node_version` and `go_version` in `~/.p10k.zsh` so that the respective versions are displayed on the right side of the prompt.

**Zsh Syntax Highlighting**

```bash
brew install zsh-syntax-highlighting
echo 'source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh' >> ~/.zshrc
```

## Applications

**Window Manager**

```bash
brew install --cask tiles
```

**Visual Studio Code**

```bash
brew install --cask visual-studio-code
```

**MenuMeters**

I prefer to see my network speed by utilizing MenuMeters and configuring it in a very basic way. Just enable “Network” as “Arrows and Throughput” with nothing else to display. Finally just choose black for both, transmit and receive, and a light grey for inactive.

```bash
brew install --cask menumeters
```

**Docker**

```bash
brew install --cask docker
```

## Programming Languages

**Node.js**

```bash
brew install node
```

**Go**

```bash
brew install go
mkdir -p $HOME/go/{bin,src}
```
