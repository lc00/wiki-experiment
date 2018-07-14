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
