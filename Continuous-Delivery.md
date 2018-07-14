## The Problem of Delivering Software

The goal is to deliver useful, working software to users as quickly as possible. To do this, we reduce cycle time, which is how long it takes between deciding to make a change and your customer seeing it. One way to measure it is by how long it takes to release a one-line change.

### Deployment Pipeline

An automation of the organization's build, deploy, test, and release process. For example:

`Commit Stage -> Automated acceptance testing -> Automated capacity testing -> Manual testing -> Release`

Every commit should result in a potential release.

### Antipatterns

* Deploying software manually - Anything manual is error-prone and slow
* Deploying to a production-like environment only after development is complete - Catch errors earlier
* Manual configuration management of production environments - Leads to unpredictability between environments

### Frequent, Automated Releases

For feedback to be useful:

* Any change needs to trigger the feedback process
    * A change in executable code, configuration, host environment, and data
    * Code should be identical everywhere- any differences are configuration
* The feedback must be delivered as soon as possible
    * Only possible through automation
    * Early tests run quick and ensure the application works, later tests run slower and ensure that it works in your production environment
* The delivery team must receive feedback and then act on it

### Principles of Software Delivery

* Create a repeatable, reliable process for releasing software
    1. Provisioning and managing the environment in which your application will run
    2. Installing the correct version of your application on it
    3. Configuring your application, including any data or state it requires
* Automate almost everything
* Keep everything in version control
    * Combine relevant changes into change sets with a single ID:
        * Documents
        * Application and network configuration scripts
        * Deployment and test scripts
        * Database creation, upgrade, downgrade, and inititialization scripts
        * Libraries
        * Toolchains
* If it hurts, do it more frequently and bring the pain forward
* Build quality in
* Done means released
* Everybody is responsible for the delivery process- DevOps
* Continuous improvement
