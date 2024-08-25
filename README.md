# Gabe's dotfiles

This repo contains the dotfiles for my laptop, a set of similar dotfiles with some slight modifications for desktops can be found [here](https://github.com/sykesgabri/dotfiles).

I use these dotfiles on EndeavourOS, but they will probably work fine on other distros.

## Requirements, dependencies, and the programs these dots contain configs for.

- Git
- Stow
- i3 Window Manager
- zsh (Execute `chsh -s /bin/zsh` then log out and back in to make zsh your default shell)
- zsh-syntax-highlighting
- Starship
- Alacritty
- fastfetch
- arandr
- polybar
- Noto Fonts CJK
- Nitrogen (You will have to manually use this to choose your wallpaper after installation, my wallpapers aren't included in the dotfiles as they are modified personal photos)
- lxsession
- lxappearance (Use this to set the theme to Catppuccin Mocha Sapphire, the theme is included in these dotfiles)
- Picom
- rofi
- i3lock
- playerctl
- flameshot

Here's one massive fucking pacman command to install everything on the above list (Arch based distros only):
```
sudo pacman -S --needed git stow i3-wm zsh zsh-syntax-highlighting starship alacritty fastfetch arandr polybar noto-fonts-cjk nitrogen lxsession lxappearance picom rofi i3lock playerctl flameshot
```

## Requirements you can't get through pacman.

- [Hack Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/Hack.zip) (Extract in `/usr/share/fonts`)
- [polybar-spotify](https://github.com/PrayagS/polybar-spotify) <details><summary>Click here for notes.</summary><br>A Polybar module that provides Spotify status and controls, my Polybar config expects it to be in ~/github/, if you clone this repo somewhere else, you'll have to change the path in .config/polybar/config.ini. If you use a player other than Spotify, you can change where it pulls its status from in get_spotify_status.sh, my own one is set to "chromium" for Tidal-HiFi.</details>
- [zscroll](https://github.com/noctuid/zscroll) (Install `zscroll-git` from the AUR. If your distro didn't come with an AUR helper, go through the steps to set up [yay](https://github.com/Jguer/yay))
- [Catppuccin cursors](https://github.com/catppuccin/cursors) (Follow the instructions in the readme and use lxappearance to set them)
- [Catppuccin Papirus folders](https://github.com/catppuccin/papirus-folders) (Follow the instructions in the readme and use lxappearance to set them)
- [Any other Catppuccin themes](https://catppuccin.com/ports) (Find and install the ones you need for the programs you use so that all their appearances match, the variant you want is Mocha Sapphire)

## Installation

1. Clone this repo into your home directory, and cd into it:
```
cd ~
git clone https://github.com/sykesgabri/laptop-dotfiles
cd dotfiles
```
2. Use Stow to create symlinks from the repo to your home directory:
```
stow .
```

If you get a `Stowing . would cause conflicts` warning, it is because your home directory already has a file in the same name and location as the one stow is trying to create a symlink for. Read whatever paths Stow is saying causes conflicts, and delete those files in your home directory, then try the Stow command again.

## If you are not me, read this:

Some parts of these dotfiles will be very specific to my setup, which is probably not the exact same as yours. Assuming you are not me, here's a list of some configs you may want to change:

- The .sh files in .screenlayout/ correspond to my monitor setup. I strongly recommend deleting them and using arandr to create a .sh file for your monitor setup. Ensure that whatever you name it is reflected in the exec command at the bottom of .config/i3/config so that it is automatically executed when you log in.

- You may wish to remove various exec commands from the i3 config. The top one prevents the screen from going to sleep. The rest correspond to various programs, some of which you may not use. Just don't delete the ones for lxsession, picom, the .screenlayout/ script, polybar, and nitrogen.

## Note on why Catppuccin GTK theme is included in my dots:

The Catppuccin GTK theme is currently an [archived repo](https://github.com/catppuccin/gtk), and not included in https://catppuccin.com/ports as of writing this. Their reasons for this are detailed in said archived repo. In the releases, the most recent ones do not contain the GTK-2.0 directory needed to have the theme work with lxappearance in i3. The release I'm using is v0.7.5, the last (as far as I've checked) to have the files necessary for my setup. I could just link to that specific release, but given the circumstances it's easier to just include the whole theme in my dots.

This repo was created following this tutorial: https://www.youtube.com/watch?v=y6XCebnB9gs
