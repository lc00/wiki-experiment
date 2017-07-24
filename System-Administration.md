## System monitoring

* `free -h` - Current RAM and swap usage
* `du -h /` - Disk usage of current disk
* `df -h --max-depth=1 ~` - Disk usage of home folder
* `top` - Look at running processes
    * `z` to color, `V` to tree
    * `l`, `t`, `m` - Toggles summary, CPU, and Memory displays
    * `R` to sort
    * `k` to kill a process
    * Arrows to scroll
    * `W` to write to a config file

## Setting up remote access on a server

* Generate an SSH key on the local computer
* Make sure there's an `~/.ssh` folder in the remote computer with `install -d -m 700 ~/.ssh`
* Copy your public key to the remote server's `.ssh/authorized_keys` folder with `cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> ~/.ssh/authorized_keys'`

## Mounting a device

```bash
mkdir /mnt/sd # Make a folder to mount to
sudo mount /dev/mmcblk0p1 /mnt/sd # Mount the device to the folder
sudo umount /mnt/sd # Unmount the folder
```
