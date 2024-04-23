-----------------------------------------------------
#===================  efibootmgr  =================== 
-----------------------------------------------------
    **Configure, examine and modify UEFI variables**
[`efibootmgr -v`](shows summary of the boot configuration)
[`efibootmgr -o 0004,0002`](specifying the options Boot0004 and Boot0002)
-----------------------------------------------------
#===================  systemctl  ==================== 
-----------------------------------------------------
**all-purpose command for investigating the status of** 
  **systemd and making changes to its configuration**
[`systemctl list-units --type=service`](show only loaded and active services)
[`systemctl list-unit-files --type=service`](show all the installed unit file)
[`systemctl isolate multi-user.target`](change the system’s current operating mode)
[`systemctl get-default`](To see the target the system boots into by default)
[`systemctl set-default multi-user.target`](To set the target the system boots into by default)
[`systemctl add-wants multi-user.target my.local.service`](adds a dependency on my.local.service to the standard multiuser target)
[`systemctl list-timers`](list all the defined timers)
[`systemd-run --on-calendar 'TIME' [COMMAND]`]**transient timer**(schedule the execution of a COMMAND on TIME without creating timer or service unit files)
-----------------------------------------------------
#===================  journalctl  =================== 
-----------------------------------------------------
    **Control and shows systemd journal logs**
[`journalctl -u ssh`](shows journal logs from the SSH Unit)
[`journalctl -f `](Print new messages as they arrive.)
[`journalctl --setup-keys`](generate the key pair Used in Log MSGs Inegrity)
[`journalctl --disk-usage`](shows the size of the journal on disk)
[`journalctl --list-boots`](shows a sequential list of system boots)
[`journalctl -b 0`](restrict the log display to a particular boot session.)
[`journalctl --since=yesterday --until=now`]( show all the messages from yesterday at midnight until now)
[`journalctl -n 100 /usr/sbin/sshd`](show the most recent 100 journal entries from a specific binary)
[`sudo kill -HUP [syslogd.PID]`](causes rsyslogd to close all open log files {rotating} by renaming and restarting logs)
[`logger -t auth -p info "MSG"`](Add log of auth.info messages to the system log for DEBUG)
[`journalctl --dmesg`](prints messages of kernel outputs from booting and during running)
[`dmesg -w`](linux version that monitor the kernel message buffer in real-time)
-----------------------------------------------------
#==============  User Configuration  ================ 
----------------------------------------------------- 
[`chfn USERNAME`](change users GECOS [F.Name,Phone,et.] information)
[`chage -m 2 -M 90 -E 2017-07-31 -W 14 USERNAME`](sets the minimum number of days between password changes to 2,
                                                  sets the maximum number to 90, 
                                                  sets the expiration date to July 31, 2017, and 
                                                  warns the user for 14 days that the expiration date is approaching)
[`useradd -c "COMMENT" -d HOME_DIR -G [GROUP1,GROUP2..] -m -s [SHELL] USER`](create user with home_dir "m" option)
[`adduser USERNAME`](higher-level SCript that provides an interactive interface for adding new users)(*)
[`userdel -r USER`](remove USER wiht Files in the user's home directory)
[`passwd -l USER`](Disabling the USER account)
[`usermod -L USER`](Lock USER by put ! in passwd to makes logins fail)
[`usermod -U USER`](unLock USER by remove ! in passwd to makes logins succeed)
[`sudo hostnamectl set-hostname HOSTNAME`](apply new HOSTNAME After changing /etc/hosts)
[`id USERNAME`](print uid, gid and groups of USERNAME)
-----------------------------------------------------
#===============  Proccess Control  ================= 
-----------------------------------------------------
[`kill [-signal] pid`](send signal to proccess, but by default it sends a TERM)
[`killall [NAME]`](kills processes by name)
[`pgrep -u root [NAME}`](list the processes's IDs called sshd AND owned by root)
[`pkill [-signal] [NAME]`](Send signal for processes Searched by name or other attributes)
[`pidof [NAME]`](Determine the PID of a process)
[`ps aux`](list all proccess in user format with/out terminal)
[`nice -n [-20:19] [PROCESS]`](Lowers priority [raise nice] by 5)
[`renice -u [USER] -5 PID`](Sets niceness of USER’s procs to -5)
[`strace -p PID`](Display every system call that a process makes and every signal it receives)
[`lsof [BINARY]`](list open files belonging to processe)
-----------------------------------------------------
#==================  Filesystems ==================== 
-----------------------------------------------------
[`file [FILENAME]`](determine the type of an existing FILENAME)
[`chmod -R g+w /PATH`](adds group write permission to /PATH all its contents[Recursively])
[`chown -R USER:GROUP /DIR`](change both the owner and group of a DIR Recursively)
[`chgrp -R GROUP /FILE`](change the group of a File)
[`getfacl FILE`](display The ACL view of file mode)
[`setfacl FILE`](set ACL of file mode)
[`setfacl -m user::r,user:USER:rw,group:GROUP:rw FILE`](modify ACL of File)
[`setfacl -b FILE`](Remove an ACL entirely and revert to the standard UNIX permission system)
[`setfacl -dm FILE`](set default ACL entries to propagat the ACLs to sub-dir and files)
-----------------------------------------------------
#================  Device Managment ================= 
-----------------------------------------------------
[`mknod DEVICE_name type major minor`](create device file of type 'c' or 'b' and major:minor)
[`udevadm info -a -n sdb`](retrieve all available attributes information about sdb)
-----------------------------------------------------
#==============  Networking Managment =============== 
-----------------------------------------------------
[`ip neigh show`](prints, flushes, adds or deletes entries of ARP or NDP table)
[`ip route add Network/CIDR via ADDRESS dev DEVICE`](add route ipv4 to table)
[`netstat -rn`](list all routes with numeric instead hostnames)
[`ip route -6 add Network/CIDR via ADDRESS dev DEVICE`](add route ipv6 to table)
[`ip route flush`](initialize the routing table and start over)
[`ip route del Network/CIDR`](remove route from table)
[`ip link show`](list all the network interfaces)
[`ethtool -s eth0 speed 100 duplex full`](set eth0 interface to 100 Mb/s full duplex)
[`ethtool -K I  NET`](shows what protocol-related tasks are assigned to ethernet network interface)
[`ping -n IP`](ping using ip only not Domain names "DNS not work!")
[`ping -s 1500 DEST`](send icmp packet of 1500 bytes "check media error!")
-----------------------------------------------------
#================  Firewall and NAT ================= 
-----------------------------------------------------
[`iptables -F`](flush OUTPUT, INPUT and FORWARD chains)
[`iptables -L -v`](how many times each rule in your chains has matched a packet)
[`iptables -P INPUT DROP`](set Policy to Chain)
[`iptables -A INPUT -d IP -p tcp --dport 80 -j ACCEPT`](append rule to accept http sent to IP)
[`iptables -A INPUT -i INET -d IP -p ANY -j ACCEPT`](append to interface with any protocol)
[`iptables -A FORWARD -d IP -p icmp --icmp-type 0 -j ACCEPT`](accept/reject certain types of ICMP)
[`iptables -A INPUT -i INET -j LOG`](forbids all packets not explicitly permitted)
[`iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT`](match state of connection if true then accept)
[`iptables -t nat -A POSTROUTING -o Private_INET -j SNAT --to PUBLIC_IP`](set NAT of INET)
-----------------------------------------------------
#==============  Domain Name Service ================ 
-----------------------------------------------------
[`dig @a.root-servers.net DOMAIN soa`](query root servers for SOA of DOMAIN)
[`dig @a.gtld-servers.net DOMAIN soa`](query globale top-level servers for SOA of DOMAIN)
[`dig @ns1.google.com DOMAIN any`](query nameserver for any record of DOMAIN)
-----------------------------------------------------
#==============  POSTFIX Mail Agent ================= 
-----------------------------------------------------
[`postconf`](prints all parameters currently configured)
[`postconf -d`](prints all Default parameters)
[`postconf -n`](prints parameters differ from the default)
[`postconf PARAM=VALUE`](set parameters of Postfix) 
[`postconf -m`](Information sources for Postfix lookup tables)
[`postmap hash:/PATH`](compile Text filesto their binary formats)
[`postmap -q ALIAS TYPE:/PATH`](query values in a lookup table)
-----------------------------------------------------
#==============  Storage Management ================= 
-----------------------------------------------------
[`lsblk`](list all block devices attached)
[`fdisk /DEV`](Partioning Tool MBR-GPT-DOS)
[`df -h`](shows filesystem disk use in human-readable units)
[`du [FILEs]`](Summarize disk usage of the set of FILEs)
[`mkfs -t ext4 -L LABEL /DEV`](make FS of ext4 type on /DEV)
[`mkfs.btrfs -L demo -d raid1 /dev/sdb /dev/sdc`](create RAID-1 Solution using BTrfs)
[`mount LABEL=spare /dev/{DEV} /PATH`](mount FS stored on {DEV} under the path {PATH})
[`umount -f`](force-unmounts a busy FS even not all files closed)
[`umount -l`](removes a busy FS from the naming hierarchy after closing all files)
[`sg_format /DEV`](format Command TO SAS Disks)
[`hdparm --user-master u --security-set-pass PASSWORD /DEV`](set password on a drive before Secure Erase)
[`hdparm --user-master u --security-erase PASSWORD /DEV`](Secure Erase of ATA Drives Disks)
[`hdparm -I /DEV`](Display drive identification and all information about it)
#---------------- Logical Volume Management ---------
[`pvcreate /DEV`](label the DEV as an LVM physical volume)
[`vgcreate DEMO /DEV`](add DEV to a volume group DEMO)
[`vgdisplay DEMO`](display Volume group DEMO)
[`lvcreate -L 4G -n web1 DEMO`](create logical volume of size 4G from DEMO VG)
[`lvcreate -L 2G -s -n web1-snap DEMO/web1`](create snapshot of /dev/DEMO/web1)
[`lvchange -an DEMO/web1`](De-Activate the volume "unmount it")
[`lvresize -L +3G DEMO/web1`](Add 3G to Web1 LV "Add more giga to disk")
[`lvchange -ay DEMO/web1`](De-Activate the volume "mount it")
[`resize2fs /dev/DEMO/web1`](resize FS of web1 "resize FS with new size")
#---------------- Zetta-byte FS management ---------
[`zpool create demo /DEV`](creates the pool “demo” FS of DEV and mounts as /demo)
[`zpool create demo raidz1 /DEV1 /DEV2`](create RAID single parity solution)
[`zpool add demo mirror /DEV3 /DEV5`](Add DEVs to pool RAID solution as mirroring)
[`zpool list`](list all zpool on device)
[`zpool status demo`](more details about the virtual devices that make up a pool)
[`zfs create demo/new_fs`](create new_fs under demo/)
[`zfs create -V 128m demo/swap`](create raw vloume of 128m "like hard disk or partition")
[`ls /dev/zvol`](contain not-monunted raw volumes)
[`zfs list -r demo`](list zfs filesystems recursively)
[`zfs set quota=1g demo/new_fs`](set quota on ZFS fs "AVAIL")
[`zfs set reservation=1g demo/new_fs`](set quota on ZFS fs "USED")
[`zfs get all demo`](dump all properties of ZFS "local, inherited, -")
[`zfs snapshot -r demo/new_fs@snap1`](create snapshot of ZFS recursively)
[`ls /mnt/demo/new_fs/.zfs/snapshot/snap1`](direction of snpashots "snapshotes're Read-only")
[`zfs rollback demo/new_fs@snap1`](restore snapshot)
[`zfs clone demo/new_fs@snap1 demo/subclone`](create a full-fledged snapshot "writable filesystem")
[`zfs destroy demo/new_fs`](remove ZFS)
-----------------------------------------------------
#==============  Network File System  =============== 
-----------------------------------------------------
[`exportfs -a`](convert /etc/exports to xtab for server)
[`systemctl restart nfs-server.service`](to enable nfsd configuration changes)
[`exportfs -v`](shows the existing exports for V4)
[`showmount -e HOSTNAME`](verify which server's filesystems has exported for V3)
-----------------------------------------------------
#================  Docker Management  =============== 
-----------------------------------------------------
[`docker info`](Displays summary information about the daemon)
[`docker pull IMAGE:TAG`](Downloads images from a remote registry)
[`docker pull REGISTRY/IMAGE:TAG`](Downloads images from REGISTRY "Not Docker hub")
[`docker push`](uploads images to a remote registry)
[`docker build -t NAME:TAG /DIR`](create image with NAME and TAG with files on /DIR)
[`docker images`](Displays local images)
[`docker rm CONTAINER_ID`](Removes a container)
[`docker rmi IMAGE_ID`](Removes an image)
[`docker inspect CONTAINER_ID`](Displays the configuration of a container)
[`docker inspect -f '{{ json .KEY }}' CONTAINER_ID`](filter Config on KEY)
#---------------- Running Containers ---------
[`docker run IMAGE_ID`]( Runs a new container)
[`docker run -it`](Runs a new container with Interactive Terminal)
[`docker run -d IMAGE_ID`](Runs a new container in the background "Daemon")
[`docker run -p HOST_PORT:CONTAINER_PORT`](Runs a new container with Port tunneling)
[`docker run --rm`](run and auto removes when it exits "Not work with -d")
[`docker run -v /data`](add a volume to a container on /data "inside Container")
[`docker run -v /mnt/data:/data`](bind-mount /mnt/data from the host to /data in the container)
[`docker run --volumes-from VOLUME_ID`](use VOLUME_ID in container "data-only")
[`docker run --network NAME`](select container network Name) 
[`docker run --logging-driver DRIVER`](select OUTPUT log-driver "json-file,awslogs,journald...") 
[`docker run --read-only`](limiting the container to a read-only root filesystem)
[`docker run --cap-add NET_RAW SETUID IMAGE_ID`](add linux capabilities to container)
[`docker run --cap-drop SETUID IMAGE_ID`](remove linux capabilities from container)
#---------------- Manage Containers ---------
[`docker create -v /mnt/data:/data --name VOLUME_ID IMAGE_ID`](Create a data container "Data-only")
[`docker exec nginx bash`](Executes a new process in an existing container)
[`docker ps`](Displays running containers)
[`docker ps -a`](Displays history of running containers)
[`docker top`](Displays containerized process status "inside Container")
[`docker start`](Starts an existing container)
[`docker stop`](stops an existing container)
[`docker logs CONTAINER_ID`](Displays the standard output from a container)
[`docker logs -f CONTAINER_ID`](get a real-time stream of a container’s output)
[`docker network ls`](Displays networking options)
[`docker volume ls`](Displays Volumes)
#---------------- Secure Containers ---------
[`docker --tlsverify`](Require authentication)
[`docker --tlscert PATH`](Path to a signed certificate "default location ~/.docker/{cert}.pem")
[`docker --tlskey PATH`](Path to a private key "default location ~/.docker/{key}.pem")
[`docker --tlscacert PATH`](Path to the certificate of a trusted authority "default location ~/.docker/{ca}.pem")
-----------------------------------------------------
#===============  Jenkins Management  =============== 
-----------------------------------------------------
[``]()
-----------------------------------------------------
#=================  TIME Management  ================ 
-----------------------------------------------------
[`sudo timedatectl set-time "YYYY-MM-DD HH:MM:SS"`](Set the time manually)
[`sudo timedatectl set-ntp true`](Set the time using NTP)
[`sudo timedatectl set-timezone Africa/Cairo`](adjust the timezone)
-----------------------------------------------------
#===================  Security  ===================== 
-----------------------------------------------------
#---------------- Openssl ---------
[`openssl genrsa -out admin.com.key 2048`](creating a 2048-bit private key)
[`openssl req -new -sha256 -key KEY -out admin.com.csr`](create a certificate signing request)
[`openssl enc -aes-192-gcm -in INPUT -out OUT.enc`](Encrypting with AES-192 GCM)
[`openssl -d -aes-192-gcm -in INPUT.enc -out OUT`](Decrypting with AES-192 GCM)
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()
[``]()

