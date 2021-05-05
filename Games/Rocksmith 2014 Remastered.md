# Rocksmith 2014 Edition - Remastered *(Steam)*
First of all, be sure to check out the [ProtonDB page](https://www.protondb.com/app/221680) for any new potential issues.  

This will assume you are using the official RealTone cable.

## Normal steps
1. Install the game in the usual way but be sure to select the default Steam library folder on your `home` partition. It is unclear not doing so still causes issues but installing it in a library on an external drive has prevented the game from working in the past. On Kubuntu 20.04 LTS this is `~/.steam/steam/` but your mileage may vary. Another common location is `~/.steam/debian-installation/`. Replace entries below with your specific path.

2. Edit `Rocksmith.ini` in `~/.steam/steam/steamapps/common/Rocksmith2014/` to ensure the following is there:  
```
[Audio]
EnableMicrophone=0
ExclusiveMode=0
LatencyBuffer=2
ForceDefaultPlaybackDevice=
ForceWDM=0
ForceDirectXSink=0
DumpAudioLog=0
MaxOutputBufferSize=0
RealToneCableOnly=1
Win32UltraLowLatencyMode=0
```
You may need to run the game once to create this file.  

3. Place your copy of `D3DX9_42.dll` in the base game folder. Same as above. This will enable Custom DLC (CDLC).  

4. Place any custom DLC you own in a separate folder inside the `dlc` folder. The `dlc` folder is where the official DLC goes; don't clutter this up.  

5. Specify the audio devices for the game to use.  
First ensure it uses `alsa` for sound processing:  
```
WINEPREFIX=~/.steam/steam/steamapps/compatdata/221680/pfx winetricks sound=alsa
```

Then completely kill `pulseaudio` via:  
```
pulseaudio -k
```

And finally run:
```
WINEPREFIX=~/.steam/steam/steamapps/compatdata/221680/pfx winecfg
```
To select the Rocksmith audio cable as both input devices and the Analog option for both Output devices.

You should now have a working Rocksmith 2014 Remastered. You *may* need to reboot to re-enable pulseaudio.
