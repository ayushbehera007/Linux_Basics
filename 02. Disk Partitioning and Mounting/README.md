# Disk Partitioning and Mounting in Linux

## Partitioning with `fdisk`

- `sudo fdisk -l` : Lists all the drives in your system.
- `sudo fdisk /dev/sda` : Starts partitioning tool for `/dev/sda`.

### Inside `fdisk`:

| Command | Description |
|---------|-------------|
| `m`     | Show help. |
| `a`     | Toggle a bootable flag. |
| `n`     | Add a new partition (choose `p` for primary, `e` for extended). |
| `g`     | Create a new GPT partition table. |
| `o`     | Create a new DOS/MBR partition table. |
| `t`     | Change a partition type (`L` to list all types). |
| `p`     | Print the current partition table. |
| `w`     | Write the partition table to disk and exit. |
| `q`     | Quit without saving changes. |

**Note:**
- MBR supports up to 4 partitions.
- GPT supports up to 128 partitions.

## Formatting Partitions
- `sudo mkfs.ext4 /dev/sda1` : Format partition `/dev/sda1` with ext4 filesystem.

## Creating a Mount Point and Mounting
- `sudo mkdir /mnt/Ayush` : Create a mount point for `/dev/sda1`
- `sudo mount /dev/sda1 /mnt/Ayush` : Mount partition `/dev/sda1` to `/mnt/Ayush`.

## Viewing Block Devices

- `lsblk` : Lists all block devices.
- `blkid` : Lists block device UUIDs and types.

## Persistent Mount using `/etc/fstab`

Edit the file:
```bash
sudo nano /etc/fstab
```

Example entry:
```fstab
<file system>             <mount point>          <type>     <options>     <dump>      <pass>
UUID=xxxx-xxxx            /mnt/Ayush             ext4       defaults        0            2
```

Replace `UUID=xxxx-xxxx` with the actual UUID found using `blkid`.


## Unmounting
- `sudo umount /mnt/ayush` : Unmounts `/dev/sda1` from `/mnt/ayush`

## Other Tools
- `cfdisk`
