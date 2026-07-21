
```
 echo 'Acquire::http { Proxy "http://<your-apt-cache-server-ip-address>:3142"; }' \
     | sudo tee -a /etc/apt/apt.conf.d/99proxy
```
