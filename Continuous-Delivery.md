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

## Configuration Management

Configuration management is the process for storing, retrieving, and modifying all of the artifacts for your project.

If you're doing it well, all of these should be true:

* [ ] You can exactly reproduce any environment- OS, network configuration, software stack, applications, app config, etc.
* [ ] You incrementally change any of those and deploy them to any or all environments
* [ ] You can see all changes in all environments and trace them back to who changed them and when
* [ ] You can satisfy all of your compliance obligations
* [ ] Can every member of the team get the information they need and make the changes they need to make

### Version Control

Keep everything in version control:

* App code
* Documentation
* Environment configuration information
* Requirements
* Test scripts

All of this helps easily recreate any version of the application and get anyone new to the team up and running quickly.

Changes need to be checked into master quickly and regularly
    * Run your tests before check-in to reduce chance of conflicts
    * Should ideally be several times a day
    * Commit messages should be long and detailed, include an overview and links to tickets

It's useful to have copies of external libraries stored somewhere, and split your application into components with separate pipelines and clean interfaces between each other.

Configuration information is even more risky to change than source code because it throws such unclear errors, which is why it should be versioned so carefully.

Types of configuration:

* Pulled into binaries at build time
* Pulled into packages at packaging time
* Pulled into an installation at deployment time
* Fetched into the application at run time

It's ideal to push configuration as late as possible, to keep your application code universal.

You can store configurations in a database, or a key-value store like Redis. You can have your application access them through an interface to isolate them from how they are being stored and to make them injectable for tests. You may need to store the keys in version control separately from the values (passwords, things that change on a different cycle than the app). Keep binaries separate from configuration information, and keep all configuration information in one place.

Your configuration depends on:

* The application
* The version of the application
* The environment it's running in

Testing configuration:

* Test that your external dependencies are still functioning
* Write smoke tests for your application that depend on it being configured correctly

Production environments should be completely locked down- no one should be able to modify them directly.
