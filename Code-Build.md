Imports a `.zip` or git repo, runs the build steps, and puts the output in S3

## Projects

* Source can be S3, Code Commit, Bitbucket, or GH
* Bring your own Docker (using ECR) or use theirs
* `buildspec.yml` describes the how to execute the build
* Artifacts (the resulting build) can be put in S3

## Builds

* Can be a specific commit
* Can inject environment variables
