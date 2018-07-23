# Enable ZRAM on your NavPi
The steps in this guide come from [novaspirit](https://github.com/novaspirit)'s repo [rpi_zram](https://github.com/novaspirit/rpi_zram) and further information about ZRAM can be found [here](https://en.wikipedia.org/wiki/Zram).

Novaspirit's script will dynamically enable ZRAM on your current NavPi. It automatically detects the number of CPU cores to allocate to ZRAM computation, disables existing swap and enables ZRAM swap.

We have tested this on the NavPi devices and it does improve performance, though the [USB swap solution](usb-swap.md) seems to be superior if you are relying 100% on using the Chromium UI w/ Keyboard/Mouse connected to your NavPi.

If your current NavPi is running out of memory, ZRAM helps by expanding the amount of data you can store in RAM. It essentially buys you more time if you don't have the USB swap enabled.

## Let's get started

### Upgrade NavPi to latest version
Before attempting this, you should follow this article from the official Knowledge Base:
[How to update the NavPi](https://info.navcoin.org/knowledge-base/how-to-update-the-navpi/)

After updating, reboot your NavPi

    sudo reboot

If update is successful you should now see the `cfund` directory appear in `/home/stakebox/.navcoin4`

    cd /home/stakebox/.navcoin4
    ls

    Output
    banlist.dat blocks cfund chainstate database db.log debug.log fee_estimates.dat navcoin.conf navcoin.pid peers.dat wallet.dat

### Backup your current NavPi img
Before proceeding with this swap configuration, it is worth making a backup image of your NavPi's SD card so if it fails, you can easily restore to this point. Follow this [guide](https://info.navcoin.org/knowledge-base/creating-a-navpi-back-up-img/).

### Backup your wallet.dat
To ensure you don't lose any coins while making configuration changes to your NavPi, it's essential to backup the wallet.dat file. This holds your private keys. With a backup of the wallet.dat you can always restore your wallet.

First, make sure your have encrypted your wallet. Then proceed with the following steps:

1. Open the WebUI
2. Go to `control`
3. Scroll down to `security`
4. *Click* `Backup Wallet`. This will download the wallet.dat file to your preferred device (USB, HD)
5. Save the wallet backup and rename it to `wallet.dat`

### Download and copy script
This will download and copy the `zram.sh` script to your `/usr/bin` directory

    sudo wget -O /usr/bin/zram.sh https://raw.githubusercontent.com/novaspirit/rpi_zram/master/zram.sh

### Make the script file executable

    sudo chmod +x /usr/bin/zram.sh

### Ensure that the script runs on startup / reboot

    echo '/usr/bin/zram.sh &' | sudo tee -a /etc/rc.local

    Output
    /usr/bin/zram.sh &

### Change .navcoin4 directory permissions

    cd /home/stakebox/.navcoin4
    sudo chown www-data:www-data -R chainstate cfund blocks chainstate
    sudo chmod 777 -R cfund blocks chainstate

If successful, you'll be able to see that the directories have the correct permissions.

    ls -l

The permissions should be `drwxrwxrwx` on `blocks`, `cfund`, `chainstate`

### Reboot NavPi
    sudo reboot

### Check memory usage with ZRAM now configured

    free -h

    Output
              total      used      free     shared    buffers     cached
    Mem:       923M      879M       43M         6M        22M        97M
    -/+ buffers/cache:   760M      163M
    Swap:       99M       29M       70M

**Pro Tip:** Install htop, a nice option for monitoring interactively. It's a nice way to filter on running processes, like 'nav'. It combines the functionality of top and iotop into a single screen. It's not a necessity, you can always just use `free -h`.

    sudo apt-get install htop
    htop

### Enjoy Stability

Now that ZRAM has been enabled on your NavPi, the system should be stable.

### Access via WebUI

You may still notice sub-optimal performance while using the built-in Chromium UI. If you have another computer available on the same home network, you can view the WebUI of the NavPi.

1. Visit the IP-address of the NavPi on any web browser
2. Ignore warning (click proceed) about an unsafe certificate
3. Enter your password for WebUI (default is NAV if you haven't changed it yet)







