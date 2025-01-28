Configure dnf.conf
```shell
sudo tee -a /etc/dnf/dnf.conf << EOF
max_parallel_downloads=6
fastestmirror=True
defaultyes=True
EOF
```
```shell
sudo nano /etc/dnf/dnf.conf
```

Update system
```shell
sudo dnf update --refresh
sudo dnf distro-sync --refresh
sudo dnf autoremove
```
```shell
sudo dnf update --refresh -y && sudo dnf distro-sync --refresh -y && sudo dnf autoremove -y
```

Upgrade system
```shell
sudo dnf upgrade --refresh -y
sudo dnf install dnf-plugin-system-upgrade -y
sudo dnf system-upgrade download --releasever=42 -y
sudo dnf system-upgrade reboot
```

Install RPM fusion repositories (Free and Nonfree)
```shell
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

Enable openh264 library
```shell
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
```

AppStream metadata 
```shell
sudo dnf update @core -y
```

Add Mullvad / Tor Browser to your desktop's application menu
```shell
./start-mullvad-browser.desktop --register-app
```

```shell
./start-tor-browser.desktop --register-app
```

Add Mullvad VPN repository and install package

Stable repository
```shell
sudo dnf config-manager --add-repo https://repository.mullvad.net/rpm/stable/mullvad.repo
```
Beta repository
```shell
sudo dnf config-manager --add-repo https://repository.mullvad.net/rpm/beta/mullvad.repo
```
Install the package
```shell
sudo dnf install mullvad-vpn
```


---
Install flatpak and flathub Repository
```shell
sudo dnf install -y \
flatpak && flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
