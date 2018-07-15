## Overview

Handles 4 related services:

* Domain registration
* DNS management
* Traffic management - Simliar to ELB, chainable
    * Simple routing policy - Matches the record set
    * Weighted routing policy - Directs proportion of traffic to different places
    * Latency routing policy - Matches the server with the lowest latency for a user
    * Failure routing policy - Redirects traffic away from a failing server
    * Geolocation routing policy - Directs user to a server that it's in the nearest availability zone to them
* Availability monitoring (Health Checks)
    * Notifies you in the event of a failure. Give it a URL or IP and a path, and it will email you in the event of a failure.

Hosted zone: Records related to a specific domain
TTL: Time to live, how often your records are refreshed. Lower is faster, but more expensive.

## DNS Record Types

* A Record - Maps a URL to an IP
    * Don't associate something to your EC2 public IP address- it could easily change. Instead, add an elastic IP to your EC2 from the dashboard, and use that.
* ALIAS record: Redirects a domain to another domain, can be used at the apex
* CNAME - "Canonical name", Maps one URL to another URL (never an IP)
    * Can't be used at the apex
* NS - "Name servers", the addresses that will resolve the URL
    * Authoritative name servers that can be queried about your domain. These are public services.
* MX - "Mail Exchange", IP that will handle mail requests
* SOA: Start of Authority. Basic DNS configuration information.

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
* No SSL (http only)

## Redirecting and masking the URL with Firebase Deploy

* Make a new Hosting Zone- this is a collection of DNS records related to one domain
* Copy the generated NS URLs to the Name Server entries for the domain
* Add an A Record to the Hosting Zone, set the values to Firebase's name servers:
    ```
        151.101.1.195 
        151.101.65.195
    ```
* Use "Connect Custom Domain" on Firebase the console and follow the instructions.
* Google will issue an SSL certificate within 24 hours (https)
