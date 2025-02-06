
202411141419

# Complete Tmux Installation Guide
This guide covers the installation of tmux, TPM (Tmux Plugin Manager), and setting up a fully configured tmux environment.

## 1. Install Required Packages

First, ensure your system is up to date and install necessary packages:

```bash
# Update system
sudo apt update
sudo apt upgrade

# Install required packages
sudo apt install git xclip tmux
```

## 2. Install TPM (Tmux Plugin Manager)

Install TPM by cloning the repository:

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

## 3. Create tmux Configuration

Create and populate the tmux configuration file:

```bash
# Create tmux.conf file
touch ~/.tmux.conf

# Open with your preferred editor (e.g., nano, vim)
nvim ~/.tmux.conf
```

Copy and paste the following configuration:
```
# Core Options
set -g mouse on
set -g default-terminal "tmux-256color"
set-option -sa terminal-overrides ",xterm*:Tc"

# Window and Pane Settings
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on
set-window-option -g mode-keys vi

# Key Bindings
bind -n M-H previous-window
bind -n M-L next-window
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi C-v send-keys -X rectangle-toggle
bind-key -T copy-mode-vi y send-keys -X copy-selection-and-cancel
bind '"' split-window -v -c "#{pane_current_path}"
bind % split-window -h -c "#{pane_current_path}"

# Plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'christoomey/vim-tmux-navigator'
# set -g @plugin 'catppuccin/tmux'
set -g @plugin 'dreamsofcode-io/catppuccin-tmux'

set -g automatic-rename on
set -g automatic-rename-format '#{b:pane_current_path}'

# Initialize TPM (keep this line at the very end)
run '~/.tmux/plugins/tpm/tpm'

```


```

## 4. Load Configuration

If tmux is already running:

```bash
# Reload tmux configuration
tmux source-file ~/.tmux.conf
```

## 5. Install Plugins

1. Start tmux if not already running:
```bash
tmux
```

2. Install plugins by pressing:
- `prefix` + `I` (capital i)
  - Note: The default prefix is `Ctrl + b`

Wait for the installation to complete. You'll see a message when it's done.

## 6. Basic Usage

### Copy/Paste:
- Enter copy mode: `prefix` + `[`
- Select text: 
  - Mouse: Click and drag
  - Keyboard: Move cursor with vi keys, press `v` to start selection
- Copy: 
  - Mouse: Release selection
  - Keyboard: Press `y`

### Window Management:
- New window: `prefix` + `c`
- Next window: `Alt` + `L` or `prefix` + `n`
- Previous window: `Alt` + `H` or `prefix` + `p`

### Pane Management:
- Split vertical: `prefix` + `%`
- Split horizontal: `prefix` + `"`
- Navigate panes: `prefix` + arrow keys

## 7. Troubleshooting

If clipboard isn't working:

1. Verify xclip installation:
```bash
xclip -version
```

2. Test clipboard outside tmux:
```bash
echo "test" | xclip -selection clipboard
xclip -selection clipboard -o  # Should output "test"
```

3. Check for X11 display:
```bash
echo $DISPLAY
```

4. If using SSH, ensure X11 forwarding is enabled:
```bash
ssh -X user@host
```

## 8. Uninstallation (if needed)

To completely remove tmux and start fresh:

```bash
# Remove tmux
sudo apt remove tmux
sudo apt purge tmux

# Remove configuration
rm -rf ~/.tmux
rm -rf ~/.tmux.conf*

# Remove TPM
rm -rf ~/.tmux/plugins/

sudo apt clean
sudo apt update
```

Then you can start again from step 1 if needed.





---
### Reference

