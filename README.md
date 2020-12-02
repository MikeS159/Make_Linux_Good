# Make_Linux_Great_Again
A bunch of things to change to make (Debian based) Linux work the way I like

Some things are easy to script but others seem to break things, so I keep this file around as a reference and add to it as I go.

## General Utilities

Changing keyboard layout to UK QWERTY

`sudo setxkbmap gb`

Add this line to the end of /etc/sudoers (replace "$USER" with "your_user_name")

"$USER" ALL=(ALL) NOPASSWD:ALL`


Get everything up to date and make sure security fixes get done automatically

`sudo apt update`

`sudo apt upgrade`

`sudo apt install unattended-upgrades`

`sudo dpkg-reconfigure --priority=low unattended-upgrades`


Uncomment the updates line in below if you want updates to be automatic too

`sudo nano /etc/apt/apt.conf.d/50unattended-upgrades`


Make a strong key for SSHing

`ssh-keygen -t ed25519`


Install useful Stuff

`sudo apt install numlockx -y`
`sudo apt install xrdp`
`sudo apt install screen`
`sudo apt install git`

`sudo snap install --classic code`
`sudo snap install insomnia`
`sudo snap install gitkraken --classic`
`sudo snap install nmap`

`sudo apt install dconf-editor`
`sudo apt install gnome-shell-extension-arc-menu`
`sudo apt install gnome-shell-extension-dash-to-panel`
`sudo apt install gnome-shell-extension-pixelsaver`


Add this function to .bashrc
You can set terminal titles with 'set-title whatever'

```function set-title() {
  if [[ -z "$ORIG" ]]; then
    ORIG=$PS1
  fi
  TITLE="\[\e]2;$*\a\]"
  PS1=${ORIG}${TITLE}
}```


Add these lines to .inputrc to allow keyboard shortcut for moving a word at a time

`"\e[1;5C": forward-word   # ctrl + right`

`"\e[1;5D": backward-word  # ctrl + left`

Change a keyboard shortcut so Alt+Tab cycles through all windows, not groups

`Open Settings > Devices > Keyboard > Navigation > Switch Windows > Alt+Tab > Done!`


## Useful Apps

A section to contain all the useful shell extensions and core apps that Make Linux Great Again

* [Dash To Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/) - An icon task-bar which gives more customisation and allows ungrouping like in Windows OS. Gnome shell extension.



