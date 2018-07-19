# Configuring NavPi to use a USB drive for swap disk
If you are interested in using a USB drive as a swap disc, this guide should get you sorted. Any size drive could be used, but for this guide I'm using an 8GB USB drive I bought for $13. The drive is pre-formatted FAT32.

### Insert drive
Connect USB drive to the NavPi

### List drives connected to your NavPi
    sudo blkid

    Output
    Device     Boot    Start     End   Sectors     Size    Id    Type
    ...
    /dev/mmcb1k0p1: LABEL="boot" UUID="XXXX-XXXX" TYPE="vfat" PARTUUID="db06311d-01"
    /dev/sda1: LABEL="UNTITLED" UUID="XXXX-XXXX" TYPE="vfat" PARTUUID="a9be7089-10"

You should see four entries, with the last one being your USB drive - `dev/sda1`

### Format drive to EXT4
Your USB drive has mosty likely come preformatted as FAT, however you'll get far more speed and reliability by using EXT4. FAT can be understood by Linux file system but is not native.

**First unmount the USB**

    sudo umount /dev/sda1

**Now reformat to ext4**

    sudo mkfs.ext4 /dev/sda1

    Output
    Writing superblocks and filesystem accounting information: done

### Create mount directory
    sudo mkdir /navswap

### Ensure USB auto mounts on system boot

    sudo nano /etc/fstab

When file is opened in nano, add the following line:

    /dev/sda1    /navswap    ext4   nofail    0   0

_Note: the 'nofail' mount option tells Raspbian to ignore this entry if the USB drive is not plugged in_

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close nano

### Set swap location and size

    sudo nano /etc/dphys-swapfile

**Set path to new swap:**

    CONF_SWAPFILE=/navswap/swap

**Set new swap size:**

    CONF_SWAPSIZE=2048

_In this example we'll go for a 2GB swap_

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close nano

### Recreate and activate swap
    sudo dphys-swapfile setup
    sudo dphys-swapfile swapon

    Output
    [ok] Restarting dphys-swapfile (via systemctl): dyphys-swapfile.service.

_Note: this might take awhile_

### Verify memory and new swap
    free -m

### Reboot your NavPi
    sudo reboot

### Verify new swap
    cat /proc/swaps

    Output
    Filename         Type         Size      Used      Priority
    /navswap/swap    file         2097418   0         -1

### Check memory usage with swap in place

There are several options for checking memory use.

Built-in commands include:

    free -h
    top

**pro tip - install htop** - a nice option for monitoring interactively. It's a nice way to filter on running processes, like 'nav'. It combines the functionality of top and iotop into a single screen.

    sudo apt-get install htop
    htop

You should now see the swap drive being monitored.

### Enjoy stability
