Design decisions drive a lot of infrastructure choices. A lot of money and maintenance issues can be avoided by having architects, stakeholders, and operations people agree on the trade-offs together.

The typical architecture scaling starts with the...

* Entire stack being delivered from one server
* Then that server gets made bigger
* Then the database is split out
* Then a load balancer is put in front several servers
* Then the database gets mirrored and synced

As it grows, maintenance gets super complicated because of data sync issues. This pattern can be improved upon.

## "Static is the new black"
* Static sites are the fastest, the most secure (nothing to hack), and instantly scalable.
* They're hard to update, difficult to grow the variety of features
* Several generators exist: middleman is a favorite, list available at www.staticsitegenerators.net

## Considerations

* Is your site mostly static, like a blog?
* What percent of the time is it static?
    * A CMS can function as the backend to a static server.
    * WordPress and Drupal are big hacking targets, significant amount of bandwidth is penetration attacks from bots trying to hack common CMS risk vectors.
* Sync between them with a cron job, or mirror with wget.
* Comments can be implemented with Facebook or Disqus to push the maintenance obligation onto them.
* Simple forms can be implemented by FormStack or Wufoo
* Forums can be implemented by Discourse

## Parts of your site that are unique...

* Should go browser-based (Angular, Ember, React...) to push as much processing burden onto the user as possible.
* Caching
    * Only possible if content is static. JS and Cookie management can keep your pages static but allow simple dynamics.
    * By putting static elements such as assets on their own subdomain, you can force caching much easier.
    * CDN is basically just a cache. If you dev like this, you are "CDN ready."
* The same can be done for APIs. How static are they?

## Example

1. A user gets the site from an AWS CloudFront service. This is an infinitely scalable CDN service that can't be crashed.
1. CloudFront gets data from an EC2 instance and caches the result, meaning it doesn't need to get the EC2 server often.
1. Users upload content to an S3 bucket. The EC2 runs a cron every few minutes to sync assets from theS3.

This strategy allowed a single server to handle 100,000 users over 5 minutes during a World Series ad.

## Another Example

* An S3 instance and a Route 53 service handled a moderate number of users for $3 a month
* Scaled up to Node/S3/CloudFront/Heroku/Mongo via compose.io/Redis via redisgreen to handle a fully scaled load for $40 a month.
