# Linux-Gaming
Setting up Linux for optimal gaming. Along with specific game setup instructions and tweaks.

1. [Required packages and drivers](#Requirements)
2. [Hardware](#Hardware)
3. [Launchers](#Launchers)
4. [Steam Tweaks](#Steam-Tweaks)

---

# <a id="Requirements"></a>1. Required packages and drivers.

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

## Custom Steam Play compatibility tools
Sometimes the default Steam Play Proton tool just won't work and you'll need to use another compatibility tool in order to get a game working.  

The tools listed below need to be downloaded and extracted into the `compatibilitytools.d` directory which is usually located in `~/.local/share/Steam/compatibilitytools.d`. If it does not exist yet, create it.  

### Proton GloriousEggroll Custom
Running games with this custom version of Proton can fix games that are not (yet) working with regular Proton. This is often due to propriety licenses, e.g.: `.NET`.  
https://github.com/GloriousEggroll/proton-ge-custom

### Boxtron
Steam Play compatibility tool to run DOS games using native Linux DOSBox instead if the provided Windows version.  
https://github.com/dreamer/boxtron

### Roberta
Steam Play compatibility tool to run adventure games using native Linux ScummVM instead if the provided Windows version. Example: [Beneath A Steel Sky](https://store.steampowered.com/app/1368340/Beneath_a_Steel_Sky/).  
https://github.com/dreamer/roberta

**Note:** The above tools will show up after a Steam restart.  

---

# <a id="Hardware"></a>2. Hardware

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

## Steam Link
The hardware version of the Steam Link is a great tool to stream your games from your main gaming PC to any other device like your TV. However, there is a significant audio bug present when streaming from Linux devices which only has a workaround for now but no actual fix.  

### Audio degradation / loss after 1+ hour of streaming
If you experience audio crackling or just plain disappearing after 1-2 hours of continuous streaming then this workaround may fix the issue.  
- Make sure you are not currently streaming to the Steam Link.  
- Turn all audio device profiles to `Off` on the streaming source until it lists `Dummy Output` as your Playback Device.  
- Start streaming to the Steam Link.  

---

# <a id="Launchers"></a>3. Launchers

## Epic Games Store Launcher
First install [legendary](https://github.com/derrod/legendary) via:  
```
pip install legendary-gl
```

Then add [Heroic Launcher](https://github.com/flavioislima/HeroicGamesLauncher) for a fancy GUI. I recommend the `.deb` over the Appimage.

Run Heroic Launcher once, it will ask you to log in to the Epic Games Store and get the ssid you'll need to copy over in order to automatically log in and get the games list.


## Lutris
Add the lutris repo with `sudo add-apt-repository ppa:lutris-team/lutris` and then install with `sudo apt install lutris`.  

### Stuck on "Starting".
2021-03-25: Bug. Just press `Esc` once to have it start the main app. You can do it again to close the launcher window after.


### Create symbolic link to move runners to external drive, saving space

Move runners from `.local`  to destination location first, then symlink using the following syntax format: `ln -s [DESTINATION] [SOURCE]`

Example:  
```
ln -s /media/Entrapta/Games/lutris-games/runners/ ~/.local/share/lutris/runners/
```

---

# <a id="Steam-Tweaks"></a>4. Steam app tweaks

## Custom screenshot folder
In Steam settings you can set a custom screenshot folder but it will not work unless you also check the box that reads `Save an uncompressed copy`. Screenshots will still be saved in the old standard location as well as the new one. Plus, deletion via the Steam interface will only delete from the default folder.
