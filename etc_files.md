#---------------------------------------------------------------------
#-----------------------  Booting and System   -----------------------
#---------------------------------------------------------------------
[1](/usr/lib/systemd/system) --> **contain packages's unit files**
[2](/etc/sysctl.conf) --> **Configuration file for setting system variables permanent**
#---------------------------------------------------------------------
#----------------  Access Control and Rootly Powers   ----------------
#---------------------------------------------------------------------
[1](/etc/sudoers) --> **lists authorized people to use sudo and commands they are allowed to run on each host**
[2](/etc/apparmor.d) --> **contain AppArmor profiles**
[](/etc/hosts.allow) --> **list of hosts that are allowed to access the system**
[](/etc/hosts.deny) --> **list of hosts that are _not_ allowed to access the system**


#---------------------------------------------------------------------
#---------------------  Logging and Syslog   -------------------------
#---------------------------------------------------------------------
[1](/etc/systemd/journald.conf) --> **The default Systemd journal configuration file**
[2](/etc/rsyslog.conf) --> **The default rsyslog configuration file**
[3](/var/log/syslog) --> **The file contain Syslog log got from journald**
#---------------------------------------------------------------------
#---------------------   Periodic processes   ------------------------
#---------------------------------------------------------------------
[1](/etc/crontab) --> **Cron Configuration File for system administrators to maintain by hand**
[2](/etc/crontab.d/) --> **Cron Configurations Directory where software packages install any crontab**
[3](/etc/cron.{allow,deny}) --> **list of all users that may/not submit crontabs, one per line**
[4](/var/spool/cron/) --> **Contain Crontab for each User**
[5](/var/log/cron) --> **lists the commands that were executed by cron**
#---------------------------------------------------------------------
#----------------------   User Managment   ---------------------------
#---------------------------------------------------------------------
[1](/etc/passwd) --> **list of users recognized by the system**
[2](/etc/shadow) --> **contain all users's Passwords**
[3](/etc/group) --> **contain all group's Data**
[4](/etc/adduser.conf) --> **Default values of new user added**
[5](/etc/login.defs) --> **Configuration control definitions for the login package**
[6](/etc/profile) --> **system-wide ~/.profile file**
[7](~/.bashrc) --> **Sets the terminal type**
[8](~/.bash_profile) --> **Sets up environment variables, command aliases, search path**
[9](~/gitconfig) --> **Sets user, editor, color, and alias options for Git**
#---------------------------------------------------------------------
#----------------   Userspace Device Management   --------------------
#---------------------------------------------------------------------
[](/lib/udev/rules.d) --> **Default rules of udev**
[](/etc/udev/rules.d) --> **Local rules of udev**
[](/etc/udev/udev.conf) --> **The master configuration file of udev**
[](/etc/udev/) --> ** **
[](/usr/lib/udev/) --> ** **
#---------------------------------------------------------------------
#------------------   Networking Management   ------------------------
#---------------------------------------------------------------------
[1](/etc/dhcp/) --> **all dhcp server and client data**
[2](/etc/bind/named.conf) --> **configuration file for the BIND DNS server named**
[3](/etc/hostname) --> **my Host name**
[4](/etc/hosts) --> **contain all hosts DNS Cache**
[5](/etc/networks) --> **maps networs to names**
[6](/etc/resolv.conf) --> **DNS Configurations**
[7](/proc/sys/net/ipv4:6/) --> **all TCP, UDP, ICMP parameters**
[8](/proc/sys/net/ipv4:6/conf) --> **parameters of interface**
[9](/proc/sys/net/ipv4:6/neigh) --> **arp table parameters for each interface**
[10](/etc/sysctl.conf) --> **configurations read by the sysctl command at boot time**
#---------------------------------------------------------------------
#--------------------   Single Sign On    ----------------------------
#---------------------------------------------------------------------
[1](/etc/pam.d/) --> **directory of all Pluggable Authentication Modules Data**
[2](/etc/sssd/sssd.conf) --> **configuration file of SSSD**
#---------------------------------------------------------------------
#-------------------   Electronic Mail    ----------------------------
#---------------------------------------------------------------------
[](/etc/mail/aliases) --> **system-wide mail aliases configuration**
[](~/.forward) --> **each-user mail aliases configuration**
[](/etc/[postfix:exim4]/) --> **main Confugrations of Agent**
[](/var/spool/[postfix:exim4]/) --> **Related Confugration of Agent**
#---------------------------------------------------------------------
#-------------------  POSTFIX Mail Agent   ---------------------------
#---------------------------------------------------------------------
[](/etc/postfix/main.cf) --> **Postfix’s principal configuration file** 
[](/etc/postfix/master.cf) --> **configures the server programs** 
[](/etc/postfix/) --> ** ** 
[](/etc/postfix/) --> ** ** 
#---------------------------------------------------------------------
#------------------   Storage Management    --------------------------
#---------------------------------------------------------------------
[](/etc/fstab) --> **static file system information (automatic mount partition at boot time)**
[](/dev/disk/by-[TYPE]) --> **list disks by various stable characteristics**
[](/etc/exports) --> **the root of the exported filesystem in NFS**
[]() --> ****
[]() --> ****
#---------------------------------------------------------------------
#------------------   Docker Management    --------------------------
#---------------------------------------------------------------------
[](/var/lib/docker/) --> **directory where containers and images stored**
[](/etc/default/docker) --> **Docker Daemon Configuration Options**
[]() --> ****

















