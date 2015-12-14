# installfest
Instructions for installing work environment in OS X

# Install a clean version of OS X
### Create OS X Booteable
1. Download the OS X Installer app from the Mac App Store.

1. Use Disk Utility to erase the 8GB+ usb drive in Mac OS X Extended (Journaled) format and leave the drive name as "Untitled".

1. Make sure the El Capitan installer (or at least a copy of it), called Install OS X El Capitan.app, is in its default location in your main Applications folder (/Applications).

1. Run in terminal:
```
sudo /Applications/Install\ OS\ X\ El\ Capitan.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ El\ Capitan.app --nointeraction
```

### Booting from the installer drive
1. Restart the Mac holding down the alt(option) key.

1. Use Disk Utility to erase the Mac hard drive in Mac OS X Extended (Journaled) format.

1. Intall the OS X.

# OS X Preferences
### System Preferences
- Trackpad > Point & Click > Tap to click
- Trackpad > More Gestures > Swipe between pages > uncheck
- Dock > Size > Small
- Dock > Automatically hide and show the Dock
- Keyboard > Shortcuts > Full keyboard access > All controls
- Keyboard > Shortcuts > Keyboard > Move focus to next window > CMD + §(spa) or CMD + `(eng)
- Security & Privacy > Allow apps downloaded from > Anywhere
- Energy Saver > Battery & Power Adapter > Computer Sleep > Never
- Energy Saver > Battery & Power Adapter > uncheck "Put hard disks to sleep when possible"
- Energy Saver > Battery > uncheck "Slightly dim the display while on battery power"
- Date & Time > Clock > Date options > Show date

### Other Preferences
- Show hidden files:
```
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```
- Right click on Battery > Show percentage

### Finder Preferences
- General > New Finder windows show > Downloads
- Sidebar > Favorites > Applications, Desktop, Documents, Downloads
- Sidebar > Tags > Uncheck Recent Tags
- Advanced > Check Show all filename extensions
- Advanced > When performing a search > Search the current folder
- Add HD & User to favorites

# Bash
1. Check if you have a `.bashrc` file in your home directory. Open your terminal and type `ls ~/.bashrc`. If you receive a warning saying no such file or directory exists, type `touch ~/.bashrc`. This creates an empty file for us.

2. Check if you have a `.bash_profile` in your home directory. Open your terminal and type `ls ~/.bash_profile`. If you receive a warning saying no such file or directory exists, type `touch ~/.bash_profile`.

3. Execute the follow commands at the terminal.
```
echo 'export PATH=/usr/local/bin:$PATH' >> ~/.bash_profile
```
```
echo 'test -f ~/.bashrc && source ~/.bashrc' >> ~/.bash_profile
```

4. Check `.bash_profile` to make sure it has the contents we expect. Type `cat ~/.bash_profile` in the terminal to look at the contents of the file. Near the bottom, you should have something that looks like this:
```
# ~/.bash_profile

export PATH=/usr/local/bin:$PATH
test -f ~/.bashrc && source ~/.bashrc
```

5. Update `/etc/paths` by running the following commands.

```
echo '/\/usr\/local\/bin/\nd\nwq' | sudo ed /etc/paths
```
```
echo '1i\n/usr/local/bin\n.\nwq' | sudo ed /etc/paths
```

6. Inspect our changes by typing `cat /etc/paths`. It should look like this:

```
# /etc/paths

/usr/local/bin
/usr/bin
/bin
/usr/sbin
/sbin
```

# APPS
### Chrome

### Google Drive

### Spotify

### Hipchat

### Skipe

### Jumpcut
- System Preferences > Users & Groups > Login Items > Jumpcut
- Preferences > General > Display in menu > 40
- Preferences > Hotkeys > Main hotkey > CMD + ALT + c

### Xcode
1. Install Xcode from the AppStore.
1. Open Xcode to agree terms and conditions, and close it.