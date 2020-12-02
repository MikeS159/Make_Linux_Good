# Make_Linux_Great_Again
A bunch of things to change to make (Debian based) Linux work the way I like

Some things are easy to script but others seem to break things, so I keep this file around as a reference and add to it as I go.

## Security

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


## Install useful Stuff

`sudo apt install numlockx -y`

`sudo apt install xrdp`

`sudo apt install screen`

`sudo apt install git`


### Snaps
`sudo snap install --classic code`

`sudo snap install insomnia`

`sudo snap install gitkraken --classic`

`sudo snap install nmap`


### Gnome Stuff
`sudo apt install dconf-editor` For editing org.gnome settings (search "Animation" and disable those settings/reduce time to 0 to make everything smoother")

`/org/gnome/desktop/wm/keybindings/` allows you to change from switching applications to switching windows with alt-tab (disables alt-tab grouping)

`sudo apt install gnome-shell-extension-arc-menu` Smoother than the gnome activities menu and more Windowsy

`sudo apt install gnome-shell-extension-dash-to-panel` Merge task bar and top bar

`sudo apt install gnome-shell-extension-pixelsaver` Merge title bar and menu bar in windows (saves vertical space!)

## File Changes

### Terminal titles

Add this function to .bashrc
You can set terminal titles with 'set-title whatever'

    function set-title() {
      if [[ -z "$ORIG" ]]; then
        ORIG=$PS1
      fi
      TITLE="\[\e]2;$*\a\]"
      PS1=${ORIG}${TITLE}
    }

### xRDP popups

xRDP sessions don't have the same permissions as local sessions, the polkit manager will ask for passwords to create colour profiles and change repositories

In
`/etc/polkit-1/localauthority/50-local.d`

Create a new file called `45-allow-colord.pkla` with the following content

    [Allow Colord all Users]
    Identity=unix-user:*
    Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.free>
    ResultAny=no
    ResultInactive=no
    ResultActive=yes

and another called `46-allow-update-repo.pkla` with


    [Allow Package Management all Users]
    Identity=unix-user:*
    Action=org.freedesktop.packagekit.system-sources-refresh
    ResultAny=yes
    ResultInactive=yes
    ResultActive=yes




