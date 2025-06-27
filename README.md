# OctoPrint-NetworkHealth

![GitHub top language](https://img.shields.io/github/languages/top/jonfairbanks/OctoPrint-NetworkHealth.svg)
![GitHub last commit](https://img.shields.io/github/last-commit/jonfairbanks/OctoPrint-NetworkHealth.svg)
![License](https://img.shields.io/github/license/jonfairbanks/OctoPrint-NetworkHealth.svg?style=flat)

#### Monitors the health of the OctoPrint Network connection and restarts it if necessary

### Configuration

By default the `ip` command used to restart the network interfaces requires sudo permissions. 

To allow OctoPrint to manage this for us, we need to update sudoers using the below command:
```
echo 'pi ALL=NOPASSWD:/sbin/ip' | sudo tee /etc/sudoers.d/octoprint-ip
```

If your system does not have `ip` installed, you can install it via apt:
```
apt-get install iproute2
```

### Commands used to restart the network
```
sudo sh -c 'ifconfig wlan0 down; sleep 5; ifconfig wlan0 up'
sudo sh -c 'ifconfig eth0 down; sleep 5; ifconfig eth0 up'
```
➤ ifconfig <interface> down
Disables (takes down) the network interface. This disconnects it from any network.

➤ sleep 5
Waits for 5 seconds before doing anything else.

➤ ifconfig <interface> up
Re-enables (brings up) the interface. This makes it available again and allows it to reconnect.

### Setup

Install via the bundled [Plugin Manager](https://docs.octoprint.org/en/master/bundledplugins/pluginmanager.html)
or manually using this URL:

    https://github.com/jonfairbanks/OctoPrint-NetworkHealth/archive/master.zip
