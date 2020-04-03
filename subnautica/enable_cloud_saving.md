# Subnautica Cloud Saving

Yes, it's true, there is a way to enable cloud saving for Subnautica!

It is **NOT** built-in to the game, nor is it a steam *feature*.

Note: I have only tested this with Windows 10, Subnautica for Steam, and OneDrive. There may be other methods to get this working.

1. **BACKUP YOUR SAVE FILES**
    - I *cannot* stress this enough.
    - Navigate to your Subnautica save file directory (typically in `C:\Program Files(x86)\Steam\steamapps\common\Subnautica\SNAppData\`).
    - Make a copy of the `SavedGames` folder.
2. **Create the 'cloud' directory**
    - Navigate to your OneDrive and create the folder that will hold your game files.
    - Right click on the folder you just made and select `Always keep on this device`.
    - That will ensure that it's always downloaded to the computer and not just visible/waiting to be used.
3. **Move SavedGames folder**
    - Pretty self explanatory, simply move the SavedGames folder from it's original location to the new OneDrive location we created.
4. **Set up Symbolic Link**
    - It's important to understand that a shortcut and a symbolic link are not quite the same thing, so simply making a shortcut may not work how one would think.
    - Open up an administrator command prompt (Windows Key -> Type 'cmd' -> right click -> click 'run as administrator').
    - Type: 
        ```
        symlink /D DriveLetter:\Default\Location\To\Subnautica\Saved\Files\Directory\SavedGames DriveLetter:\Your\OneDrive\SavedGames\Folder
        ```
    - symlink will create the symbolic soft link, /D specifies we're linking a directory
    - If your default game files are as specified before, your command *might* look like this (depending on where you made your OneDrive folder): 
        ```
        symlink /D "C:\Program Files(x86)\Steam\steamapps\common\Subnautica\SNAppData\SavedGames" C:\Users\artic0de\OneDrive\Games\Subnautica\SavedGames
        ```
    - Notice the quotations marks around `"C:\Program Files(x86)\Steam\steamapps\common\Subnautica\SNAppData\SavedGames"`. This is because `Program Files(x86)` has a space in it. If you type it without the quotation marks, it will give you an error.
    - Remember: the first path in the command is *where the link will be* and the second path is *where the actual directory is*. This link is taking the place of the directory's original location, so the game files will first go to the link which will bring it to your OneDrive folder.
5. **Repeat Step 4 for each computer**
    - This part can get tricky. For example: if you already have two different save files, make sure each folder in all of your `SavedGames` directories has a different name. If one computer has a `slot0000` folder and another also has a `slot0000` folder, rename one of them to `slot0001`. 
    - Make sure you once again select `Always keep on this device` on your other computer as well. You shouldnt have to remake the OneDrive folder, and you should already see the files from your first computer. So all you really should have to do is add the `SavedGames` folder, which should merge and make you decide which `options` folder to keep.
 6. **Restoring from backup**
    - If you messed up and need to restore your backup save folder, all you have to do is rename it to `SavedGames`.
    - Keep in mind, if you played and saved to the cloud-saved folder, your backup will not have ANY of those changes. It will be exactly where you were at when you first made the backup.
