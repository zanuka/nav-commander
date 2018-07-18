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

### Create mount directory
    sudo mkdir /mnt/usbstorage

### Make Pi the owner of new directory
    sudo chown -R pi:pi /mnt/usbstorage
    sudo chmod -R 775 /mnt/usbstorage

### Set all future permissions for mount point to pi user
    sudo setfacl -Rdm g:pi:rwx /mnt/usbstorage
    sudo setfacl -Rm g:pi:rwx /mnt/usbstorage

### Mount the USB
    sudo mount -t uid=pi,gid=pi /dev/sda1 /mnt/usbstorage

### Ensure USB auto mounts on system boot

    sudo nano /etc/fstab

When file is opened in nano, add the following line:

    /dev/sda1    /mnt/usbstorage    ext4   nofail    0   0

_Note: the 'nofail' mount option tells Raspbian to ignore this entry if the USB drive is not plugged in_

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close nano

## Configure Raspbian to use swap, set swap size

    sudo nano /etc/dphys-swapfile

**Set path to new swap:**

    CONF_SWAPFILE=/dev/sda1

**Set new swap size:**

    CONF_SWAPSIZE=1024

ctrl + O to `WriteOut` the file, then press Enter, then ctrl + X to close nano

### Activate the new swap
    sudo /etc/init.d/dphys-swapfile restart

    Output
    [ok] Restarting dphys-swapfile (via systemctl): dyphys-swapfile.service.

### Verify memory and new swap
    free -m

### Reboot your NavPi
    sudo reboot

### Verify new swap
    cat /proc/swaps

    Output
    Filename      Type         Size      Used      Priority
    /var/swap     file         102396    1124      -1
    /dev/sda1     partition    7861756   0         -2

### Check current memory usage

There are several options for checking memory use.

Built-in commands include:

    free -h
    top

htop is also an option:

    sudo apt-get install htop
    htop
