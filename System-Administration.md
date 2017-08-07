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
* `time <command>` - Report time elapsed
* `ps` - Show running processes
    * `-e` - All processes
    * `-x` - System
    * `-f` - "Forest" tree view
* `watch <command>` - Alert when a command’s output changes
* Monitor logs in realtime with `sudo tail -50 -f <log_name>`

## Permissions

* `chgrp -R <group> <file>` - Change the group of a file
* `chown -R <user> <file>` - Change the owner of a file
* `chmod -R u=rxw,g=rx,o=r <file>` - Set permissions
* `chmod -R ugo+r,ugo-x <file>` - Add and remove permissions
* `umask <022>` - Set default permissions for this session only

## User Commands

* `passwd` - Changes your password
* `logout` - Logout user, end session
* `su <username>` - Switch user, keeping your session
* `su - <username>` - Switch user, new session
* `finger` - Show who's logged in
* `who` - Finger with basics
* `w` - Finger with what the users are doing
* `last` - Last logged in users
* `id` - Information about yourself
* `groups <username>` - Show what groups a user is in

## System Commands

* `uname -a` - Display OS information
* `dmesg` - Show boot information

## Scheduling

* `at <time>` - Starts scheduling a one-time job
    * Enter job
    * `ctrl+d` to stop
* `atq` - Shows queued jobs
* `atrm <number>` - Cancels job
* `crontab -e` - Edit your cron file
    * `<min> <hour> <day> <month> <0-6 sun-sat>`
    * commas for multiples
    * `*` for any match
    * `-` for range
    * Use full paths. No environment vars available.
    * crontab -l = list your cron jobs

## Backup/Archive Commands

* `wget <url>` - Download webpage
* `tar -cf <destination_file> <input_files>` - Combine files (`-c` = create, `-f` = name file)
* `tar -xvf <source_file> <destination_directory>` - Extract (`-x` = extract, `-v` = verbose)
* `gzip <file_name>` - Compress
* `gunzip <file_name>` - Uncompress
* `rsync -v -a <source> <destination>` - Backup. Can be done remotely.

## Background Processing

* `Ctrl+z` to suspend a process
* `bg` - Restart most recent process in the background (%<number> for a specific)
* `fg` - Restart most recent process in the foreground (%<number> for a specific)
* `kill <process>` - Remove a process (-9 to force kill)
    * `%<command>`
    * `%<process number>`
    * `<pid>`
* `pkill <command>` - Kill by name
* `jobs` - Show running jobs
* `Start a command in the background by ending it with &
* `nice -n [-20-19] <command>` - Set priority
* `renice - n [-20-19] <command>` - Reset priority

## Setting up remote access on a server

* Generate an SSH key on the local computer
* Make sure there's an `~/.ssh` folder in the remote computer with `install -d -m 700 ~/.ssh`
* Copy your public key to the remote server's `.ssh/authorized_keys` folder with `cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> ~/.ssh/authorized_keys'`

## SSH

* `ssh <username>@<domain>`
* end with `logout`

## Communication

* `wall "message"` - Send a message to all logged in users ("write all")
* `write username [tty]` - Send messages to a specific user. Find out your tty with `tty`. Terminated by Ctrl-D.
* `talk username` - Start a chat with a user. Can be remote. 

## Mounting a device

```bash
mkdir /mnt/sd # Make a folder to mount to
sudo mount /dev/mmcblk0p1 /mnt/sd # Mount the device to the folder
sudo umount /mnt/sd # Unmount the folder
```

## Network

* `ping` - Check if a computer is up
* `traceroute` - Shows the path a packet took
* `nslookup <domain>` - Show IP address

## DNS Lookup

* To look up all DNS records, use `dig -t ANY example.com +noall +answer`
* You can set default options in a `~/.digrc` file

## Reverse-DNS Lookup

* To see what URL owns an IP, use `dig -x 127.0.0.1`
