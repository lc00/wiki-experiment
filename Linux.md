## Linux File Structure

* `/bin` - Global, primitive programs
* `/etc` - Configuration and settings
* `/home` - User files
* `/sbin` - Programs needed for boot
* `/tmp` - Temporary files
* `/usr`
* `/bin` - Less critical programs, general installs
* `/local`
* `/bin` - Locally developed/installed programs
* `/man` - Help pages for local programs
* `/share/man` - Help pages
* `/var` - Changeable data, logs, temporary program files

## Linux Services

* A daemon is background process
* Daemons are listed in `/etc/init.d`
* Start/stop/restart them with `sudo service <name> <command>`
* Logs are in `/var/log` and `/var/adm`
