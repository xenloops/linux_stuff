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

