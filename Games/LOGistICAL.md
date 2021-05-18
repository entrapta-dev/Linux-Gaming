# LOGistICAL *(Steam)*

## Requirements
This game, and many of its separately listed modules all use the exact same architecture and the fix for them is the same. I have not tested this with LOGistICAL 3 however as I do not own a copy.

LOGistICAL depends on Microsoft .NET which is (obviously) not installed on your average Linux distro so we'll have to use winetricks (or protontricks) to add it to the prefix. Depending on the version you are using you may run into errors that will halt the entire installation. For me a workaround was to switch to the development version of Wine temporarily and revert back after the .NET installation was finished.

## Steps
- If you have Protontricks installed you can try `protontricks 573060 -q dotnet472` which is the easiest and fastest way to install all the requirements.  
- If you only have Winetricks installed you can run `WINEPREFIX=<STEAM LIBRARY>/steamapps/compatdata/573060/pfx winetricks` where `<STEAM LIBRARY>` is the location of your Steam installation. Then follow the following steps:  
1. Select the default wineprefix  
2. Install a Windows DLL or component  
3. Scroll down and select `dotnet472` from the list and click Ok.  

Installation of .NET is cumbersome and will take up over 1.5GB of space when finished. You may need Accept terms and click Okay for Wine warnings during installation. It will go through several iterations of .NET making the entire process last several minutes.  

**Note:** When asked to restart *always* select `Restart later`. We're not actually running Windows here.  
