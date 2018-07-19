# Creating swap on USB drive
In this example we are using an 8GB USB drive

### Insert drive
Connect your USB drive to the NavPi

### List drives connected to your NavPi
    sudo fdisk -l

    Output
    Device     Boot    Start     End   Sectors     Size    Id    Type
    /dev/sda1           8192    93596   85405      41.7M   c     W95 FAT32 (LBA)

Make note of the disk that represents your USB drive, which in this example is `dev/sda1`

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

## Configure Raspbian to use swap, set swap size

    sudo nano /etc/dphys-swapfile

**Set path to new swap:**

    CONF_SWAPFILE=/navswap/swap

**Set new swap size:**

    CONF_SWAPSIZE=2048

_In this example we'll go for a 2GB swap_

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close nano

### Recreate swap and turn it on
    sudo dphys-swapfile setup
    sudo dphys-swapfile swapon

    Output
    [ok] Restarting dphys-swapfile (via systemctl): dyphys-swapfile.service.

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
