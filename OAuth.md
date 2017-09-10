## Notes

* If you don't need to access a user's data on another system, use HTTP Basic or HTTP Digest instead
* Open standard for authorization
* Gives users access tokens 

## Versions

* Don't use OAuth2 for sensitive data
* OAuth2 is much more popular
* OAuth 1.0a is much more secure

## OAuth 1.0a Modes

* 1-legged
* 2-legged
* 3-legged

## OAuth2 Modes

Also called "grant types"

* Authorization Code (3-legged)
    * Use with server-side web apps
    * Steps:
        1. User chooses to do 3rd-party login
        1. User is redirected to the 3rd-party (`https://login.blah.com/oauth?response_type=code&client_id=xxx&redirect_uri=xxx&scope=email`), logs in, and accepts certain permissions
        1. 3rd-party redirects back to your site with an authorization code (`https://yoursite.com/oauth/callback?code=xxx`)
        1. Your app makes a request to the 3rd-party with the authorization code (`POST https://api.blah.com/oauth/token?grant_type=authorization_code&code=xxx&redirect_uri=xxx&client_id=xxx&client_secret=xxx
        `), and gets an access token that they can use to request data
* Implicit (2-legged)
    * Use with client-side web apps or mobile apps
    * User doesn't have access to the `client_secret` value
    * Steps:
        1. User chooses to do 3rd-party login
        1. User is redirected to the 3rd-party (`https://login.blah.com/oauth?response_type=token&client_id=xxx&redirect_uri=xxx&scope=email`), logs in, and accepts certain permissions
        1. 3rd-party redirects back to your site with an access code (`https://yoursite.com/oauth/callback?token=xxx`), and gets an access token that they can use to request data
* Password Credentials (2-legged)
    * Use with an OAuth service you built yourself
    * Steps:
        1. User chooses to login
        1. They input their username/password into your site (`POST https://login.blah.com/oauth/token?grant_type=password&username=xxx&password=xxx&client_id=xxx
        `), and gets an access token that they can use to request data
* Client Credentials (2-legged)
    * Use with an application that doesn't interact with user data (logging, services, etc.)
    * Steps:
        1. Your app makes a request to the identity provider's API using its credentials (`POST https://login.blah.com/oauth/token?grant_type=client_credentials&client_id=xxx&client_secret=xxx
        `), and gets an access token that you can use to request data
* Refresh Token
