# Ubuntu Oh My Zsh Installation Guide

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [ZSH Installation](#zsh-installation)
3. [Oh My Zsh Installation](#oh-my-zsh-installation)
4. [Oh My Zsh Configuration](#oh-my-zsh-configuration)

## Prerequisites

Install the required packages for the installation:

```bash
sudo apt install wget curl git
```

## ZSH Installation

### 1. Install ZSH Package

```bash
sudo apt install zsh
```

### 2. Change Default Shell

```bash
chsh -s $(which zsh)
```

### 3. Verify Shell Configuration
- After system reboot or SSH reconnection, select option `2` in the initial configuration screen.
- Verify that ZSH is set as your default shell using the following command:
  ```bash
  echo $SHELL
  ```
- If the output shows `/bin/zsh`, ZSH is correctly set as your default shell.

## Oh My Zsh Installation

Choose and execute one of the following commands:

```bash
# Using curl
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# Using wget
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

## Oh My Zsh Configuration

### 1. Theme Configuration
- Open the configuration file: `vi ~/.zshrc`
- Change `ZSH_THEME="robbyrussell"` to `ZSH_THEME="af-magic"`

### 2. Install Powerline Fonts
Install the required fonts for the af-magic theme:

```bash
sudo apt install fonts-powerline
```

### 3. Install Plugins
Install commonly used plugins:

```bash
# Install zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Install zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Install fzf (Fuzzy Finder)
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### 4. Enable Plugins
Modify the plugins section in your `~/.zshrc` file as follows:

```bash
plugins=(
    git
    sudo
    colored-man-pages
    zsh-syntax-highlighting
    zsh-autosuggestions
    fzf
)
```

### 5. Apply Configuration
Apply the changes to your current session:

```bash
source ~/.zshrc
```

## Important Notes
- These settings apply only to the current user.
- Root user requires separate installation.
- It is recommended to install separately for each user.

## Configuration Files Location
- Zsh configuration file: `$HOME/.zshrc`
- Oh-my-Zsh configuration directory: `$HOME/.oh-my-zsh/`

## Additional Information
- The agnoster theme is one of the most popular themes for Oh My Zsh.
- The installed plugins provide the following features:
  - `git`: Enhanced git commands and status display
  - `sudo`: Press double ESC to add sudo before commands
  - `colored-man-pages`: Colored manual pages
  - `zsh-syntax-highlighting`: Command syntax highlighting
  - `zsh-autosuggestions`: Fish-like command suggestions
  - `fzf`: Fuzzy file finder and command history search

## Troubleshooting
- If the theme doesn't display correctly, ensure your terminal supports Powerline fonts
- If plugins don't work after installation, verify they are correctly listed in the plugins section
- For any issues with the configuration, you can reset by removing `.zshrc` and copying the template: `cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`
