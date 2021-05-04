# Fallout 4 *(Steam)*

## Fixes / Tweaks

### Audio not playing / not playing correctly
If you're having issues hearing all the audio, like missing speech and music, set the launcher options to:  
`WINEDLLOVERRIDES="xaudio2_7=n,b" PULSE_LATENCY_MSEC=90 %command%`


### Fullscreen fix
Change the `Fallout4Prefs.ini` file in `/steamapps/compatdata/377160/pfx/drive_c/users/steamuser/My Documents/My Games/Fallout4/` to the following:  

```
bMaximizeWindow=1
bBorderless=1
bFull Screen=0
iSize H=1080
iSize W=1920
```


### Stuck on White Screen at character creation
- Run the game via the official launcher (not f4se) and go into advanced graphic options and disable `Wetness`.

---

## Useful Console Commands

### Low res textures at Thicket Excavation site.
- Quit to menu, reload.

### Lost Dogmeat
- Open Console (\`)
- Enter: `prid0001d162`
- Enter: `moveto player`
- Close Console (\`)
