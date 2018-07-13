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

Or install `htop:`
- `sudo apt-get install htop`
- run `htop`

### Setup USB swap drive (WIP)

  - connect your USB drive to the NavPi
  - locate your USB drive `/dev/XXX`
  - unmount the drive with `sudo umount /dev/XXX` where `XXX` is device name
  - create/format your swap with `sudo mkswap /dev/XXX`
  - if successful you'll see a message like `Setting up swapspace...`
  - copy the new UUID (everything inside the quotes UUID="XXXX-XXXX")
  - edit `fstab` file with `sudo nano /etc/fstab`
  - enter `UUID=XXXX-XXXX none swap sw,pri=5 0 0` where XX's are your UUID
  - enter `sudo swapon -a`
  - enter `cat /proc/swaps` to see your new swap drive listed `dev/XXX`
  - enter the following command `sudo blkid` (This will list connected drives)

### Configure Rasbian to use new swap drive (WIP)

  - enter `sudo nano /etc/dphys-swapfile`
  - uncomment `#CONF_SWAPFILE`
  - set the path to your new swap `CONF_SWAPFILE=/dev/sda1`
  - uncomment `#CONF_SWAPSIZE`
  - set the size `CONF_SWAPSIZE=1024` (1 GB)
  - ctrl + O to `WriteOut` the file
  - press enter
  - ctrl + X to `Exit` nano editor
  - stop service `sudo /etc/init.d/dphys-swapfile stop` (you'll see an [ok] message)
  - start service `sudo /etc/init.d/dphys-swapfile start`

### Connect to NavPi from external system (WIP)

If you are unable to access a screen, keyboard and mouse to plug in directly to the NavPi, you can access the the web UI from a computer on the same network. You can also ssh directly to the Pi if needed to perform tasks like upgrades or other commands.

### Questions

- Is it possible to use zram and usb swap at the same time?