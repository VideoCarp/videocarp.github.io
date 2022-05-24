# Exporting your Map

Follow the process below.

### Finding your Directory

Click the > like thing to expand.

<details>
  <summary> Windows 10 </summary>
Open up the "Run" app, (shortcut Win+R) and insert this.<br>
`%LocalAppData%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang\minecraftWorlds`<br>
This will find the Minecraft Windows 10 Edition directory and you will see some folders here.<br>
  </details>

<details>
  <summary> iOS </summary>
Use the "files" app and find 'On my iPad' or 'On my iPhone', find Minecraft.<br>
  Now navigate like this:` games -> com.mojang -> minecraftWorlds`
  </details>

<details>
  <summary> Android </summary>
Use any file explorer app, and follow this path:<br>
`/sdcard/games/com.mojang/`
</details>

### Continuing

#### This part is for how to do the rest after finding your minecraftWorlds folder.

Now that you've found your minecraftWorlds folder, select a sorting option for your folders.
Preferably, if available sort by which was last edited, tne most recently edited one, if you exited properly
should be the correct map, read the `level_name.txt` file, if it has the correct name,
Now, you would need to have some way of compressing and renaming files, renaming files should be covered for
Windows and Android, for iOS, use iZip.
it is the correct world. Now that you have the exact folder, and the correct apps you need for your map, follow this process: 

- Compress the **_contents_** of the folder.
  Zip the contents of the folder, not the folder itself, otherwise your .mcworld will fail to import.
- Rename to `your_map's_name`
  You don't need to make it match anything, just use plain text. Do not use `§eYellow` for example, it is unecessary and makes your installer look bad.
- Change the zip file's extension to `.mcworld`
  You've got your compressed folder now set up. Try testing it!
  
