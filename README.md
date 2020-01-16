# Make_Linux_Good
A bunch of things to change to make (Debian based) Linux work the way I like

Some things are easy to script but others seem to break things, so I keep this file around as a refrence and add to it as I go



Changing keyboard layout to UK QWERTY
`sudo setxkbmap gb`

Add this line to the end of /etc/sudoers (replace "USER" with "your_user_name")
`$USER' ALL=(ALL) NOPASSWD:ALL`

Get everything up to date and make sure security fixes get done automatically
`sudo apt update`
`sudo apt upgrade`
`sudo apt install unattended-upgrades`
`sudo dpkg-reconfigure --priority=low unattended-upgrades`
Uncomment the updates line in below if you want updates to be automatic too
`sudo nano /etc/apt/apt.conf.d/50unattended-upgrades`

Make a strong key for sshing
`ssh-keygen -t ed25519`

This works for Mint (and Ubuntu?)
`sudo apt install numlockx -y`

Install screen because it's really useful
`sudo apt install screen`

Add this function to .bashrc
You can set terminal titles with 'set-title whatever'
`set-title(){
  ORIG=$PS1
  TITLE="\e]2;$@\a"
  PS1=${ORIG}${TITLE}
}`

Add these lines to .inputrc to allow keyboard shortcut for moving a word at a time
`"\e[1;5C": forward-word   # ctrl + right`
`"\e[1;5D": backward-word  # ctrl + left`
