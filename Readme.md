# 👻 Install Kiro IDE on Linux (tar.gz) + Full Integration

This guide explains how to install **Kiro IDE** from a `.tar.gz` file
and integrate it into your system like a real IDE (launcher + CLI
support).

------------------------------------------------------------------------

## 🔗 Download link

Download the `.tar.gz` file from:\
https://kiro.dev/downloads/

------------------------------------------------------------------------

## 📦 1. Extract the archive

``` bash
tar -xvf kiro.tar.gz
cd Kiro
```

------------------------------------------------------------------------

## 🔍 1.2 Test the executable

``` bash
./kiro
```

If it opens, everything is working correctly. This step ensures the
binary works before continuing with the installation.

------------------------------------------------------------------------

## 🎨 1.3 Download an icon

For the `.desktop` launcher, download an icon to use. For example:

https://kiro.dev/icon.svg?fe599162bb293ea0

Save it as:

``` bash
/opt/Kiro/icon.svg
```

------------------------------------------------------------------------

## 📁 2. Move to /opt

``` bash
sudo mv ~/your_path/Kiro /opt/Kiro
```

------------------------------------------------------------------------

## 🖥️ 3. Create a desktop launcher

``` bash
nano ~/.local/share/applications/kiro.desktop
```

Paste:

``` ini
[Desktop Entry]
Name=Kiro IDE
Comment=Kiro IDE
Exec=/opt/Kiro/kiro %F
Icon=/opt/Kiro/icon.svg
Terminal=false
Type=Application
Categories=Development;IDE;
```

Make it executable:

``` bash
chmod +x ~/.local/share/applications/kiro.desktop
```

Now you can launch Kiro from your applications menu.

------------------------------------------------------------------------

## 💻 4. Add CLI support (like `code .`)

Remove any previous version if it exists:

``` bash
sudo rm /usr/local/bin/kiro
```

Create a wrapper:

``` bash
sudo nano /usr/local/bin/kiro
```

Paste:

``` bash
#!/bin/bash
setsid /opt/Kiro/kiro "$@" > /dev/null 2>&1 &
```

Make it executable:

``` bash
sudo chmod +x /usr/local/bin/kiro
```

------------------------------------------------------------------------

## ⚡ Usage

Open Kiro:

``` bash
kiro
```

Open a project:

``` bash
kiro .
```

------------------------------------------------------------------------

## ⚠️ Troubleshooting

### Sandbox issues

``` bash
/opt/Kiro/kiro --no-sandbox
```

### Missing dependencies (Arch) -probably next for fedora-

``` bash
sudo pacman -Syu libx11 libxkbcommon gtk3 nss alsa-lib
```

------------------------------------------------------------------------

## 🎯 Result

-   ✅ Launch from applications menu\
-   ✅ CLI support (`kiro .`)\
-   ✅ Terminal-free execution\
-   ✅ IDE-like behavior
