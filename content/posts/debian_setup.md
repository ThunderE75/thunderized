+++
date = '2025-09-30T21:30:11+05:30'
title = 'My Debian Setup'
tags= ['linux', 'guide']
+++

This is how i like to setup a fresh install of Debian (Ubuntu) based distributions.

# List of Tools
- [nala](https://github.com/volitank/nala) - A front-end for apt (package manager)
- [eza](https://github.com/eza-community/eza) - A modern replacement for ls
- [zoxide](https://github.com/ajeetdsouza/zoxide) - A smarter cd written in rust
- [ranger](https://github.com/ranger/ranger) - Console file manager with VI key bindings
- [bat](https://github.com/sharkdp/bat) - A cat replacement with syntax highlighting and Git integration. 
- [neovim](https://github.com/neovim/neovim) -  Vim-fork focused on extensibility and usability  
- [lazygit](https://github.com/jesseduffield/lazygit) - A simple TUI for git  
- [fzf](https://github.com/junegunn/fzf) - A general-purpose command-line fuzzy finder.
- [btop](https://github.com/aristocratos/btop) - Resource monitor that shows usage and stats for processor, memory, disks, network and processes.

# Commands

- Updating the index and upgrading all the packages
- Installs the `nala` front end for apt & update the mirror

```sh
sudo apt update
sudo apt upgrade
sudo apt install nala
sudo nala fetch
```

- Add my `alias.sh` file to `.bashrc`, this adds some Quality of Life Aliases

```sh
cat << 'EOF' > ~/.alias
# ===== QoL Aliases =====
alias cls="clear"
alias vim="nvim"
alias cat="batcat"
alias f="fzf"
alias r="ranger"
alias z="zoxide"
alias refresh="source ~/.bashrc"

# ===== EZA Aliases =====
alias l="eza --icons --sort Name"
alias ls="eza --icons --grid --classify --colour=auto --sort=type --group-directories-first --header --modified --created --binary --group"
alias ll="eza --icons --sort Name --long --header"
alias la="eza --icons --sort Name --long --all --header"
alias lr="eza --icons --sort Name --long --recurse --header"
alias lra="eza --icons --sort Name --long --recurse --all"
alias lt="eza --icons --sort Name --long --tree --header"
alias lta="eza --icons --sort Name --long --tree --all"
EOF

grep -qxF 'source ~/.alias' ~/.bashrc || echo 'source ~/.alias' >> ~/.bashrc
source ~/.bashrc
```

# Future Scope
- After a while, i usually switch to zsh as my shell but i have not made my guide for it
- I use OhMyBash/OhMyZsh to customize my prompt
- For ubuntu, i remove snap support & use [Flatpak](https://flatpak.org/setup/Ubuntu)