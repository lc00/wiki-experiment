Security groups are very blunt tools, IAM allows you to create "users" within accounts with different permissions. Either CLI access with keys, or a separate login page specific to the account.

IAM Policy: Who may perform what actions on what resources through a set of statments.

* Effect: Allow/Deny
* Principal: User via their unique ARN ID
* Policy Action: Which action on which service
* Resource: Which instances

Concepts:

* User: Account within account
* Groups: A combination of policies you can apply to users
* Roles: Permissions owned by objects
* Access Keys: CLI/API access

## Service Roles

* Created in IAM
* Allow one AWS service to talk to another
