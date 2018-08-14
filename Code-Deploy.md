Allows you to deploy code to multiple servers at once while leaving those servers online as much as possible.

## Deployment Types

* Blue/green - Replaces servers with new versions
* In-place - Updates running servers

## Configuring Instances

* Can be configured with Cloud Formation (text files describing an infrastructure setup)
* Needs an existing EC2 code pair
* Must have an IAM role associated with it that gives it rights to code deploy
* Must be have the code-deploy agent installed and running

## Revisions

* Version of an application to deploy
* Can be S3 or Github

## Deployment Groups

* One or more instances to deploy to
* Deployments can be one at a time, half at a time, or all at once

## Service Roles

* May need to create a new role for Code Deploy
* Grant Code Deploy access to your instances

## Deploy New Revision

* Select location (S3 or GH)
* Enter file or repo (eg. `kylecoberly/my-repo-name`)
* Enter commit ID (eg. `0ca66aa6efd9c6336dd7700e2d5d56ea9eae4e49`)
