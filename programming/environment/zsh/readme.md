# Zsh

Quick setup for macOS, Ubuntu, and AlmaLinux / RHEL — Oh My Zsh, Powerlevel10k, and personal aliases from this folder.

---

## Install

### macOS

```bash
brew install zsh
# Or use system zsh: /bin/zsh (already present)

# Set default (pick the path that exists)
chsh -s /opt/homebrew/bin/zsh   # Apple Silicon Homebrew
# chsh -s /usr/local/bin/zsh    # Intel Homebrew
# chsh -s /bin/zsh              # system
```

### Ubuntu

```bash
sudo apt update
sudo apt install -y zsh
chsh -s "$(which zsh)"
```

### AlmaLinux / RHEL

```bash
sudo dnf install -y zsh
chsh -s "$(which zsh)"
```

Restart the terminal or run `exec zsh`.

---

## Setup (all platforms)

### 1. Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 2. Theme & plugins

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting"

git clone https://github.com/zsh-users/zsh-autosuggestions.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions"
```

### 3. Configure `~/.zshrc`

```bash
# Backup, then edit
cp ~/.zshrc ~/.zshrc.bak 2>/dev/null || true
```

Set:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
```

Append personal settings from this directory:

```bash
# Recommended minimal config (see Config & usage below)
cat .zshrc.mini.example >> ~/.zshrc

# Or full (macOS PATH exports + extra aliases: Java/Go/GCP, fzf, Cursor)
# cat .zshrc.example >> ~/.zshrc
```

### 4. Reload & configure prompt

```bash
source ~/.zshrc
p10k configure
```

Use a Nerd Font in your terminal (e.g. JetBrainsMono Nerd Font in Ghostty) so Powerlevel10k icons render correctly.

---

## Verify

```bash
echo $SHELL      # zsh path
zsh --version
grep ZSH_THEME ~/.zshrc
```

---

## Config & usage (`.zshrc.mini.example`)

Minimal personal block: PATH tweaks + aliases. Append after Oh My Zsh loads:

```bash
cat .zshrc.mini.example >> ~/.zshrc
source ~/.zshrc
```

For a fuller macOS-oriented block (Java/Go/GCP, fzf, Cursor, etc.), use `.zshrc.example` instead.

### Exports

| Setting | Effect |
|---------|--------|
| `PATH="/usr/local/sbin:$PATH"` | Prefer `/usr/local/sbin` |
| `# PATH=$PATH:$HOME/bin` | Optional private bin — uncomment to enable |

### Common

| Alias | Usage |
|-------|--------|
| `ll` | Long listing: `ll` |
| `cdp` | `cd` resolving symlinks: `cdp ~/link` |
| `n` | Open Neovim: `n file.py` |

### Python / Jupyter / uv

| Alias | Usage |
|-------|--------|
| `pip` | `pip3` |
| `pye` | Create `./venv`: `pye` |
| `pyse` / `pyde` | Activate / deactivate `./venv` |
| `jupynote` | `jupyter notebook` |
| `uvi` / `uvil` | `uv init` / `uv init --lib` |
| `uve` | `uv venv` → creates `.venv` |
| `uvse` / `uvde` | Activate / deactivate `.venv` |
| `uva` | `uv add <pkg>` |
| `uvr` | `uv run …` |
| `uvrm` | `uv remove <pkg>` |

Typical flow:

```bash
uvi && uve && uvse
uva requests
uvr python main.py
uvde
```

### Claude Code

| Alias | Usage |
|-------|--------|
| `claudex` | Claude with Bash/Write/Edit allowed, skip permissions |
| `claudext` | Same + Telegram channel plugin |

### Kubernetes

| Alias | Usage |
|-------|--------|
| `k` | `kubectl …` |
| `kvc` | List contexts |
| `kvcc` | Current context |
| `kcc` | Switch context: `kcc my-ctx` |

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| `chsh: command not found` | Use full path from `which chsh`, or set default shell in terminal settings |
| Oh My Zsh won't load | `ls -la ~/.zshrc ~/.oh-my-zsh` |
| Theme / icons broken | Install a Nerd Font; re-run `p10k configure` |
| Plugins not active | Confirm `plugins=(...)` includes both custom plugins **before** `source $ZSH/oh-my-zsh.sh` |
| Syntax highlighting last | Keep `zsh-syntax-highlighting` last in the `plugins` list |

---

## Resources

- [Oh My Zsh](https://ohmyz.sh/)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Oh My Zsh plugins](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins)
