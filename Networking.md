## General

* Router is usually at `XXX.XXX.0.1` -> On TP-Link, that's `192.168.0.1`
* Forward incoming requests on a port to internal IPs and ports
* Connected wired devices are at `IP & MAC Binding > ARP List`
* Connected wireless devices are at `DHCP > Clients List`
* Your `/etc/hosts` file will map a hostname to an IP address
* Look up all devices on your network with `nmap -sP "192.168.0.*"`
* Look up information about your network adapter with `ifconfig`

## Dynamic IP addresses

* Your router's address changes, but you can setup a [service](https://noip.com) that gives you a static domain name that redirects to a variable IP address
* Configure your router to update the service, or install a client on an always-connected computer in your network that updates it

## Assigning static IP addresses

* Under `DHCP > Address Reservation`, put the MAC address of the hardware and the IP address you'd like to reserve
    * Address must be outside of the range of addresses assigned by DHCP
* Edit `/etc/dhcpcd.conf`
* At the bottom of the file, add (for wired/wireless connections):

    ```
    interface eth0

    static ip_address=192.168.0.10/24
    static routers=192.168.0.1
    static domain_name_servers=192.168.0.1
    ```

    ```
    interface wlan0

    static ip_address=192.168.0.11/24
    static routers=192.168.0.1
    static domain_name_servers=192.168.0.1
    ```
