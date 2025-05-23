# KaihongGo's Dotfiles

A comprehensive dotfiles configuration managed with [chezmoi](https://www.chezmoi.io/) for a consistent development environment across machines.

## Features

This dotfiles setup includes:

- **Zsh Shell Configuration**: Complete Oh My Zsh setup with useful plugins
- **Enhanced Terminal Experience**: Auto-suggestions, syntax highlighting, and smart completions
- **TLDR Configuration**: Custom theme for better command-line help
- **Automated Installation**: One-command setup with proper permission handling

## Quick Installation

### Prerequisites

Install the required dependencies:

```bash
sudo apt install curl git
```

### One-Command Setup

```bash
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply KaihongGo
```

This command will:
1. Download and install chezmoi
2. Initialize the dotfiles repository
3. Install Zsh and set it as the default shell
4. Install Oh My Zsh with custom configuration
5. Install useful Zsh plugins
6. Apply all configurations

## What Gets Installed

### Zsh Configuration (`.zshrc`)
- **Theme**: robbyrussell (clean and informative)
- **Plugins**:
  - `git`: Git aliases and status information
  - `zsh-autosuggestions`: Fish-like autosuggestions
  - `zsh-syntax-highlighting`: Syntax highlighting for commands
  - `zsh-completions`: Additional completion definitions
- **Settings**: Auto-updates disabled for stability

### TLDR Configuration (`.tldrrc`)
- Custom "ocean" theme with cyan and green color scheme
- Enhanced readability for command examples
- Consistent formatting across all tldr pages

### Installation Scripts
The setup process runs three automated scripts:

1. **`run_once_before_10-install-zsh.sh`**: Installs Zsh and sets it as default shell
2. **`run_once_before_20-install-oh-my-zsh.sh`**: Installs Oh My Zsh framework
3. **`run_once_before_30-install-zsh-plugins.sh`**: Clones useful Zsh plugins

## Features & Benefits

### Enhanced Productivity
- **Smart Autosuggestions**: Get command suggestions based on history
- **Syntax Highlighting**: See command validity before execution
- **Rich Completions**: Enhanced tab completion for commands and arguments
- **Git Integration**: Visual git status and helpful aliases

### Cross-Platform Support
- **Linux**: Full support for Ubuntu, Fedora, and Arch-based distributions
- **macOS**: Automatic Homebrew integration
- **Robust Permissions**: Handles sudo contexts properly

### Maintainable Configuration
- **Version Controlled**: All configurations tracked in Git
- **Modular Setup**: Separate scripts for different components
- **Safe Updates**: Non-destructive updates with chezmoi

## Manual Installation Steps

If you prefer to install components manually:

### 1. Install Zsh
```bash
# Ubuntu/Debian
sudo apt-get update && sudo apt-get install -y zsh

# Fedora
sudo dnf install -y zsh

# Arch Linux
sudo pacman -Sy --noconfirm zsh

# Set as default shell
chsh -s $(which zsh)
```

### 2. Install Oh My Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 3. Install Plugins
```bash
# Create plugins directory
mkdir -p ~/.oh-my-zsh/custom/plugins

# Clone plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-completions ~/.oh-my-zsh/custom/plugins/zsh-completions
```

### 4. Apply Configurations
```bash
# Initialize chezmoi with this repository
chezmoi init KaihongGo

# Apply the dotfiles
chezmoi apply
```

## Updating

To update your dotfiles configuration:

```bash
chezmoi update
```

This will pull the latest changes from the repository and apply them to your system.

## Customization

### Adding New Dotfiles
1. Add files to the chezmoi source directory: `~/.local/share/chezmoi/`
2. Use `chezmoi add <file>` to track new files
3. Commit and push changes to the repository

### Modifying Existing Configuration
1. Edit files directly: `chezmoi edit <file>`
2. Apply changes: `chezmoi apply`
3. Commit changes: `chezmoi cd && git add . && git commit -m "Update configuration"`

## Troubleshooting

### Permission Issues
If you encounter permission errors during installation, the scripts now properly handle sudo contexts. The installation will:
- Detect when running with sudo
- Install components to the correct user's home directory
- Maintain proper file ownership

### Plugin Issues
If plugins don't load properly:
1. Restart your shell: `exec zsh`
2. Check plugin installation: `ls ~/.oh-my-zsh/custom/plugins/`
3. Verify `.zshrc` configuration: `chezmoi diff`

### Zsh Not Default Shell
If zsh isn't set as your default shell:
```bash
chsh -s $(which zsh)
```
Then log out and log back in.

## Contributing

Feel free to fork this repository and customize it for your own needs. If you find improvements or bug fixes, pull requests are welcome!

## License

This dotfiles configuration is available under the MIT License.