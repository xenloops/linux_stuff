# Common useful Linux commands 
Debian variant

## Update the system
Always do this after installing Linux, and once or twice a week
```
sudo apt update; sudo apt upgrade -y
```
## Install .deb packages not in the repositories
Make sure you can trust the source of the package!
```
cd <directory of file>
sudo apt install ./<filename>
```
or
```
sudo apt install -f <filename>
```
## Add directory to PATH
```
export PATH="<directory>:$PATH"
```
## Users and groups

### Enable sudo for a user
```
su -
<enter root password>
usermod -a -G sudo <username>
```
### Create 

User: ```sudo useradd -s /bin/bash -m -c "<Name>" -G<group> <username>```

Group: ```sudo groupadd <group>```

Add user to group: ```sudo usermod -a -G <group> <user>```

### List 

Users: ```getent passwd```

Groups for a user: ```groups <user>```

### Change password

Your own: ```passwd```

Others': ```sudo passwd <user>```

Force password change at next login: ```sudo passwd --expire <user>```

### Delete

User: ```sudo userdel <username>```

Group: ```sudo groupdel <group>```

