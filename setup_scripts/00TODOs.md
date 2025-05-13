# DOTFILES TO CONSIDER
- [-] https://github.com/Nisfeight8/Nisfere
- [-] https://github.com/end-4/dots-hyprland
- [-] https://end-4.github.io/dots-hyprland-wiki/en/general/showcase/
- [-] https://github.com/linkfrg/dotfiles/
- [-] https://github.com/rubiin/HyDePanel
- [-] https://github.com/rubiin/dotfiles
- [-] https://github.com/Axenide/Ax-Shell
- [-] https://github.com/xeji01/hyprstellar.git

# NEOVIM CONFIGURATION
- [ ] Use lunarvim and astronvim 
- [ ] Build a neovim config from scratch
- [ ] Add yazi.nvim to neovim  configuration
- [ ] Add tree-sitter-hyprlang for neovim
- [ ] Add indentation support to markdown headings
- [ ] Add iron.nvim to astronvim config

# CRON JOBS/SYSTEMD TIMERS
- [ ] add a cron job to automatically push to gitlab and/or github every 15 minutes
- [ ] add cron joba for updating the system once a week

# EMACS/DOOM EMACS
- [ ] Use crafted-emacs and use deepseek to create emacs config files
- [ ] Decide whether to use personal config instead of doom emacs
- [x] Install hyprlang-ts-mode for emacs
- [ ] Add color support to doom emacs
- [ ] add scripts directory to path
- [ ] add lisp code to path for use in configuration
- [ ] highlight matching parenthesis and use rainbow brackets
- [ ] integrate better defaults from emacs-config.org into fresh-emacs.org
- [ ] line numbering support inside org-src-code blocks
- [ ] borrow line numbers setting and minibuffer escape from emacs-config.org
- [ ] borrow zooming config from emacs-config.org
- [ ] org-capture binary from the doom emacs project
- [ ] setup a doom doctor-like setup and binary from the doom emacs project
- [ ] jupyter and latex integration inside org-babel
- [ ] after finishing emacs-config.org add features from from doom emacs init.el into the deepseek command


# Crafted Emacs
- [x] crafted-ide-config
- [x] crafted-ide-packages
- [x] crafted-evil-config
- [x] crafted-evil-packages
- [x] crafted-completion-config
- [x] crafted-completion-packages
- [x] crafted-lisp-config
- [x] crafted-lisp-packages
- [x] crafted-org-config
- [x] crafted-org-packages
- [x] crafted-speedbar-config
- [ ] crafted-ui-config
- [ ] crafted-ui-packages
- [ ] crafted-workspaces-config
- [ ] crafted-workspaces-packages
- [ ] crafted-writing-config
- [ ] crafted-writing-packages


# Integrate the following comments into doom emacs
1. ___Write an org-mode configuration for doom emacs using the built-in org-mode in emacs with org-mode optimizations and the following features and integrations___:
    - org file directory is in $home/org along with all other org-mode related files; 
    - extensive org headlines configuration with variable font size with each level of header, fonts using jetbrainsmono nerd font bold fonts for all headlines; 
    - prettify source code blocks with ligatures and icons; 
    - all org files start in the overview mode; 
    - comprehesive org-agenda setup including integrations with org-super-agenda;
    - comprehensive org-modern configuration with optimizations and integrations throughout the whole configuration and also include integrations with org-super-agenda, org-fragtog, org-download, org headlines and have custom org stars; use org-modern-table instead of a custom configuration;
    - org-fancy-priorities configuration with integration into org-modern
    - comprehensive org-todo configuration with ligatures and unicode integrated into org todo keywords
    - make sure org-ellipses integrates well with org-modern stars
    - have support for pretty tables in org files
    - seamless integrations writing in bold, italic and underline texts
    - comprehensive setup for writing latex in org-mode files and integrating the setup into a reference management system that includes support for multiple .bib files. Also integrate the latex setup with zotero to review the attached sources in .bib files. Use tectonic from https://github.com/tectonic-typesetting/tectonic for latex setupUse tectonic from https://github.com/tectonic-typesetting/tectonic for latex setup 
    - have doom tokyo-night theme integration throughtout the configuration
    - org-roam v2 configuration with the following features and integrations: features that are inspired by The Brain in https://thebrain.com/; keybindings that follow doom-emacs-like bindings; quality-of-life features and improvements; advance visualizations; obsidian-like features; don't follow obsidian keybindings;; denote related files are inside the org directory; additional quality-of-life features and improvements
    - comprehensive org-noter configuration that integrates well with org-roam v2
    - do not include any redundant configuration options already present in doom emacs
  ___Then integrate all the parts of the configuration to provide a seamless experience to write scientific documents in org mode.___



[!Note] Add org-mode after seeing crafted-emacs config, write part about org configuration with org-appear, org-modern, denote, org-fragtog
Write a state-of-the-art emacs 30 configuration in org-mode that will be tangled to init.el with the following features, properties and integrations:
  - divide the whole org file into sensible titles and respectives emacs-lisp org source code blocks with integration between the source code blocks for their respective configurations
  - optimize emacs startup time and optimize the whole configuration where possible. all packages must be lazy loaded like neovim wherever possible.
  - use emacs built-in package manager both emacs repos and pulling from git repos; do not use straight package manager or any other package manager for emacs
  - aggressive emacs optimizations to the configuration wherever possible
  - comprehensive doom tokyo-night theme integration throughout the configuration and wherever possible
  - setup automatic package update
  - comprehensive keybindings configuration with doom emacs-like and spacemacs-like bindings and vim bindings integration using the general emacs package. Vim keybindings must not clash with the doom emacs-like or spacemacs-like keybindings
  - minimal ui along with zen mode integration 
  - relace yes/no prompts for y/n
  - disable automatically starting the splash screen, startup message, scratch message on startup
  - comprehensive eglot configuration including eglot ensure for all the major programming mode
  and using eglot-booster from https://github.com/jdtsmith/eglot-booster to optimize eglot
  - comprehensive treesitter support with treesitter integration for any part of the emacs 30 config that needs it. treesitter is built into emacs 30. Don't pull from package manager sources or git sources.
  - comprehensive editorconfig configuration to have cross-editor/ide like features
  - comprehensive ibuffer configuration following keybindings from doom emacs project and integrating the ibuffer-project emacs package 
  - color and emojis support for emacs 30 as well as rainbow-mode integration
  - comprehensive evil configuration including setups for the emacs package: emacs-collection, evil-nerd-commenter and evil-goggles
  - comprehensive completion system using extensive configurations for cape, consult, corfu, corfu-terminal, embark embark-consult, marginalia, orderless, and vertico. Have nerd-icons and catppuccin mocha theme integration wherever possible
  - comprehensive lisp configuration for lisp modes including emacs-lisp, sly, clojure and guile. All lisp modes must have aggressive indent integration. The following emacs packages will be setup: package-lint, package-lint-flymake, sly, sly-asdf, sly-quicklisp, sly-repl-ansi-color, cider, clj-refactor, clojure-mode, flycheck-clojure, geiser, geiser-guile and geiser-racket.
  - comprehensive speedbar configuration. speedbar is built into emacs 30. Don't pull from package manager sources or git sources.
  - keep folders clean by no littering emacs package and disable nativecomp warnings 
  - set default fonts as JetBrainsMono Nerd Font and Ubuntu Nerd Font for variable pitch fonts
  - comprehensive and state-of-the-art dired configuration with the following features and integrations: ranger integration; keybindings must follow the keybindings from the doom emacs project; file preview for various types of files; files and folders must only show the icon and title of the respective file and/or folder in that particular order; nerd icons integration; catppuccin mocha theme integration; hidden files must be shown with distinction from regular files; folders must be shown first then files are shown; respective files and/or folders for hidden files must be shown first before their regular counterpars
  - use doom emacs way of opening configuration directory and its files
  - comprehensive setup for looking up documentation for all common programming languages
  - all-the-icons and nerd-icons integration throughout the configuration where needed. Don't use both. Mainly have nerd icons integration for the whole configuration and all the icons where nerd icons use is not available
  - extensive dabbrev integration throughout the configuration
  - add the ability to drag stuff (words, region, lines) around in Emacs using drag-stuff emacs package
  - add the ability to format the a file on save using format-all package for the available file types 
  - setup comprehensive flycheck configuration using the flycheck package
  - setup comprehensive magit configuration that includes git-timemachine package
  - extensive helpful configuration for the package helpful from https://github.com/Wilfred/helpful instead of the built-in emacs 30 one
  - extensive indent guides highlighting setup using highlight-indent-guides package
  - comprehensive ligature configuration using the ligature emacs package
  - comprehensive emacs modeline configuration using doom-modeline package and following doom emacs project theming and features
  - comprehensive treemacs configuration following keybindings from doom emacs project, integration with catppuccin mocha and nerd icons theming
  - support for editing nix files in emacs
  - comprehensive prescient configuration with integration for the whole emacs configuration, including the completion setup in this emacs 30 configuration
  - comprehensive prettiy-symbols configuration with integration for all programming modes
  - support for re-opening all open buffers and files if emacs crashes for any reason
  - add quality of life features for delimites including highlighting for matching parenthesis and extensive rainbow-delimiters integration
  - comprehensive liguratures configuration
  - comprehensive centaur-tabs configuration including features and keybindings from the doom emacs project
  - comprehensive vterm configuration with optimizations and vterm toggle integration. Disable the use of eshell in emacs
  - comprehensive which-key configuration with which-key being at the bottom and having idle delay of 0.1 and using  → as the separator
  - comprehensive snippets configuration using yasnippet and the snippets are integrated throughout the whole configuration
  - comprehensive dashboard configuration using the emacs-dashboard packages with quality of life improvements emacs and following the theming and features from the doom emacs dashboard
  - comprehensive and state-of-the-art configuration for org-mode using the built-in org-mode in emacs with org-mode optimizations and the following features and integrations: do not pull org package from any emacs sources, instead use the built-in org-mode that comes with emacs 30; quality of features and improvements; do not setup org-roam(v1,2), org-noter or org-brain throughout the emacs 30 configuration; org file directory is in $HOME/org along with all other org-mode related files; extensive org headlines configuration with variable font size with each level of header, catppuccin mocha theme integrations, fonts using JetBrainsMono Nerd Font bold fonts for all headlines; prettify source code blocks with ligatures and icons; all org files start in the overview mode; comprehensive org babel configuration with support for python, shell, emacs-lisp and conf-unix; comprehensive org structure templates configuration with support for python, shell, emacs-lisp and conf-unix; comprehesive org-agenda setup including integrations with org-super-agenda; comprehensive org-todo configuration following exactly from the doom emacs project including the default keybindings, and default keywords, and integrates with org-super-agenda and org-modern; comprehensive org-fragtog and org-download integration; pomodoro integration for tasks; doom emacs-like capture templates; comprehensive org-modern configuration with optimizations and integrations throughout the whole configuration and also include integrations with org-super-agenda, org-fragtog, org-download, org headlines and have custom org stars; org-fancy-priorities configuration with integration into org-modern; setup a binary or python script for org-capture similar to the doom emacs project; seamless integrations writing in bold, italic and underline texts, as well as url and highlighted texts in org mode
  - extensive hl-todo configuration that integration with org-modern and keybindings follows spacemacs like format
  - autopair setup for types of brackets except for the delimiter "<" inside a org file
  - comprehensive and state-of-the-art denote configuration with the following features and integrations: mimics org-roam version 2 and includes many of its features; integrations throughout the whole configuration; features that are inspired by The Brain in https://thebrain.com/; keybindings that follow doom-emacs-like bindings; quality-of-life features and improvements; naming schemes follow org-roam version 2 format; advance visualizations; obsidian-like features; don't follow obsidian keybindings; denote extensions and denote menu integrations; org-noter like features; denote related files are inside the org directory; additional quality-of-life features and improvements
  - setup a binary or python script for having features like doom doctor and doom sync from the doom emacs project for the emacs 30 configuration
  - comprehensive and state-of-the-art python programming configuration that includes eglot integration, treesitters, formatters, linters, and dap and integrates all these features into org-mode so that python programming in an org file has support for eglot, treesitters, formatters, linters, dap and all other features inside org source code blocks so that python programming in org-mode is seamless. The configuration must include comprehensive support for programming in jupyter using the emacs-jupyter package inside org mode. Org's structure templates for python must include the shebang argument '#!/usr/bin/env python'
  - comprehesive projectile configuration with support for various programming languages and integrates into ibuffer if possible

Then take inspiration from the doom emacs project for any missing features that may quality of life improvements


# UPDATES SCRIPT
- [ ] Add to systemd timer service or cron job
- [ ] Add go packages, both release and source
- [ ] Add source packages
- [ ] Hyprland plugins
- [ ] texlive packages
- [ ] flatpak apps

# HYPRLAND DE
- [-] Use nisefere as base https://github.com/Nisfeight8/Nisfere and add weather widget from https://github.com/rubiin/HyDePanel
- [ ] Install Ianny as an ebuild using uwsm ebuild
- [x] Install and configure anyrun from my NixOS setup
- [ ] Ask chatgpt to create a lo of modules. First ask to create macOS-like using  waybar that autohides and only comes on mouse hover
- [x] Get Inspiractions from awesome-rices github-repo and whatsappm list repos
- [ ] Use linkfrg dotfiles animations
- [ ] Consider specific parts from configs jakoolit and end-d4]
- [ ] Make browser pop-ups floating by identifying their class using `hyprctl clients | grep -i class`
- [ ] When setting up waybar, consider adding grouped-items following https://itsfoss.com/waybar-grouped-items/
- [ ] Install hyprls using go ebuild
- [ ] Autostart apps and services using systemd user services
- [ ] Use the following plugins:
    - [ ] hyprland-expo
    - [ ] hycov with hyprland-expo to see all open windows
    - [ ] hy3
    - [ ] hycov
    - [ ] hyprscroller
    - [ ] hyprslidr
    - [ ] hyprnome
    - [-] Consider if hyprspace conflicts with hypcov and expo
    - [-] Find out hyprland-easymotion does
    - [ ] Test hyprchroma to test transparency
- x Consider Ashell for bar
- [x] Consider nwg-shell for bar too.
- [ ] Consider very strongly if Walker Application Launcher
- [x] Install Hyprlux

- [-] See what hyprkool does since it is inspired by Kde-Plasma-activities

# GLOBAL CONFIGS
- [NISFERE Main] https://github.com/Nisfeight8/Nisfere 
  - [x] bpytop
  - [ ] fabric
  - [ ] fastfetch
  - [ ] hyprland
  - [ ] nisfere-gtk-theme [!NOTE] : See if catppuccin is available
  - [ ] scripts
  - [ ] zsh

- [HOME-NIX] https://gitlab.com/aahsnr/home-nix.git
  - [x] anyrun
  - [x] hyprlock
  - [x] hypridle
  - [ ] pyprland
  - [ ] scripts

- [DOTFILES] https://gitlab.com/aahsnr/dotfiles.git -b zephyrus
  - [ ] atuin
  - [ ] bat
  - [ ] btop
  - [ ] capsule
  - [-] for cliphist test if the /etc/portage part works or not; also setup a systemd timer for the command in cliphist.md
  - [ ] cliphist
  - [ ] cliphist-rofi
  - [ ] eza
  - [ ] fzf
  - [ ] hyprlock
  - [ ] hypridle
  - [ ] hyprland
  - [ ] hyprlux
  - [ ] imv
  - [ ] kitty
  - [ ] lazygit
  - [ ] man pages
  - [ ] nwg-drawer
  - [ ] nwg-menu
  - [ ] ripgrep
  - [ ] scripts
  - [ ] thefuck
  - [ ] sddm  
  - [-] for starship, test if cd into .dots directory takes time or certain commands take time or not
  - [ ] starship
  - [ ] tealdeer
  - [ ] yazi
  - [ ] zathura
  - [ ] zoxide
  - [ ] zsh

# DEEPSEEK MD
[!Note]: For all the deepseek created configs, systemd units and scripts, make sure all of them are working
  - [x] atuin
  - [x] bat
  - [ ] capsule
  - [x] kitty
  - [x] lazygit
  - [x] nwg-drawer
  - [x] nwg-menu
  - [x] sddm
  - [x] zsh
  - [x] borg-backup script
  - [x] eza
  - [x] fzf
  - [x] cliphist
  - [x] imv
  - [x] [[Home Configuration]] write an advanced and optimized configuration for ___zathura___ with catppuccin mocha theme integration, hyprland integration, vim keybindings integration and quality of life improvements for use in gentoo linux
  - [x] [[Home Configuration]] write an advanced and optimized configuration for ___thefuck___ with catppuccin mocha theme integration, zsh integration and quality of life improvements for use in gentoo linux
  - [x] tealdeer
  - [x] [[Home Configuration]] write an advanced and optimized configuration for ___ripgrep___ with catppuccin mocha theme integration, zsh integration and quality of life improvements for use in gentoo linux
  - [x] [[System Configuration]] write an advanced and optimized configuration for handling ___man pages___ in gentoo linux with quality of life improvements, zsh integration and catppuccin mocha theme integration
  - [x] write a secure systemd user configuration for running the following command weekly: ___cliphist optimize --compact___   
  - [x] [[Home Configuration]] write an advanced and optimizemized configuration for ___atuin___ in gentoo linux that has vim keybindings and zsh integration
  - [ ] [[Scripts]] write an advance, secure and optimized script in python that extract files in any format for gentoo linux and all linux distributions in general, has user-friendly features, zip bomb detection, parallel extraction using multiple CPU cores, color-coded output and custom extraction directory
  - [ ] [[Enterprise-Grade System Configuration]] Write an enterprise grade and security hardened ___auditd profile___ with apparmor, systemd and cron integration 
  - [x] [[Home Configuration]] write an advance, optimized and modular rofi configuration to use ___cliphist (text and images) as gui___, has catppuccin mocha theme, papirus icon and fzf integration
  - [x] write an advanced and optimized configuration for ___starship prompt___ with catppuccin mocha theme integration, zsh integration, support for broad range of languages, and git optimization for gentoo linux
  - [x] write an advance, optimzed and clean configuration for ___btop___ with catppuccin mocha theme, vim keybingings and quality of life improvements for use in gentoo linux 
  - [x] write an advanced and optimized configuration for ___zoxide___ with catppuccin mocha theme integration, zsh integration, git optimization and quality of life improvements for use in gentoo linux
  - [x] write an advance, optimized and beatiful configuration for ___yazi___ with catppuccin mocha theme, using nerd fons, vim keybindings, useful plugins integration and quality of life improvements for use in gentoo linux
  - [ ] write an advanced and optimized czkawka clone using python and gtk4 as gui
  - [ ] [[Important System Utilities]] write a suit of advance, optimized, and useful python programs for ___daily-driving and maintaining gentoo linux and non-gentoo related linux tasks___ with the following features and integrations: security hardened, systemd integration, email notifications for critical issues, database integration for tracking changes, gui using gtk4, wayland integration, detailed hardware monitoring, quality of life improvements, integration with Gentoo's own tools and other linux-related tools. Then add glade ui files for all the programs to have complex layouts Then write gentoo ebuild files to install the generated programs in gentoo.
  - [x] [[Important System Utilities]] ___write useful python scripts for use in linux___
  - [ ] [[Desktop Shell]] ___Use the awesome window manager configuration in  and replicate all the desktop widgets and elements using EWW, and hyprland animations and blur to all eww widgets, and have the following properties and modifications: modular, eww configurations, hyprland blur and animations added to eww, animation aware dock, volume control osd using pipewire, gentoo-specific integrations, catppuccin mocha theme and papirus icon theme integrations, animated and dynamic workspace indicator in panel, main panel at the bottom , Do Not Disturb support, JetBrainsMono Nerd Font for fonts, notification center using mako, kitty for the default terminal, zen-browser for default browser, without a lockscreen, all configurations being advance and optimized, and additional desktop elements to improve quality of life and desktop experience___
  - [ ] [[Important System Utilities]] write an advance, modular, and optimized ___duplicate file finder___ program using python and gtk4 for gui without libadwaita support and the following features: multiple scan modes, image similarity detection, advanced filtering options, saving/loading scan results, ML-based similarity detection using pytorch for various file types, sophisticated file management options, mass delete/move operations for duplicates, similarity detection for documents, videos,etc., and fzf integration. Use numba wherever possible to optimize the python code. Then add glade ui file for complex layouts, and ensure the program has wayland support. Then write a gentoo ebuild file for installing in gentoo.


- write an advanced and optimized eww configuration that creates a desktop shell with the following properties: macOS-like desktop elements, catppuccin mocha theme integration, hyprland integration with animations and blur effects and quality of life improvements for use in gentoo
- Expand the above EWW macOS-like Desktop Shell Configuration by adding more desktop elements to improve quality of life and add hyrpland blur and animations integrations to eww
- For the above EWW macOS-like Desktop Shell Configuration, setup an advanced notification center and advanced volume control osd using pipewire
- For the notication center use mako instead of dunst for the above configurations
- Modularize the above configurations [TODO]

# SYSTEMD USER UNITS
- [x] cliphist
- [x] cliphist-images
- [ ] hyrpm reload -n
- [x] pyprland
- [x] hyprtheme
- [x] hyprpaper
- [x] xdg-desktop-portal-hyprland
- [x] ianny
- [ ] fabric
- [x] pypr
- [x] hyprtheme
- [x] hypridle


# DOTFILES 

[[IMPORTANT]] ___Recreate all config files inside an org file that tangles files to appropriate location. Only this org file is required.___

ln -sv $HOME/.dots/gentoo_setup $HOME/
ln -sv $HOME/.dots/org $HOME/
ln -sv $HOME/.dots/.config/bat $HOME/.config/
ln -sv $HOME/.dots/.config/btop $HOME/.config/
ln -sv $HOME/.dots/.config/capsule $HOME/.config/
ln -sv $HOME/.dots/.config/hypr $HOME/.config/
ln -sv $HOME/.dots/.config/Thunar $HOME/.config/
ln -sv $HOME/.dots/.config/gtk-3.0 $HOME/.config/
ln -sv $HOME/.dots/.config/gtk-4.0 $HOME/.config/
ln -sv $HOME/.dots/.config/Kvantum $HOME/.config/
ln -sv $HOME/.dots/.config/lazygit $HOME/.config/
ln -sv $HOME/.dots/.themes $HOME/
ln -sv $HOME/.dots/.config/nvim $HOME/.config/
ln -sv $HOME/.dots/.config/qalculate $HOME/.config/
ln -sv $HOME/.dots/.config/qt5ct $HOME/.config/
ln -sv $HOME/.dots/.config/qt6ct $HOME/.config/
ln -sv $HOME/.dots/.config/yazi $HOME/.config/
ln -sv $HOME/.dots/.config/wallpapers $HOME/.config/
ln -sv $HOME/.dots/.config/zathura $HOME/.config/
ln -sv $HOME/.dots/.gtkrc-2.0 $HOME/

# GENERAL
- [ ] Need to port over firefox config 
- [x] Configure anyrun like home-nix
- [ ] Update zsh config and borrow certain elements from Nisfere
- [ ] Setup yazi and its plugins and optimize it
- [ ] Setup docker and podman in gentoo 
- [x] Learn how to setup borg for automatic documents backup
- [ ] Setup ccache in gentoo
- [x] Install python-fabric via python ebuilds
- [ ] Write ebuilds for go packages following nwg-drawer ebuild as an examples
- [-] Follow this guide https://wiki.gentoo.org/wiki/Zswap to setup zswap in gentoo
- [ ] Setup nvhpc later on worksation
- [x] Setup gnome-software or discover to install flatpak and snap packages
- [ ] Setup apparmor in gentoo
- [ ] Install firewalld after finishing full system install
- [ ] Use kitty terminal for everything
- [ ] Use tgpt to setup gpt, deepseek,etc
- [ ] Install apparmor profiles from https://github.com/roddhjav/apparmor.d inside sec-policy/apparmor-profiles
- [ ] Setup Arpwatch later down the line
- [ ] Consider SecurityOnion for deploying in my house and look at youtube videos
- [ ] Set up default applications using https://wiki.gentoo.org/wiki/Default_applications
- [ ] Add these asus modules to dracut: hid_asus asus_wmi asus_nb_wmi
- [X] Setup graphite flags in package.env like clang https://wiki.gentoo.org/wiki/Clang
- [x] Add current neovim config to dotfiles
- [ ] Add kernel integrity subsystem support using https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/managing_monitoring_and_updating_the_kernel/enhancing-security-with-the-kernel-integrity-subsystem_managing-monitoring-and-updating-the-kernel#enhancing-security-with-the-kernel-integrity-subsystem_managing-monitoring-and-updating-the-kernel
- [x] install yarn and npm
- [ ] add fuji fox to firefox
- [ ] Consider https://github.com/xeji01/hyprstellar.git for some of its elements
- [ ] Find out which repos need to be followed to update versioned ebuild packages
- [ ] Find out which repos need to be followed for to update packages built from source
- [ ] Fix yank and paste in neovim
- [ ] Install tmux and look at vim-syntax scripts
- [ ] Find out which git repos you need to follow
- [ ] Switch to vivaldi browser
- [ ] Replace straight with emacs built-in package manager
- [ ] :pin org in (use-package org)
- [ ] Install yazi plugins
- [ ] Setup cliphist rofi
- [ ] Use modprobed-db to use localmodconfig
- [ ] Need to setup winapps using https://github.com/winapps-org/winapps for certain windows applications
- [ ] Remove tree-sitter packages 
       dev-libs/tree-sitter-markdown dev-libs/tree-sitter-vimdoc dev-libs/tree-sitter-lua dev-libs/tree-sitter-vim dev-libs/tree-sitter-query dev-libs/tree-sitter-c dev-libs/tree-sitter-bash dev-libs/tree-sitter-html
- [X] Apply polly optimizations to clang/llvm and its packages
- [ ] Setup zram using zram-init after booting into gentoo


# `EBUILDS`
[!NOTE] : EGIT_REPO_URI="https://github.com/hyprwm/${PN^}.git"
- [ ] gui-apps/alacritty-graphics [versioned]
- [ ] app-misc/czkawka [versioned] using pycargoebuild and https://devmanual.gentoo.org/eclass-reference/rust.eclass/index.html
- [x] sys-apps/apparmor [versioned]
- [x] sys-apps/apparmor-utils [versioned]
- [x] sys-libs/libapparmor [versioned]
- [x] sec-policy/apparmor-profiles [versioned]
- [x] gui-wm/hyprland [9999]
- [ ] gui-libs/hyprland-qtutils 
- [x]	dev-libs/hyprgraphics [9999]
- [x]	dev-libs/hyprlang [9999]
- [x]	gui-libs/aquamarine [9999]
- [x]	gui-libs/hyprcursor [9999]
- [x]	gui-libs/hyprutils [9999]
- [x]	dev-libs/hyprland-protocols [9999]
- [x] dev-util/hyprwayland-scanner [9999]
- [x]	gui-libs/xdg-desktop-portal-hyprland [9999]
- [x]	gui-apps/hypridle [9999]
- [x]	gui-apps/hyprlock [9999]
- [x]	gui-apps/hyprpaper [9999]
- [x]	gui-apps/hyprpicker [9999]
- [x]	gui-wm/hyprland-contrib [9999]
- [x]	gui-apps/hyprsunset [9999]
- [x]	gui-apps/uwsm [9999]
- [x] dev-util/dart-sass [9999]
- [ ] pyprland [9999] using https://devmanual.gentoo.org/eclass-reference/python-r1.eclass/index.html 
- [X] sys-kernel/cachyos-settings
- [x] sys-process/cachyos-ksm-settings
- [ ] app-admin/ananicy-cpp
- [ ] app-admin/ananicy-rules-cachyos
- [ ] sec-policy/apparmor-profiles-roddhjay https://github.com/roddhjav/apparmor.d [9999]
- [x] gui-apps/anyrun using git commit
- [ ] ianny
- [ ] czkawka  
- [ ] fabric-cli



