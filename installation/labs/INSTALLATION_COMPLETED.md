```
I did arrived by lunch time on Monday, as 1pm was listed as a begginning of Bootcamp in my invitation email.

So, I did CDH installation without copy-pasting details from my screen due to time crunch I had.



==========
1) on all 5 nodes: chage swappiness to 10
I checked all nodes for that in /etc/sysctl.conf
vm.swappiness=10was already there
===========

2) on all 5 nodes: disbale transparent huge pages
echo never > /sys/kernel/mm/transparent_hugepage/defrag

put same in /etc/rc.local
in order these changes survive reboot
==========
3) disable iptables on all nodes
>service iptables status

they all been disabled
========
4) disable SELINUX

===========
5)
install java on CM nodes
============
6)
install and configure MySQL
create all databases for amon, rman, metastore, sentry, nav, navms, oozie, hue
================
7)
install CM REPO


======================
8) install CM9

=======
9) install cluster
================

10)
Cluster is up and running

Complaints: free log space directory warnings
I suppressed these warnings

```