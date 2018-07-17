# NavPi

Dev notes on the [NavPi Stake Box](https://github.com/Encrypt-S/navpi) project

Rough drafts of content, configs, and support docs.

For official documentation, refer to the [NavPi Knowledge Base](https://info.navcoin.org/article-categories/navpi/)

## Focus
- audit current version of NavPi (functionality, setup, support, docs)
- create updated content to enhance stability and support NAV community

## Improving performance

The current NavPi configuration is in need of a performance optimisation.

## Current Approach - R & D

### Expand your SD card

For best results, follow this knowledge base article tutorial to expand your SD card prior to next steps.
(This article is in the works and not publised to site yet)

### Prepare to make swap

These are the consolidated steps from this [guide](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04) on DigitalOcean's site

### Check system for swap info
    sudo swapon --show

### Verify no swap exists
    free -h

### Check available space on hard drive
    df -h

### Create swap file
    sudo fallocate -l 1G /swapfile

### Verify correct amount of space reserved
    ls -lh /swapfile

    Output
    -rw-r--r-- 1 root root 1.0G Apr 25 11:14 /swapfile`

### Make the file only accessible to root
    sudo chmod 600 /swapfile

### Verify permissions change
    ls -lh /swapfile

    Output
    -rw------- 1 root root 1.0G Apr 25 11:14 /swapfile

### Mark file as swap space
    sudo mkswap /swapfile

    Output
    Setting up swapspace version 1, size = 1024 MiB (1073737728 bytes)
    no label. UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX

### Enable swap file
    sudo swapon /swapfile

### Verify that the swap is available
    sudo swapon --show

### Check the output of the free utility
    free -h

    Output
                  total        used        free      shared  buff/cache   available
    Mem:           488M         37M         96M        652K        354M        425M
    Swap:          1.0G          0B        1.0G

The swap has been set up successfully. Operating system will begin to use it as necessary.

### Make the Swap File Permanent
First backup your `/etc/fstab` file

    sudo cp /etc/fstab /etc/fstab.bak

Then add the swap info as follows

    echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

## Tweak your Swap Settings
Configure your NavPi's performance when dealing with swap.

### Configure swappiness
The swappiness parameter configures how often your system swaps data out of RAM to the swap space. This is a value between 0 and 100 that represents a percentage.

    vm.swappiness = 10

    Ouput
    vm.swappiness = 10

This value is sometimes recommended to improve performance when sufficient memory exists in a system, this value *10* could be considered for the performance being expected.

Make this persist on reboot:

    sudo nano /etc/sysctl.conf

Add this at bottom of file:

    vm.swappiness=10

### Adjust the cache pressure
This setting configures how much the system will choose to cache inode and dentry information over other data.

Check the current cache pressure setting:

    cat /proc/sys/vm/vfs_cache_pressure

    Ouput
    100

By default, the system removes inode information from the cache too quickly. 

Set this to a more conservative setting like 50:

    sudo sysctl vm.vfs_cache_pressure=50

    Output
    vm.vfs_cache_pressure = 50

Make it persist:

    sudo nano /etc/sysctl.conf

Add this to bottom of file:

    vm.vfs_cache_pressure=50

Save and close the file.

### Reboot NavPi
    sudo reboot



## Approach 2 - Making a USB swap
This is not my favorite approach at the moment, since it requires the extra USB drive and lots of additional configurations.

### 1. Setup USB swap drive

  - connect your USB drive to the NavPi (using an 8GB drive for this test)
  - enter the following command `sudo blkid` (This will list connected drives)
  - locate your USB drive `/dev/XXX`
  - unmount the drive with `sudo umount /dev/XXX` where `XXX` is device name
  - create/format your swap with `sudo mkswap /dev/XXX`
  - if successful you'll see a message like `Setting up swapspace...`
  - copy the new UUID (everything inside the quotes UUID="XXXX-XXXX")
  - edit `fstab` file with `sudo nano /etc/fstab`
  - enter `UUID=XXXX-XXXX none swap sw,pri=5 0 0` where XX's are your UUID
  - enter `sudo swapon -a`
  - enter `cat /proc/swaps` to see your new swap drive listed `dev/XXX`

### 2. Configure Raspbian to use new swap drive

  - enter `sudo nano /etc/dphys-swapfile`
  - set the path to your new swap `CONF_SWAPFILE=/dev/sda1`
  - ctrl + O to `WriteOut` the file
  - press enter to Write `/etc/dphys-swapfile`
  - ctrl + X to `Exit` nano editor
  - enter `cd etc/`
  - enter `sudo dphys-swapfile setup`

### 3. Mounting drive on boot
  - enter `sudo nano /etc/rc.local`
  - add `sleep 20`
  - add `sudo mount -a`
  - these lines should be added before last line `exit 0`
  - ctrl + O to `WriteOut` the file
  - press enter to confirm
  - ctrl + X to `Exit` nano editor
  - enter `sudo reboot`

### Errors to deal with...
You might get a `a start job started by dev-disk-by...` message on reboot of the Pi followed by a 90 second delay during each boot. This is normal when using swap drive.

### Check current memory
See how much current memory you have on your Pi with `free -h`

install `htop` for best stats:

- `sudo apt-get install htop`
- run `htop`

