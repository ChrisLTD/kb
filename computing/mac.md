# Mac

## App Favorites

I've left default Apple apps off this list \(like Calendar, and Music\), but I use those as well.

* [1Password](https://1password.com/) - Password vault
* [Acorn](https://flyingmeat.com/acorn/) - Image editor
* [Arq Backup](https://www.arqbackup.com/) - Backup archived files to B2 or S3
* [Backblaze](https://www.backblaze.com/) - Backup entire computer
* [BBEdit](https://www.barebones.com/products/bbedit/) - Lightweight text editor
* [Be Focused Pro](https://apps.apple.com/us/app/be-focused-pro-focus-timer/id961632517?mt=12) - Pomodoro timer
* [CodeRunner](https://coderunnerapp.com/) - Playground for different programming languages
* Creative Cloud - I use this just for Photoshop.
* [DaisyDisk](https://daisydiskapp.com/) - Helps cleanup old files
* [Dropbox](https://www.dropbox.com/) - Sync files
* [Encrypt.me](https://encrypt.me/) - VPN
* [Forecast](https://overcast.fm/forecast) - Edit tags for podcast mp3s
* [HandBrake](https://handbrake.fr/) - Convert video files
* [Hazel](https://www.noodlesoft.com/) - automate file cleanup and organization
* [HazeOver](https://apps.apple.com/us/app/hazeover-distraction-dimmer/id430798174?mt=12) - Darken inactive windows
* [ImageOptim](https://imageoptim.com/mac) - Batch compress images
* [IntelliJ](https://www.jetbrains.com/idea/) - IDE for web project
* [Keyboard Maestro](https://www.keyboardmaestro.com/) - Text snippets, and OS automation
* [MenuBar Stats](https://apps.apple.com/us/app/menubar-stats/id714196447?mt=12) - Keep track of runaway apps
* [Microsoft Edge](https://www.microsoft.com/en-us/edge) - Gives me the same dev tools as Google Chrome
* [Moom](https://manytricks.com/moom/) - Window management
* [Music Converter Pro](https://apps.apple.com/us/app/music-converter-pro/id468990782?mt=12) - Convert audio files
* [Patterns](https://apps.apple.com/us/app/patterns-the-regex-app/id429449079?mt=12) - Regex helper
* [Paw](https://paw.cloud/) - Debug HTTP requests
* [Piezo](https://rogueamoeba.com/piezo/) - Record audio
* [Reeder](https://reederapp.com/) - RSS reader
* [Rest](https://apps.apple.com/us/app/rest/id661067914?mt=12) - Make yourself to take screen breaks
* [RH Timers](https://apps.apple.com/us/app/rh-timer-manage-your-time/id929960914?mt=12) - Until Siri can do timers
* [Scrutiny](https://peacockmedia.software/mac/scrutiny/) - Check links for websites
* [Sequel Pro](https://www.sequelpro.com/) - GUI for MySQL
* [Soulver](https://acqualia.com/soulver/) - A better calculator
* [SourceTree](https://www.sourcetreeapp.com/) - Free Git GUI
* [SuperDuper!](https://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html)  - Full disk backup
* [Textual](https://apps.apple.com/us/app/textual-7/id1262957439?mt=12) - IRC client
* [Todoist](https://todoist.com/)  - Cross platform to do list service
* [ToothFairy](https://c-command.com/toothfairy/) - Connect to AirPods from menu bar
* [Transmit](https://panic.com/transmit/) - File transfer to remote 
* [TripMode](https://www.tripmode.ch/) - Throttle apps while on cellular data
* [Turbo Boost Switcher Pro](https://www.rugarciap.com/turbo-boost-switcher-for-os-x/) - Turn off CPU turbo boost while on battery power
* [Viscosity](https://www.sparklabs.com/viscosity/) - OpenVPN client
* [Visual Studio Code](https://code.visualstudio.com/) - Light code text editor
* [XScope](https://xscopeapp.com/) - Measure things on screen

### Apps to Consider

* [iStat Menus](https://bjango.com/mac/istatmenus/) - Keep track of runaway apps
* [BlockBlock](https://objective-see.com/products/blockblock.html) - Get alerts when apps try to install background processes
* [LuLu](https://github.com/objective-see/LuLu) - Open Source LittleSnitch alternative, blocks outgoing apps
* [Hidden](https://github.com/dwarvesf/hidden) - Open Source bartender alternative
* [Timer](https://github.com/Zeqiang-Lai/Timer-APP) - Open Source timer app
* [SwiftBar](https://github.com/swiftbar/SwiftBar) - Put the results of scripts in your menu bar
* [CleanShot X](https://cleanshot.com) - Screenshot tool
* [Suspicious Package](https://www.mothersruin.com/software/SuspiciousPackage/) - Inspect MacOS installers
* [Mouseless](https://mouseless.app) - Keyboard shortcut trainer
* [VimMotion](https://github.com/dwarvesf/VimMotionApp) - Vim like keyboard nav for Mac
* [Blurred](https://github.com/dwarvesf/Blurred) - Open Source alternative to HazeOver
* Parallels -Virtual Machines
* Time Out - Take breaks
* [LaunchControl](https://www.soma-zone.com/LaunchControl/) - Manage and debug system services

### Retired Apps

* [Bartender](https://www.macbartender.com/) - Organize Mac menu bar
* Virtual Box - X86 virtual machines

## Keyboard shortcuts of note

* Dictation - Double Tap Right Command 
* Siri - Hold Opt Space 
* Keyboard Maestro Macro - Ctrl Opt Cmd T
* Lock Screen / Put Display to Sleep - Ctrl Shift Q 
* Clipboard History \(KM\) - Ctrl Opt Cmd V 
* 1Password Autofill - Cmd  
* 1Password Global - Cmd Shit \

_\(KM\): Custom Keyboard Maestro shortcut_

## Useful Terminal Commands

[Check disk stats like lifetime read and writes](https://twitter.com/never_released/status/1358539964460511233): `$ smartctl --all /dev/disk0`

2017 MacBook Pro \(about ~3 years of usage\):  
Data Units Read:                    746,318,540 \[382 TB\]  
Data Units Written:                 100,074,549 \[51.2 TB\]  
Power On Hours:                    1,349

Check system uptime: `$ uptime`

Check system sleep / wake cycles: `$ pmset -g log|grep -e " Sleep " -e " Wake "`

## Backup Exclusions

### Time Machine

* ~/.dropbox
* ~/Dropbox/.dropbox
* ~/Dropbox/.dropbox.cache
* ~/Library/Containers/com.docker.docker
* docker.driver.amd64-linux/Docker.raw
* ~/Library/Application Support/Developer/Xcode/iOS DeviceSupport
* ~/Library/Application Support/Developer/Xcode/watchOS DeviceSupport

### Backblaze

* ~/Library/Containers/com.docker.docker
* ~/Library/Application Support/NVIDIA
* docker.driver.amd64-linux/Docker.raw
* ~/Library/Application Support/Developer/coresimulator
* ~/Library/Application Support/Developer/Xcode/iOS DeviceSupport
* ~/Library/Application Support/Developer/Xcode/watchOS DeviceSupport

## Homebrew Packages

Get list of top level packages with `$ brew leaves`

* apr-util 
* aspell 
* autoconf 
* awscli 
* carthage 
* cmake 
* composer 
* cputhrottle 
* freetds 
* glib 
* gmp 
* heroku/brew/heroku 
* imagemagick 
* libpq 
* libsass 
* libxslt 
* libzip 
* lynx 
* mcrypt 
* pkg-config 
* python@3.9 
* smartmontools 
* unixodbc 
* webp 
* yajl
* yarn

## Launchd services

List non-Apple services: `$ launchctl list | grep -v com.apple`  
\(`-v` inverts the grep match\)

[Remove service](https://osxdaily.com/2011/03/08/remove-an-agent-from-launchd/): `$ launchctl remove NameHere`

[More info about launchd](https://www.launchd.info) from the maker of [LaunchControl](https://www.soma-zone.com/LaunchControl/).

## Preventing a Mac From Waking Up Randomly

In Settings / Notifications / Do Not Disturb: Check the box to turn on Do Not Disturb when the Display is Sleeping \(I also have it set to turn on DND from 10pm to 7am, when the screen is locked, and when mirroring\)

Unconfirmed ideas:

In Settings / Battery / Power Adapter disable Wake for Network Access

In Settings / Bluetooth / Advanced disable Allow Bluetooth Devices to Wake This Computer

In Settings / Battery / Power Adapter turn off Sleep When Display is Off

## References

* [https://github.com/nikitavoloboev/my-mac-os](https://github.com/nikitavoloboev/my-mac-os)
* [https://github.com/serhii-londar/open-source-mac-os-apps](https://github.com/serhii-londar/open-source-mac-os-apps)
* [https://github.com/learn-anything/macos-apps](https://github.com/learn-anything/macos-apps)
* [https://github.com/jaywcjlove/awesome-mac](https://github.com/jaywcjlove/awesome-mac)





