# installfest
Instructions for installing work environment in OS X

# Install a clean version of OS X
### Create OS X Booteable
1. Download the OS X Installer app from the Mac App Store.

1. Use Disk Utility to erase the 8GB+ usb drive in `Mac OS X Extended (Journaled)` format and leave the drive name as "Untitled".

1. Make sure the El Capitan installer (or at least a copy of it), called Install OS X El Capitan.app, is in its default location in your main Applications folder (/Applications).

1. Run in terminal:
  ```
  sudo /Applications/Install\ OS\ X\ El\ Capitan.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled --applicationpath /Applications/Install\ OS\ X\ El\ Capitan.app --nointeraction
  ```

### Booting from the installer drive
1. Restart the Mac holding down the `alt` or `option` key.

1. Use Disk Utility to erase the Mac hard drive in Mac OS X Extended (Journaled) format.

1. Install the OS X.

# OS X Preferences
### System Preferences
- `Trackpad > Point & Click > Tap to click`
- `Trackpad > More Gestures > Swipe between pages > uncheck`
- `Dock > Size > Small`
- `Dock > Automatically hide and show the Dock`
- `Keyboard > Shortcuts > Full keyboard access > All controls`
- `Keyboard > Shortcuts > Keyboard > Move focus to next window > CMD + §(spa) or CMD + `(eng)`
- `Security & Privacy > Allow apps downloaded from > Anywhere`
- `Energy Saver > Battery & Power Adapter > Computer Sleep > Never`
- `Energy Saver > Battery & Power Adapter > uncheck "Put hard disks to sleep when possible"`
- `Energy Saver > Battery > uncheck "Slightly dim the display while on battery power"`
- `Date & Time > Clock > Date options > Show date`

### Other Preferences
- Show hidden files by running this code into the terminal:
  ```
  defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
  ```
- Right click on `Battery > Show percentage`

### Finder Preferences
- `General > New Finder windows show > Downloads`
- `Sidebar > Favorites > Applications, Desktop, Documents, Downloads`
- `Sidebar > Tags > Uncheck Recent Tags`
- `Advanced > Check Show all filename extensions`
- `Advanced > When performing a search > Search the current folder`
- Add HD & User to favorites

# Bash
1. Check if you have a `.bashrc` file in your home directory. Open the terminal and type `ls ~/.bashrc`. If you receive a warning saying no such file or directory exists, type `touch ~/.bashrc`. This creates an empty file for us.

1. Check if you have a `.bash_profile` in your home directory. Open the terminal and type `ls ~/.bash_profile`. If you receive a warning saying no such file or directory exists, type `touch ~/.bash_profile`.

1. Execute the follow commands at the terminal.
  ```
  echo 'export PATH=/usr/local/bin:$PATH' >> ~/.bash_profile
  ```
  ```
  echo 'test -f ~/.bashrc && source ~/.bashrc' >> ~/.bash_profile
  ```

1. Check `.bash_profile` to make sure it has the contents we expect. Type `cat ~/.bash_profile` in the terminal to look at the contents of the file. Near the bottom, you should have something that looks like this:
  ```
  export PATH=/usr/local/bin:$PATH
  test -f ~/.bashrc && source ~/.bashrc
  ```

1. Update `/etc/paths` by running the following commands.

  ```
  echo '/\/usr\/local\/bin/\nd\nwq' | sudo ed /etc/paths
  ```
  ```
  echo '1i\n/usr/local/bin\n.\nwq' | sudo ed /etc/paths
  ```

1. Inspect our changes by typing `cat /etc/paths`. It should look like this:

  ```
  /usr/local/bin
  /usr/bin
  /bin
  /usr/sbin
  /sbin
  ```

# APPS
### Install Chrome, Google Drive, Spotify, Hipchat, Skype.

### Jumpcut
- `System Preferences > Users & Groups > Login Items > Jumpcut`
- `Preferences > General > Display in menu > 40`
- `Preferences > Hotkeys > Main hotkey > CMD + ALT + c`

### Xcode
1. Install Xcode from the AppStore.
1. Open Xcode to agree terms and conditions, and close it.

### Command Line Tools
Run in terminal `xcode-select --install` and then click install.

### Homebrew
1. Go to [Homebrew's page](http://brew.sh/), and copy the entire command listed under "Install Homebrew", then paste it into the terminal.

1. Run `brew doctor` into the terminal.

  **NOTE: YOUR SYSTEM WILL PROBABLY THROW SOME ERRORS HERE!** Some of these errors are probably minor, but some might not be; please wait until one of the instructors has given you the go-ahead before moving on.

1. Once Homebrew says `Your system is ready to brew`, run  `brew update` to update Homebrew's directory of packages.

### NVM and Node/NPM
1. Run `brew install nvm` into the terminal.

1. Add the following snippet to your bash configuration file `.bash_profile`.
  ```
  export NVM_DIR=~/.nvm
  source $(brew --prefix nvm)/nvm.sh
  ```

1. Use NVM to install the latest stable version of Node:
  ```
  nvm install stable
  ```

1. Use NPM to install important Node modules and make them available across all of our projects:
  ```
  npm install -g jshint grunt-cli bower yo gulp
  ```

1. Install the node version for the AMEX project:
  ```
  nvm install 0.10.26
  ```
  ```
  nvm use 0.10.26
  ```
  ```
  nvm alias default 0.10.26
  ```

1. Update NPM:
  ```
  npm install npm -g
  ```

# Sublime Text 3
### Installation
1. Download the latest Sublime Text build from [Sublime's page](http://www.sublimetext.com/3).

1. Enter the following into your terminal - it will create a 'symlink', a shortcut that we can use to open Sublime from the command line:
  ```
  ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
  ```

### Custom Preferences
1. Go to `Sublime Text > Preferences > Settings - User` and replace the entire content with the following:

  ```
  {
    "close_windows_when_empty": false,
    "font_size": 12,
    "ignored_packages":
    [
      "Vintage"
    ],
    "open_files_in_new_window": false,
    "scroll_past_end": true,
    "tab_size": 2,
    "translate_tabs_to_spaces": true,
    "word_wrap": true
  }
  ```

1. Go to `Sublime Text > Preferences > Key Bindings - User` and replace the entire content with the following:

  ```
  [
    { "keys": ["super+shift+m"],
      "command": "insert_snippet",
      "args": {
        "contents": "console.log('${1:}$SELECTION');${0}"
      }
    },
    { "keys": ["super+shift+j"],
      "command": "insert_snippet",
      "args": {
        "contents": "('.${1:}$SELECTION');${0}"
      }
    }
  ]
  ```

1. Hide Minimap in `View > Hide Minimap`

### Package Manager
##### Install the Package Manager
1. Go to [Package Control's page](https://packagecontrol.io/installation) and copy the code.
1. Hit `ctrl + `` to enter the Sublime Text console, and paste the installation code.

##### Install Add-On Packages
1. Hit `command + shift + p` to enter the Command Pallette; and enter `install` into the search bar to open the package manager.
1. Install each of the following plugins:

  - [All Autocomplete](https://github.com/alienhard/SublimeAllAutocomplete): Extends the default autocomplete to find matches in all open files. By default Sublime only considers words found in the current file.
  - [AngularJS](https://github.com/angular-ui/AngularJS-sublime-package)
  - [BeautifyRuby](https://github.com/CraigWilliams/BeautifyRuby)
  - [Better CoffeeScript](https://github.com/aponxi/sublime-better-coffeescript)
  - [Dotfiles Syntax Highlighting](https://github.com/mattbanks/dotfiles-syntax-highlighting-st2): Want ShellScript (Bash) syntax highlighting for your dotfiles? You're damn right you do!
  - [GitGutter](https://github.com/jisaacks/GitGutter): A sublime text 2/3 plugin to show an icon in the gutter area indicating whether a line has been inserted, modified or deleted.
  - [Haml](https://packagecontrol.io/packages/Haml)
  - [Handlebars](https://github.com/daaain/Handlebars)
  - [HTML5](https://packagecontrol.io/packages/HTML5): Add HTML5 syntax mode & snippets to Sublime Text.
  - [jQuery](https://github.com/SublimeText/jQuery): This is a Sublime Text bundle to help with jQuery functions. It has syntax highlighting and almost all of the jquery methods as snippets.
  - [Sass](https://packagecontrol.io/packages/Sass): Sass support for TextMate & Sublime Text (2 & 3).

# Git, GitHub and Bitbucket
### Install Git
Run `brew install git` into the terminal.

### Configuring Git
1. Paste the following code into the bottom of the `.bashrc` file:
  ```
  # Git
  function parse_git_branch {
    ref=$(git symbolic-ref HEAD 2> /dev/null) || return
    echo "("${ref#refs/heads/}")"
  }
  export PS1="\w \$(parse_git_branch)\$ "
  ```

1. Colorize git in the command line:
  ```
  git config --global color.ui true
  ```

1. Set up a global 'excludesfile', listing all the files that we might want git to ignore:
  ```
  git config --global core.excludesfile ~/.gitignore
  ```
  ```
  echo ".DS_Store" >> ~/.gitignore
  ```

1. Set a default user:
  ```
  git config --global user.name "dquijano-bairesdev"
  ```
  ```
  git config --global user.email "bairesdev_dquijano@iseatz.com"
  ```  