# S20Debloat

An S20 debloat list using adb. Credit to N7-BADA for most of this.

### Requirements

- Have ADB installed on your computer:
  - On Debian Linux, you can install adb with `sudo apt install adb`. Otherwise check this guide on xda: https://www.xda-developers.com/install-adb-windows-macos-linux/.

- Enable USB debugging in your phone's Developer Options:
  - Go to Settings > About phone > Software Information and keep tapping "Build number" until it says you've enabled Developer Options.
  - Go back to the main Settings page, go into Developer Options, and enable USB debugging.

I've seen people using adb in Termux (a terminal emulator on Android) too so try that if you don't have a computer.

### Usage

1. Connect your phone and computer:
   1. Plug your phone into your computer with a USB cable.
   2. On your computer, open up a terminal and type `adb devices`.
   3. On your phone, you should see a prompt asking if you trust this computer, click Allow.
   
2. Enter this command: `adb shell`.

3. Copy and paste* the [DEBLOAT] list into the shell.
   1. *You may not want to uninstall everything in the list. For example, `pm uninstall -k --user 0 com.sec.android.app.samsungapps`  will uninstall the Galaxy Store. Feel free to open the list in a text editor and remove any lines you wish before entering them into the shell.
   
4. Close the shell by typing `exit`.

### Extra (root)

Lots of people have been seeing Game Optimisation Service popping back up again after using `pm uninstall (...)`. **If you have root**, you can get around this as follows ([thanks to justin22](https://forum.xda-developers.com/t/force-remove-gameoptimizationservice-howto.4223511/post-84705313)):

1. Open a terminal and enter `adb shell`.
2. If you've already removed the app with the debloat list, reinstall it with `cmd package install-existing com.samsung.android.game.gos`.
3. Enter `su` and accept the prompt on your device to give superuser access to "Shell" ([screenshot](https://imgur.com/yLGRKUL)). If you can, select to only grant access temporarily/once.
4. Enter `pm hide com.samsung.android.games.gos`.
5. Exit su by entering `exit`. Exit the shell by entering `exit` again. Done!

You can undo this by substituting the command in step 4 with `pm unhide com.samsung.android.games.gos`.
