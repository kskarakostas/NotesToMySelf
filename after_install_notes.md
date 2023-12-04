# Keys remapping

## Changing the key to Super (akaWindows or ⌘)
```
gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier '<Alt>'
gsettings set org.gnome.desktop.wm.preferences resize-with-right-button true
```

## Middle Click
```
gsettings set org.gnome.desktop.peripherals.touchpad middle-click-emulation true
```


## Switch langs
```
gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Shift>Alt_L']"
gsettings set org.gnome.desktop.wm.keybindings switch-input-source-backward "['<Alt>Shift_L']"
```



# Basic installs
```
sudo apt update && sudo apt upgrade -y

sudo apt install apt-transport-https gnupg2 software-properties-common apt-transport-https wget -y

sudo apt-get -y install htop nvtop bashtop

sudo add-apt-repository ppa:deadsnakes/ppa

```
