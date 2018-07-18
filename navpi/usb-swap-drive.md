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
Your USB drive has mosty likely come preformatted as FAT, however you'll get far more speed by using EXT4. FAT can be understood by Linux file system but is not native.

    sudo mkfs.ext4 /dev/sda1

### Create mount directory
    sudo mkdir /usbdrive

### Mount the USB
    sudo mount /dev/sda1 /usbdrive

### Ensure USB mounts on system boot
    sudo nano /etc/fstab

When file is opened in nano, add the following line:
    /dev/sda1 /usbdrive ext4 defaults,nofail 0 1

_Note: the 'nofail' mount option tells Raspbian to ignore this entry if the USB drive is not plugged in_

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close Nano

### Make sure drive is not mounted
    sudo umount /dev/sda1

### Create the swap
    sudo mkswap /dev/sda1

    Output
    Setting up swapspace version 1, size = 7861756 KiB
    no label, UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX

### Enable the swap
    sudo swapon -a

### Verify new swap
    cat /proc/swaps

    Output
    Filename      Type         Size      Used      Priority
    /var/swap     file         102396    1124      -1
    /dev/sda1     partition    7861756   0         -2

If successful, you should see details about your new swap in the Output

## Configure Raspbian to use swap, set swap size

    sudo nano /etc/dphys-swapfile

**Set path to new swap:**
    CONF_SWAPFILE=/dev/sda1

**Set new swap size:**
    CONF_SWAPSIZE=1024

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close Nano

### Reboot your NavPi
    sudo reboot

### Check current memory usage

There are several options for checking memory use.

Built-in commands include:

    free -h
    top

htop is also an option:

    sudo apt-get install htop
    htop
