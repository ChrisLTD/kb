# Shell \(Linux\)

## Shell Cheat Sheet

### File & Folder Operations

Delete a directory:`rm -r directory`

Delete file:`rm FILETODELETE`

New directory:`mkdir FOLDERNAME`

Copy file:`cp SOURCE DEST`

Copy folder:`cp -avr SOURCE DEST`

Watch file:`less +F YOUR.LOG`

Move/Rename folder:`mv OLD NEW`

### CURL

Download file:`curl -O URLHERE`

### Zipping & Uzipping

Unzip:`unzip FILENAME.ZIP`

Untar & Gzip:`tar -xzf FILENAME.TAR.GZ`

Zip folder:`zip -er DESTINATION.ZIP FOLDER`

### Processes

Kill process:`kill -9 PROCESSID`

Find process:`ps -ef | grep PROCESS NAME`

Process list:`ps aux`

Root process list:`ps -u root`

Check memory usage in megabytes:`free -m`

List of ports in use: `sudo lsof -i -P -n`

### Permissions

Set all new files and folders to[ inherit the group of the current folder](https://unix.stackexchange.com/a/401751): `$ chmod -R g+s somefolder`

