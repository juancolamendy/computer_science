# Tmux

Quick setup for macOS, Ubuntu, and AlmaLinux / RHEL.

---

## Install

### macOS

```bash
brew install tmux git
```

### Ubuntu

```bash
sudo apt update
sudo apt install -y tmux git xclip
```

### AlmaLinux / RHEL

```bash
sudo dnf install -y tmux git xclip
```

---

## Setup (all platforms)

From this directory:

```bash
# Install TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Backup existing config (if any), then install
cp ~/.tmux.conf ~/.tmux.conf.bak 2>/dev/null || true
cp .tmux.conf.example ~/.tmux.conf

# Start tmux, then reload (or open a new session)
tmux new-session -s main
# Inside tmux:
#   Ctrl-a r          reload config
#   Ctrl-a I          install plugins (prefix, then capital I)
```

Plugins installed by this config: `tmux-sensible`, `tmux-resurrect`, `tmux-continuum`.

---

## Verify

```bash
tmux -V
# Expect 3.0+ (3.3+ recommended)

ls ~/.tmux/plugins/tpm/
ls ~/.tmux/plugins/
# Expect: tpm/, tmux-sensible/, tmux-resurrect/, tmux-continuum/

# Clipboard (macOS)
echo "test" | pbcopy && pbpaste

# Clipboard (Linux)
echo "test" | xclip -selection clipboard
xclip -selection clipboard -o
```

Quick binding check inside tmux:

| Binding | Action |
|---------|--------|
| `Ctrl-a h/j/k/l` | Navigate panes |
| `Ctrl-a \|` | Split horizontally |
| `Ctrl-a -` | Split vertically |
| `Ctrl-a c` | New window |

---

## Key bindings

| Binding | Action |
|---------|--------|
| `Ctrl-a` | Prefix |
| `Ctrl-a I` | Install plugins |
| `Ctrl-a r` | Reload config |
| `Ctrl-a \|` | Split pane horizontally |
| `Ctrl-a -` | Split pane vertically |
| `Ctrl-a c` | Create new window |
| `Ctrl-a h/j/k/l` | Navigate panes (vim-style) |
| `Ctrl-a H/J/K/L` | Resize panes |
| `Ctrl-a P` | Rename current pane |
| `Ctrl-a C-p` | Toggle sync panes |
| `Ctrl-a [` | Enter copy mode |
| `v` / `y` | Start selection / copy (copy mode) |
| `Ctrl-a d` | Detach |

### First session

```bash
tmux new-session -s main

# Ctrl-a |     split
# Ctrl-a h/l   move between panes
# Ctrl-a c     new window
# Ctrl-a 0/1   switch windows
# Ctrl-a d     detach

tmux attach -t main
```

---

## Troubleshooting

### `command not found: tmux`

```bash
# macOS
brew install tmux

# Ubuntu
sudo apt install tmux

# AlmaLinux / RHEL
sudo dnf install tmux
```

On macOS, confirm Homebrew is on `PATH`:

```bash
which tmux
# Intel: /usr/local/bin/tmux
# Apple Silicon: /opt/homebrew/bin/tmux
```

### Plugins not installing

```bash
ls ~/.tmux/plugins/tpm/
~/.tmux/plugins/tpm/bin/install_plugins

# Or reinstall TPM
rm -rf ~/.tmux/plugins/tpm
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

### Copy/paste not working

```bash
# macOS
echo test | pbcopy && pbpaste

# Linux
echo test | xclip -selection clipboard
xclip -selection clipboard -o

# Ubuntu: sudo apt install xclip
# AlmaLinux: sudo dnf install xclip
```

### Colors look wrong

```bash
echo $TERM
# Inside tmux: tmux-256color
# Outside: xterm-256color (or similar)

export TERM=xterm-256color
```

Use a terminal with truecolor support (e.g. Ghostty, iTerm2).

### Config won't reload

```bash
tmux -f ~/.tmux.conf source ~/.tmux.conf
# Fix any reported line numbers, then retry
```

---

## Resources

- [tmux man page](https://man.openbsd.org/tmux)
- [TPM](https://github.com/tmux-plugins/tpm)
- [tmux-plugins](https://github.com/tmux-plugins)
- [tmux wiki](https://github.com/tmux/tmux/wiki)
