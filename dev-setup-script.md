#!/usr/bin/env bash
set -e

echo "▶ Starting macOS setup..."

# -------------------------
# Homebrew
# -------------------------
if ! command -v brew >/dev/null 2>&1; then
  echo "▶ Installing Homebrew..."
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

  if [[ -d /opt/homebrew ]]; then
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
  fi
else
  echo "✔ Homebrew already installed"
fi

brew update

# -------------------------
# Oh My Zsh
# -------------------------
if [[ ! -d "$HOME/.oh-my-zsh" ]]; then
  echo "▶ Installing Oh My Zsh..."
  RUNZSH=no KEEP_ZSHRC=yes \
    sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
else
  echo "✔ Oh My Zsh already installed"
fi

# -------------------------
# Helper functions
# -------------------------
install_formula() {
  local pkg="$1"
  if brew list --formula | grep -qx "$pkg"; then
    echo "↻ Reinstalling formula: $pkg"
    brew uninstall "$pkg"
  else
    echo "▶ Installing formula: $pkg"
  fi
  brew install "$pkg"
}

install_cask() {
  local app="$1"
  if brew list --cask | grep -qx "$app"; then
    echo "↻ Reinstalling cask: $app"
    brew uninstall --cask --force "$app"
  else
    echo "▶ Installing cask: $app"
  fi
  brew install --cask "$app"
}

# -------------------------
# CLI tools
# -------------------------
echo "▶ Installing CLI tools..."
install_formula git
install_formula nvm
install_formula yarn
install_formula commitizen
install_formula starship

# -------------------------
# GUI apps + fonts
# -------------------------
echo "▶ Installing GUI apps..."
install_cask firefox
install_cask brave-browser
install_cask calibre
install_cask figma
install_cask imageoptim
install_cask font-hack-nerd-font

# -------------------------
# NVM setup
# -------------------------
echo "▶ Configuring NVM..."
mkdir -p ~/.nvm

if ! grep -q 'NVM_DIR' ~/.zshrc; then
cat <<'EOF' >> ~/.zshrc

# NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$(brew --prefix nvm)/nvm.sh" ] && . "$(brew --prefix nvm)/nvm.sh"
[ -s "$(brew --prefix nvm)/etc/bash_completion.d/nvm" ] && . "$(brew --prefix nvm)/etc/bash_completion.d/nvm"
EOF
fi

# -------------------------
# Starship
# -------------------------
echo "▶ Configuring Starship..."
if ! grep -q 'starship init zsh' ~/.zshrc; then
  echo 'eval "$(starship init zsh)"' >> ~/.zshrc
fi

mkdir -p ~/.config
if [[ ! -f ~/.config/starship.toml ]]; then
cat <<'EOF' > ~/.config/starship.toml
add_newline = false

[character]
success_symbol = "➜"
error_symbol = "✗"
EOF
fi

# -------------------------
# Commitizen (npm side)
# -------------------------
echo "▶ Initializing Commitizen..."
command -v cz >/dev/null 2>&1 || npm install -g commitizen
cz init cz-conventional-changelog --save-dev --save-exact || true

echo "✔ Setup complete. Restart your terminal."
