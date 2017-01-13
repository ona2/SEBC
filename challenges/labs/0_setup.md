```
domain:
us-west-2.compute.internal

ami:
ami-09f7d239

os:
[root@ip-172-30-2-98 ~]# uname -rms
Linux 2.6.32-431.11.2.el6.x86_64 x86_64

instances:
m3.2xlarge




nodes:

35.166.205.213  node1	172.30.2.251	ip-172-30-2-251	
35.167.242.86   node2	172.30.2.23	ip-172-30-2-23		
35.167.167.1    node3	172.30.2.225	ip-172-30-2-225
35.167.229.55   node4	172.30.2.43	ip-172-30-2-43
35.167.74.24	node5	172.30.2.98	ip-172-30-2-98

volume:

node1:
[root@ip-172-30-2-251 ~]# lsblk
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   15G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 14.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.7G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  816M  0 lvm  [SWAP]
xvdc                        202:32   0   60G  0 disk 
xvdb                        202:16   0   60G  0 disk 


[root@ip-172-30-2-251 ~]# df -hT
Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                     ext4    14G  1.3G   12G  10% /
tmpfs                tmpfs   15G     0   15G   0% /dev/shm
/dev/xvda1           ext4   485M   54M  407M  12% /boot


node2:
[root@ip-172-30-2-23 ~]# lsblk
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   15G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 14.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.7G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  816M  0 lvm  [SWAP]
xvdc                        202:32   0   60G  0 disk 
xvdb                        202:16   0   60G  0 disk 


[root@ip-172-30-2-23 ~]# df -hT
Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                     ext4    14G  1.3G   12G  10% /
tmpfs                tmpfs   15G     0   15G   0% /dev/shm
/dev/xvda1           ext4   485M   54M  407M  12% /boot

node3:
[root@ip-172-30-2-225 ~]# lsblk
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   15G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 14.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.7G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  816M  0 lvm  [SWAP]
xvdc                        202:32   0   60G  0 disk 
xvdb                        202:16   0   60G  0 disk 

[root@ip-172-30-2-225 ~]# df -hT
Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                     ext4    14G  1.3G   12G  10% /
tmpfs                tmpfs   15G     0   15G   0% /dev/shm
/dev/xvda1           ext4   485M   54M  407M  12% /boot


node4:
[root@ip-172-30-2-43 ~]# lsblk
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   15G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 14.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.7G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  816M  0 lvm  [SWAP]
xvdc                        202:32   0   60G  0 disk 
xvdb                        202:16   0   60G  0 disk 

[root@ip-172-30-2-43 ~]# df -hT
Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                     ext4    14G  1.3G   12G  10% /
tmpfs                tmpfs   15G     0   15G   0% /dev/shm
/dev/xvda1           ext4   485M   54M  407M  12% /boot


node5:
[root@ip-172-30-2-98 ~]# lsblk
NAME                        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
xvda                        202:0    0   15G  0 disk 
├─xvda1                     202:1    0  500M  0 part /boot
└─xvda2                     202:2    0 14.5G  0 part 
  ├─VolGroup-lv_root (dm-0) 253:0    0 13.7G  0 lvm  /
  └─VolGroup-lv_swap (dm-1) 253:1    0  816M  0 lvm  [SWAP]
xvdc                        202:32   0   60G  0 disk 
xvdb                        202:16   0   60G  0 disk 

[root@ip-172-30-2-98 ~]# df -hT
Filesystem           Type   Size  Used Avail Use% Mounted on
/dev/mapper/VolGroup-lv_root
                     ext4    14G  1.3G   12G  10% /
tmpfs                tmpfs   15G     0   15G   0% /dev/shm
/dev/xvda1           ext4   485M   54M  407M  12% /boot


repos:
[root@ip-172-30-2-98 ~]# yum repolist enabled
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: repos.lax.quadranet.com
 * epel: mirrors.cat.pdx.edu
 * extras: mirrors.ocf.berkeley.edu
 * updates: mirror.tocici.com
cloudera-manager                                         |  951 B     00:00     
cloudera-manager/primary                                 | 4.3 kB     00:00     
cloudera-manager                                                            7/7
repo id               repo name                                           status
base                  CentOS-6 - Base                                      6,696
cloudera-manager      Cloudera Manager                                         7
epel                  Extra Packages for Enterprise Linux 6 - x86_64      12,213
extras                CentOS-6 - Extras                                       62
updates               CentOS-6 - Updates                                     772
repolist: 19,750


create users and groups on all nodes:
[root@ip-172-30-2-251 ~]# groupadd hackers
root@ip-172-30-2-251 ~]# groupadd crackers

[root@ip-172-30-2-251 ~]# useradd donald -u 2700
[root@ip-172-30-2-251 ~]# useradd vladimir -u 2800

passwd vladimir
passwd donald

[root@ip-172-30-2-251 ~]# usermod -aG hackers vladimir
[root@ip-172-30-2-251 ~]# usermod -aG crackers donald

[root@ip-172-30-2-251 ~]# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
uucp:x:10:14:uucp:/var/spool/uucp:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
gopher:x:13:30:gopher:/var/gopher:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
vcsa:x:69:69:virtual console memory owner:/dev:/sbin/nologin
saslauth:x:499:76:"Saslauthd user":/var/empty/saslauth:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
cloud-user:x:500:500::/home/cloud-user:/bin/bash
donald:x:2700:2700::/home/donald:/bin/bash
vladimir:x:2800:2800::/home/vladimir:/bin/bash


[root@ip-172-30-2-251 ~]# cat /etc/group
root:x:0:
bin:x:1:bin,daemon
daemon:x:2:bin,daemon
sys:x:3:bin,adm
adm:x:4:adm,daemon
tty:x:5:
disk:x:6:
lp:x:7:daemon
mem:x:8:
kmem:x:9:
wheel:x:10:
mail:x:12:mail,postfix
uucp:x:14:
man:x:15:
games:x:20:
gopher:x:30:
video:x:39:
dip:x:40:
ftp:x:50:
lock:x:54:
audio:x:63:
nobody:x:99:
users:x:100:
floppy:x:19:
vcsa:x:69:
utmp:x:22:
utempter:x:35:
cdrom:x:11:
tape:x:33:
dialout:x:18:
saslauth:x:76:
postdrop:x:90:
postfix:x:89:
fuse:x:499:
sshd:x:74:
cgred:x:498:
cloud-user:x:500:
hackers:x:501:vladimir
crackers:x:502:donald
donald:x:2700:
vladimir:x:2800:




```