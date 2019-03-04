
## Configuration
Just modify `/etc/fstab.example` with your credentials and merge the content to your own fstab file, located in `/etc/fstab` on your Linux device.

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

## Usage

 1. Make the NAS path by doing: 
 `mkdir /mnt/fritz_nas/%NAS_PATH%`

2. Enable `rpcbind` by following command:
`sudo update-rc.d rpcbind enable`

3. Test if your device appears:
`sudo mount -a`

4. Your NAS will be available on your Linux device on: 
`cd /mnt/fritz_nas/%NAS_PATH%`
