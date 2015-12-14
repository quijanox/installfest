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

# APPS
### Chrome
### Google Drive