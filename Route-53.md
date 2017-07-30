## DNS Record Types

* A Record - Maps a URL to an IP
* CNAME - "Canonical name", Maps one URL to another URL (never an IP)
* NS - "Name servers", the addresses that will resolve the URL

## Redirecting a URL to another URL

* Make a new Hosting Zone- this is a collection of DNS records related to one domain
* Copy the generated NS URLs to the Name Server entries for the domain
* Create a new S3 bucket
    * Make the name identical to the URL, including subdomain 
    * You'll need one for the "apex" and www if you want to keep the www in the address, otherwise use a CNAME record for www
    * Set the property of the bucket to be a static host, and redirect to the URL the site lives at
* Add an A Record to the Hosting Zone, set the alias to the bucket you set up

## Redirecting and masking the URL with Github Pages

* Make a new Hosting Zone- this is a collection of DNS records related to one domain
* Copy the generated NS URLs to the Name Server entries for the domain
* Add an A Record to the Hosting Zone, set the values to Github's name servers:
    ```
        192.30.252.153 
        192.30.252.154
    ```
* Add the URL to the Github repo in "Settings" (it adds a `CNAME` file with the apex domain name to the repo)

## Redirecting and masking the URL with Firebase Deploy

* Make a new Hosting Zone- this is a collection of DNS records related to one domain
* Copy the generated NS URLs to the Name Server entries for the domain
* Add an A Record to the Hosting Zone, set the values to Firebase's name servers:
    ```
        151.101.1.195 
        151.101.65.195
    ```
* Use "Connect Custom Domain" on Firebase the console and follow the instructions.
