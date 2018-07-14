## Intro

* Virtual Private Cloud (VPC): Virtual network that allows fast communication between resources, while limiting communication from the outside
* Security Group: Manages communication between your VPC and the internet
* Amazon Machine Image (AMI): Template for creating environments
* S3: Storage and backup
* EBS Volume: Hard drive for a compute resource

## EC2

* EC2 is the compute power, not the hard drive (that's the attached EBS)

To provision:

1. Launch instance
2. Choose an AMI
3. Choose an instance type (t2, m1, etc.)
4. Optionally, configure the instance, add storage, add tags, configure the security group

Open up the ports that you're going to use in the security group:

* SSH: 22
* HTTPS: 443
* HTTP: 80

You can also limit the IPs that are allowed to hit this server (eg. to another server, your home computer, etc). You can use the My IP tool to limit it to the computer you're using now.

To connect:

1. Download your key
2. `ssh -i my-key.pem ubuntu@ec2-43-34-34.us-wst-2.compute.amazonaws.com`

Estimating usage: Use `top`

* # of vCPUs - 
* Local storage (size of EBS) - Size of OS and local installations
* Memory - Size of concurrent traffic
* Bandwidth - Low/medium/high

Instance types:

* `T` - Burstable
* `M` - General purpose
* `C` - Compute-optimized
* `X` - Memory-optimized - in-memory apps
* `R` - Memory-optimized - intensive applications
* `P` - Graphics-optimized - GPU-intensive apps
* `G` - Graphics-optimized - Graphics processing
* `I` - Storage optimized - Fast
* `D` - Storage optimized - Big

## RDS

Reasons to use a separate database server:

* Security - Having different security for your database than your app server
* Accessibility - More than one server can access it
* Hardware/software - Different usage patterns than servers

RDS is managed (AWS takes care of administration) and gives you a single endpoint to connect to. It's guaranteed to be available, replicated, and patched.

Types:

* `T` - Burstable
* `M` - Standard
* `R` - Memory-Optimized

### Provisioning

1. Launch
2. Select engine
3. Use-case
4. Setup username/password, database name, availability
5. Put your DBS in the same VPC as your server for fast, secure access
6. Open up traffic on your RDS security group to allow only your EC2 to talk to it
    * Open up port 3306 (MySQL) or 5432 (Postgres) to inbound traffic from the security group
    * Start typing `sg` and you'll be prompted with all of the security groups you have

## Route 53

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

### Record Sets

Default records:

* SOA: Start of Authority. Basic DNS configuration information.
* NS: Authoritative name servers that can be queried about your domain. These are public services.

Other record sets:

* A record: Maps a domain name to an IP address
    * Don't associate something to your EC2 public IP address- it could easily change. Instead, add an elastic IP to your EC2 from the dashboard, and use that.
* ALIAS record: Redirects a domain to another domain, can be used at the apex
* CNAME record: Redirects a domain to another domain, cannot be used at the apex

## S3

Cheap file storage, organized into buckets of objects. You can also configure a bucket as a static site.

### Options

* You can enable versioning to make S3 keep track of all versions of an object
* You can enable logging to see all access to your bucket
* You can have different levels of access for different users
* You can set different levels of access frequency for a bucket, and different levels of redundancy
* You can encrypt your files or not

Files have to be public to be read directly by the web. You can use this to host websites, at a cost of about $0.03/GB/Month for storage and $0.09/GB/Month for transfer.
