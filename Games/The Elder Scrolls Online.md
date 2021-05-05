# The Elder Scrolls Online *(Steam)*

**Note!** When installing to a Steam Library folder that is not on your home location it may error out when trying to update the launcher, see the notes below to rectify that.

---

## Installation

Download and install from Steam.  
Once done add the following in launch options: `PROTON_NO_ESYNC=1 %command%`

Run the game.  
Press OK on Launcher  
Continue  
Accept License Agreement  

### Not enough space / Installation Path is not writable

You may encounter this error if you install anywhere but the default Steam home location. Though it's been reported in other scenarios as well.  

Quit the launcher.  

Go to `<STEAM LIBRARY>/steamapps/common/Zenimax Online/` and run `setup.exe` through wine _(right-click to open in Wine Windows Program Loader)_  

Complete the installation. It will say it will have to use 20GB of space but in reality it is only like 200MB for the Launcher, which is what we need.  It should only take a few seconds to complete.  

This should have installed the Launcher in `~/.wine/drive_c/Program Files (x86)/Zenimax Online/`.  
Now copy that entire `Launcher` folder to `steamapps/common/Zenimax Online/`  

Run the game from Steam again.  
Launcher will now run and update if needed.  

## Note

The loading screen before Character Selection may take some time depending on server load. Just wait it out.
