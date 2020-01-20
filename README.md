
General
=======

Credentials
-----------
You get your credentials by adding a new user with FRITZ!NAS access on your router. Fill your credentials based on the table below:

| Substitution | Description |
| :-: | :-- |
| **`<ROUTER_IP>`** | Your FRITZ!Box IP (Most times 192.168.178.1) | 
| **`<NAS_PATH>`** | Path on your NAS device, which you are allowed to access (With your user). |
| **`<USERNAME>`** | Your FRITZ!NAS user which will have access to your `<NAS_PATH>`. |
| **`<PASSWORD>`** | Your FRITZ!NAS user password which will have access to your `<NAS_PATH>`. |


fstab Method
============

Configuration
-------------
Just modify `/etc/fstab.example` with your credentials and merge the content to your own fstab file, located in `/etc/fstab` on your Linux device.

Usage
-----

 1. Make the NAS path by doing: 
 `mkdir /mnt/fritz_nas/<NAS_PATH>`

2. Enable `rpcbind` by following command:
`sudo update-rc.d rpcbind enable`

3. Test if your device appears:
`sudo mount -a`

4. Your NAS will be available on your Linux device on: 
`cd /mnt/fritz_nas/<NAS_PATH>`

Docker Method
=============

This method is used in my case, for shared data between multiple docker nodes.

Usage
-----

Create a volume in your docker environement

```
docker volume create \
    --driver local \
    --opt type=cifs \
    --opt device=//<ROUTER_IP>/fritz.nas/<NAS_PATH> \
    --opt o=uid=0,username=<USERNAME>,password=<PASSWORD>,vers=1.0,file_mode=0770,dir_mode=0770,addr=<ROUTER_IP>,rw \
    FRITZ_NAS_DOCKER
```

Test your created volume by executing following comands:

```
docker run -v FRITZ_NAS_DOCKER:/world busybox touch /world/FRITZ_NAS_DOCKER_TEST_FILE
```

```
docker run -v FRITZ_NAS_DOCKER:/world busybox ls /world
```

Your command window shall now show you the folder structure including the new generated file "FRITZ_NAS_DOCKER_TEST_FILE".

Tested FRITZ!Boxes
==================
| FRITZ!Box | FRITZ!OS | Tested | Working |
| :-- | :-: | :-: | :-: | 
| FRITZ!Box 6490 Cable | < 07.02 | :heavy_check_mark: | :heavy_check_mark: |

Feel free to test your own FRITZ!Box and add it to this table or create an issue for that.

