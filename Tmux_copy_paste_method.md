# Using Copy Mode in tmux

## Basic Copy Operation
To copy text in `tmux`, you first need to enter **copy mode**.

### Basic Flow:
1. Press `Ctrl + b` then immediately press `[` → This enters copy mode
2. Use arrow keys to navigate to the text you want to copy
3. Press the spacebar to mark the starting point
4. Use arrow keys to move to the endpoint
5. Press `Enter` to complete the copy operation
6. The copied text is now in the tmux internal buffer → Paste with `Ctrl + b` then `]`

## Copying to System Clipboard (X11, Wayland, macOS)
By default, `tmux` doesn't integrate with the system clipboard, so tools like `xclip`, `xsel`, or `pbcopy` are needed.

### Ubuntu/Linux:
1. Install `xclip`:
   ```
   sudo apt install xclip
   ```
2. Add the following to your `.tmux.conf`:
   ```
   set-option -g set-clipboard on
   bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "xclip -selection clipboard -in"
   ```

### macOS:
Add to your `.tmux.conf`:
```
bind-key -T copy-mode-vi y send -X copy-pipe-and-cancel "pbcopy"
```

## How to Copy to System Clipboard (After Applying Settings)

### 1. Enter Copy Mode
- Press `Ctrl + b`
- Press `[` to enter copy mode

### 2. Select Text to Copy
- Navigate with arrow keys or mouse
- Press **spacebar** to set the starting point
- Move to the endpoint using arrow keys
- Press `y` to copy (this will copy to the system clipboard via `xclip` as configured)

> Note: Previously you would press `Enter`, but **now you press the `y` key** instead

---

## Verify Copy Success
- Press `Ctrl + Shift + V` to paste and verify
- Alternatively, try pasting into a text editor or browser address bar

---

## ✅ If Settings Are Not Applied
If your settings aren't working, reload your `.tmux.conf` with:
```
tmux source-file ~/.tmux.conf
```

---

### Reference
