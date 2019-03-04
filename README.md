> # fritz_nas_auto_mount
This repository manages example files, to auto-mount your FRITZ!NAS on boot to your Linux device (In my example a Raspberry Pi running on Raspbian Stretch)

## Configuration
Just modify [https://github.com/Pantastisch/fritz_nas_auto_mount/blob/master/etc/fstab.example](fstab.example) with your credentials and merge the content to your own fstab file, located in `/etc/fstab`.

## Credentials
You get your credentials by adding a new user with FRITZ!NAS access on your router. Fill your credentials based on the description below:

**`%ROUTER_IP%`**
Your FRITZ!Box IP (Most times 192.168.178.1)

**`%NAS_PATH%`**
Path on your NAS device, which you are allowed to access (With your user).

**`%USERNAME%`**
Your FRITZ!NAS user which will have access to your `%NAS_PATH%`.

**`%PASSWORD%`**
Your FRITZ!NAS user password which will have access to your `%NAS_PATH%`.




Written with [StackEdit](https://stackedit.io/)
