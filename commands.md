# Common useful Linux commands 
Debian variant

## Enable sudo for a user
```
su -
[enter root password]
usermod -a -G sudo [username]
```
## Update the system
Always do this after installing Linux, and once or twice a week
```
sudo apt update; sudo apt upgrade -y
```
## Install .deb packages not in the repositories
Make sure you can trust the source of the package!
```
cd [directory of file]
sudo apt install ./[filename]
```
