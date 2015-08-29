
### Layout

This device (WD Passport 1TB 07A8) is dedicated to my first desktop
portable environment. Table partitions:

    fdisk -l /dev/sdX

    Disk /dev/sdX: 1000.2 GB, 1000170586112 bytes
    255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00062517
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/sdX1   *        2048    48828415    24413184   83  Linux
    /dev/sdX2        58599424  1830578175   885989376   83  Linux
    /dev/sdX3        48828416    58593279     4882432   82  Linux swap / Solaris
    /dev/sdX4      1830580222  1953457818    61438798+   5  Extended
    /dev/sdX5      1830580224  1892020223    30720000   83  Linux
    /dev/sdX6      1892022272  1953457818    30717773+  83  Linux 

First partition is for /boot (label=portable-system), the second for
data (label=portable-data) and third and last partition is dedicated
for swap (label=portable-swap).

Partition five is for Debian.

Partition six is for Ubuntu LTS Xen.


Partitions labels may be changed with `gparted`.


	lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT
	
	NAME   FSTYPE   SIZE MOUNTPOINT
	
	sdX           931.5G 
	├─sdX1         23.3G /media/user/portable-system
	├─sdX2          845G /media/user/portable-data
	├─sdX3          4.7G [SWAP]
	├─sdX4            1K 
	├─sdX5         29.3G /media/user/Debian-8
	└─sdX6         29.3G /media/user/Ubuntu-LTS-Xen

