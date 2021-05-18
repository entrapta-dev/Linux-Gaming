# Star Wars: The Old Republic *(Steam)*
Steam Store:  https://store.steampowered.com/app/1286830  
ProtonDB: https://www.protondb.com/app/1286830  

## Game Tweaks
Fix too fast camera speed by navigating to  
`<STEAM_LIBRARY>/steamapps/compatdata/1286830/pfx/drive_c/users/steamuser/Local Settings/Application Data/SWTOR/swtor/settings/`  
and edit  
`<ACCOUNT_NAME>_Account.ini`.  

Then find  
`Controls_CameraRotationSpeed = 0.1`  
and change it to anything lower than `0.1`. A setting `0.08` seems to work well.

If missing also add:  
`Controls_CameraMaxDistance = 25.0`  
which can help.
