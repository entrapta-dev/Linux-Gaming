# Final Fantasy XIV Online *(Steam)*

**Note!** It is crucial that new accounts are made on the website and not the launcher or there will be a 24 hour lockout on the email address used. Use the CD-Key(s) you got from Steam when first purchasing the game.  
More info here: https://support.na.square-enix.com/faqarticle.php?id=5382&la=1&kid=76363  

---

## Installation

Download the Final Fantasy XIV Launcher through Steam.  
Run it once until it gets stuck on the logo.  
Quit the launcher.  

Go to `/steamapps/compatdata/39210/pfx/drive_c/users/steamuser/My Documents/My Games/FINAL FANTASY XIV - A Realm Reborn/` and edit `FFXIV_BOOT.cfg`.  

Change `Browser` from `2` to `1`.  
Change `StartupCompleted` from `0` to `1`.  

Run the launcher again.  
Accept the Agreement.  
Enter your Square Enix ID and password.  

**Important!** Do NOT click the `Log In` button. It will lock up the launcher. Instead just press Enter.  

Accept another agreement.  

It should now start downloading the game. This will take some time.  

Once finished, start the game and pick your data center.

It will now seemingly lock up with a black screen.  
Close the game.  

Go to `/steamapps/compatdata/39210/pfx/drive_c/users/steamuser/My Documents/My Games/FINAL FANTASY XIV - A Realm Reborn/` and edit `FFXIV.cfg`.  

Change `CutsceneMovieOpening` from `0` to `1`.  

Open the game again and everything should now work just fine.
