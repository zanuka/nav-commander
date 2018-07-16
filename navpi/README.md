# NavPi

Dev notes on the [NavPi Stake Box](https://github.com/Encrypt-S/navpi) project

Rough drafts of content, configs, and support docs.

For official documentation, refer to the [NavPi Knowledge Base](https://info.navcoin.org/article-categories/navpi/)

## Focus
- audit current version of NavPi (functionality, setup, support, docs)
- create updated content to enhance stability and support NAV community

## Improving performance

The current NavPi configuration is in need of a performance optimisation.

### Check current memory

See how much current memory you have on your Pi with `free -h`

install `htop` for best stats:

- `sudo apt-get install htop`
- run `htop`

### 1. Setup USB swap drive (WIP)

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

### 2. Configure Raspbian to use new swap drive (WIP)

  - enter `sudo nano /etc/dphys-swapfile`
  - set the path to your new swap `CONF_SWAPFILE=/dev/sda1`
  - set the swap size `CONF_SWAPSIZE=4096` (4 GB)
  - set the max swap size `CONF_SWAPSIZE=7168` (7 GB)
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

### Connect to NavPi from external system (WIP)

If you are unable to access a screen, keyboard and mouse to plug in directly to the NavPi, you can access the the web UI from a computer on the same network. You can also ssh directly to the Pi if needed to perform tasks like upgrades or other commands.

### Questions

- Is it possible to use zram and usb swap at the same time?