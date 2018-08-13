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

## CLI

* List instances: `aws ec2 describe-instances`
* Creating an instance: `aws ec2 run-instances --security-group-ids sg-0448c212 --image-id ami-12b5f758 --instance-type t2.nano --count 1 --subnet-id subnet-bc4621db`
* Terminating instances: `aws ec2 terminate-instances --instance-ids i-01d26164507118d30`

## Multiple Availability Zones

* When deploying, you can select a subnet for a different availability zone within the same VPC
