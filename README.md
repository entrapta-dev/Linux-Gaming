# Linux-Gaming
Setting up Linux for optimal gaming. Along with specific game setup instructions and tweaks.

1. Required packages and drivers.
2. Hardware
3. Launchers

---

# 1. Required packages and drivers.

## Wine
Enable 32-bit architecture if you haven't already:  
```
sudo dpkg --add-architecture i386
```

Get the Wine repository key:  
```
wget -nc https://dl.winehq.org/wine-builds/winehq.key
sudo apt-key add winehq.key
```

Add the Wine repository:  
```
sudo add-apt-repository 'deb https://dl.winehq.org/wine-builds/ubuntu/ focal main'
```

Run apt update:  
```
sudo apt update
```

Install **stable** branch:  
```
sudo apt install --install-recommends winehq-stable
```

Check Wine version with:  
```
wine --version
```

## Proton GloriousEggroll Custom
Running games with this custom version of Proton can fix games that are not (yet) working with regular Proton. This is often due to propriety licenses, e.g.: `.NET`.  
https://github.com/GloriousEggroll/proton-ge-custom

---

# 2. Hardware

## XBOX 1914 Gamepad
In order to use this new XBOX gamepad you will need to install [xow](https://github.com/medusalix/xow) which will enable the XBOX wireless dongle we'll be using.  

Clone the repository:  
```
git clone https://github.com/medusalix/xow
```

Build it:  
```
make BUILD=RELEASE
```

Set it as a `systemd` unit and make it run on startup:  
```
sudo make install
sudo systemctl enable xow
sudo systemctl start xow
```

Reboot or you will run into a `LIBUSB_ERROR_ACCESS` error.  

After this you will likely run into a `Mt76Exception` error which means it failed to load the firmware. Unplug the dongle and run:  
```
sudo systemctl restart xow
```

After that reinsert the dongle and turn on the gamepad.  

Run:  
```
sudo systemctl status xow
```
to check if there are any errors left. If the gamepad needs pairing, do so now. Disable Bluetooth in the meantime to prevent mishaps.

---

# 3. Launchers

## Epic Games Store Launcher
First install [legendary](https://github.com/derrod/legendary) via:  
```
pip install legendary-gl
```

Then add [Heroic Launcher](https://github.com/flavioislima/HeroicGamesLauncher) for a fancy GUI. I recommend the `.deb.` over the Appimage.

Run Heroic Launcher once, it will ask you to log in to the Epic Games Store and get the ssid you'll need to copy over in order to automatically log in and get the games list.

---

# 4. Steam app tweaks

## Custom screenshot folder
In Steam settings you can set a custom screenshot folder but it will not work unless you also check the box that reads `Save an uncompressed copy`. Screenshots will still be saved in the old standard location as well as the new one. Plus, deletion via the Steam interface will only delete from the default folder.
