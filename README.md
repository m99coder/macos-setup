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

```
xcode-select --install
```

## Shell

**Oh My Zsh**

Oh My Zsh is installed by running the following command in your terminal:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
