# Readme

## Install MacOS
```bash
brew install neovim
```

## # Using APT / Ubuntu
```bash
sudo apt update
sudo apt install neovim
```

## Using dnf Alma Linux / RHEL / CentOS
```bash
# Using DNF
sudo dnf install neovim
```

## Test
```bash
nvim --version
```

## Config dir
```bash
mkdir -p ~/.config/nvim
```

## Plugin Manager
```bash
mkdir -p ~/.config/nvim/lua/plugins
```

## Place the files
```bash
nvim ~/.config/nvim/init.lua
nvim ~/.config/nvim/lua/plugins/init.lua
```

---

## Usage / Key bindings

Leader is `,` (`mapleader` / `maplocalleader`).

### Core

| Binding | Action |
|---------|--------|
| `jk` / `kj` | Escape (insert mode) |
| `Ctrl-s` | Save |
| `Ctrl-Q` | Save and quit |
| `Ctrl-h/j/k/l` | Navigate windows |
| `Ctrl-Shift-h/j/k/l` | Resize windows |
| `H` / `L` | Previous / next tab |
| `,d` `,D` `,c` `,C` `,x` `,X` | Blackhole delete/change (normal + visual) |
| `F5` | Buffer list → pick buffer |
| `Ctrl-n` | Open terminal split (zsh, height 10) |
| `Esc` | Exit terminal mode |

### Tools

| Binding | Action |
|---------|--------|
| `Ctrl-e` | Toggle Neo-tree |
| `Ctrl-p` | Telescope find files |
| `,fg` | Telescope live grep |
| `,fb` | Telescope buffers |
| `,fo` | Telescope oldfiles |

### LSP (buffer-local, when attached)

| Binding | Action |
|---------|--------|
| `gd` | Go to definition |
| `gy` | Go to type definition |
| `gi` | Go to implementation |
| `gr` | References |
| `K` | Hover docs |
| `,rn` | Rename symbol |
| `,ac` | Code action |
| `,f` | Format |
| `[g` / `]g` | Prev / next diagnostic |
| `Space-a` | Telescope diagnostics |
| `Space-o` | Document symbols |
| `Space-s` | Workspace symbols |
