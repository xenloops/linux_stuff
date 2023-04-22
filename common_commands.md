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

### Temporarily; for current session
```
export PATH="/directory/to/add/:$PATH"
```
Be sure to include the $ for $PATH, otherwise you'll lose other important path info.

### Permanently; or at least until you change it again

Once you've tested it for the session, you can make it permanent:
Edit ~/.bashrc in your favorite torturous text editor. At the _bottom_ of the file, add:

```
export PATH="/path/to/add/:$PATH"
```

To load the change immediately, run:
```
source ~/.bashrc
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

