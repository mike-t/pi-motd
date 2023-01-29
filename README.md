# Pi-MOTD

---

My working dynamic Linux MOTD displayed when accessing device by SSH or terminal directly. Primarily designed for Raspberry Pi.

## Credits
Thanks to others for advice and MOTD examples, including:
* **Gagle** installation and MOTD samples https://github.com/gagle/raspberrypi-motd

## Compatibility
Designed for and tested on Raspberry Pi 3 Model B Rev 1.2 (Linux 5.15.84-v8+ aarch64 GNU/Linux) (Debian 11 Bullseye)
Written in pure Bash. No need to install any packages.

## Installation
The following steps may vary depending on the OS. Debian 11 (Bullseye) is assumed.

*Note: There are multiple locations from where you can start the MOTD script, for example, as `~/.bash_profile`, or  `/etc/profile.d/motd.sh`. More about [autostarting scripts](https://wiki.archlinux.org/index.php/Bash#Configuration_file_sourcing_order_at_startup).*

1. Remove the default MOTD. It is located in `/etc/motd`.
  
  ```bash
  $ sudo rm /etc/motd
  ```
  
2. Remove the "last login" information from sshd. Disable the `PrintLastLog` option from the `sshd` service. Edit the `/etc/ssh/sshd_config` file and uncomment the line `#PrintLastLog yes`:
  
  ```bash
  $ sudo nano /etc/ssh/sshd_config
  ```
  
  After:
  
  ```text
  PrintLastLog no
  ```
  
  Restart the `sshd` service:
  
  ```bash
  $ sudo systemctl restart sshd
  ```

Note: If you don't see the degree Celsius character correctly (`º`) make sure you have enabled a UTF8 locale ([Arch Linux locales](https://wiki.archlinux.org/index.php/locale)).

3. If it doesn't exit already, create a `.bash_profile` file in your user's home directory
  ```bash
  $ touch ~/.bash_profile
  ```

4. Download or [copy raw](#fixme) `motd-pi.sh` bash script to your new `~/.bash_profile` using your favourite editor (e.g. `vi` or `nano`)
