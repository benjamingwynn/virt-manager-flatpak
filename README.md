# virt-manager flatpak

This is a fork of [tinywrkb's project](https://github.com/tinywrkb/flatpaks) of Flatpaks with just the [virt-manager](https://virt-manager.org/) Flatpak. Configs have been changed to be compatible with Gnome 40.

This is made for my own convenience so I can quickly manage my remote virtual machines running on my server with [Fedora Silverblue 34](https://silverblue.fedoraproject.org) clients. For that reason, I've only tested remote libvirt access over SSH, which works and fits my use-case.

### How to build

1. Install flatpak-builder
2. Install Gnome 40 platform tools and SDK
```
# You might need the beta repos if Gnome 40 is still in Beta
flatpak remote-add flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo

# Install tools and sdk, pick Gnome 40 version(s) if asked
flatpak install org.gnome.Platform
flatpak install org.gnome.Sdk
```
3. Clone this repo
```
git clone https://github.com/benjamingwynn/virt-manager-flatpak.git --recursive
```

4. Build the `libvirt` package with flatpak-builder and install it as a user Flatpak app
```
flatpak-builder --install --user --force-clean --state-dir=build/flatpak-builder --repo=build/flatpak-repo build/flatpak-target org.libvirt.libvirt.BaseApp/org.libvirt.libvirt.BaseApp.yaml
```

5. Build the `virt-manager` package with flatpak-builder and install it as a user Flatpak app
```
flatpak-builder --install --user --force-clean --state-dir=build/flatpak-builder --repo=build/flatpak-repo build/flatpak-target org.virt_manager.virt-manager/org.virt_manager.virt-manager.yaml
```

### Credit

Major kudos to [tinywrkb](https://github.com/tinywrkb) for the original repo containing loads of Flatpak's for commonly used applications, check it out [here](https://github.com/tinywrkb/flatpaks)