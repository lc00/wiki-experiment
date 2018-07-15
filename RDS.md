Reasons to use a separate database server:

* Security - Having different security for your database than your app server
* Accessibility - More than one server can access it
* Hardware/software - Different usage patterns than servers

RDS is managed (AWS takes care of administration) and gives you a single endpoint to connect to. It's guaranteed to be available, replicated, and patched.

Types:

* `T` - Burstable
* `M` - Standard
* `R` - Memory-Optimized

## Provisioning

1. Launch
2. Select engine
3. Use-case
4. Setup username/password, database name, availability
5. Put your DBS in the same VPC as your server for fast, secure access
6. Open up traffic on your RDS security group to allow only your EC2 to talk to it
    * Open up port 3306 (MySQL) or 5432 (Postgres) to inbound traffic from the security group
    * Start typing `sg` and you'll be prompted with all of the security groups you have
