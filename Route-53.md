## DNS Record Types

* A Record - Maps a URL to an IP
* CNAME - "Canonical name", Maps one URL to another URL (never an IP)
* NS - "Name servers", the addresses that will resolve the URL

## Redirecting a DNS record

* Make a new Hosting Zone- this is a collection of DNS records related to one domain
* Copy the generated NS URLs to the Name Server entries for the domain
* Create a new S3 bucket
    * Make the name identical to the URL, including subdomain (you'll need one for naked and www)
    * Set the property of the bucket to be a static host, and redirect to the URL the site lives at
* Add an A Record to the Hosting Zone, set the alias to the bucket you set up
