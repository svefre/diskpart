# Diskpart

> A built-in Windows tool to manage drives, disks, volumes and virtual disks

I use it to delete all partitions on a USB stick (usually after distro hopping) when no linux machine is near by.

## Launch

* Press `Windows + R` and enter `diskpart` (allow admin previleges)

## Disks

```bash
DISKPART> list disk
  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          476 GB  1024 KB        *
  Disk 2    Online         7450 MB  2240 MB

DISKPART> select disk 2
  Disk 2 is now the selected disk.

# The *clean* command will finish quickly since
# it only marks the data on the disk as deleted.
#
# The *clean all* command will take about an hour
# per 320 GB to finish running since it performs
# a secure erase.
DISKPART> clean
  DiskPart succeeded in cleaning the disk.

DISKPART> create partition primary
  DiskPart succeeded in creating the specified partition.

DISKPART> list partition
  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
* Partition 1    Primary           7449 MB  1024 KB

DISKPART> active
  DiskPart marked the current partition as active.

DISKPART> select partition 1
  Partition 1 is now the selected partition.

DISKPART> format fs=fat32 quick
  100 percent completed

  DiskPart successfully formatted the volume.

DISKPART> exit
```
