# Installation Steps

## Create a container (optional unless you have BoxBuddy installed)

```
distrobox-create --name muffin-signal --image debian:latest
```

## Open your container:
```
distrobox-enter muffin-signal
```

## Install Signal on it:

### Update container:
```
sudo apt update && sudo apt upgrade
```
### Install Signal's official public software signing key:
```
mkdir $HOME/.signal/ && cd $HOME/.signal/ && wget -O- https://updates.signal.org/desktop/apt/keys.asc | gpg --dearmor > signal-desktop-keyring.gpg
```
```
cat signal-desktop-keyring.gpg | sudo tee /usr/share/keyrings/signal-desktop-keyring.gpg > /dev/null
```

### Add Signal's repository to your list of repositories:
```
echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main' | sudo tee /etc/apt/sources.list.d/signal-xenial.list
```
### Update your package database and install Signal:
```
sudo apt update && sudo apt install signal-desktop
```
## Show your app in the main menu:
```
distrobox-export --app signal-desktop
```
