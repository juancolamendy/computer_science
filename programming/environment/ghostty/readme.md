# Readme

## Install MacOS
```bash
brew install --cask ghostty
```

## Config
```bash
mkdir -p ~/.config/ghostty
cat > ~/.config/ghostty/config << 'EOF'
font-family = "JetBrainsMono Nerd Font"
font-size = 14
theme = "catppuccin-mocha"
window-padding-x = 8
window-padding-y = 8
background-opacity = 0.95
cursor-style = bar
shell-integration = zsh
confirm-close-surface = false
EOF
```