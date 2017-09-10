## Notes

* If you don't need to access a user's data on another system, use HTTP Basic or HTTP Digest instead
* Open standard for authorization
* Gives users access tokens 
* "Legs" are # of client requests

## Versions

* Don't use OAuth2 for sensitive data
* OAuth2 is much more popular
* OAuth 1.0a is much more secure

## OAuth 1.0a Modes

* 1-legged
    * Quick and dirty, but has some security considerations
    * Steps:
        1. Application sends a signed request to a service, giving it:
            * `oauth_token`
            * `oauth_consumer_key`
            * `oauth_timestamp`
            * `oauth_nonce`
            * `oauth_signature`
            * `oauth_signature_method`
            * `oauth_version`
        1. Service validates and grants access to resources
* 2-legged
    * Makes sure a secure connection has been made first
    * Steps:
        1. Application sends a signed request to a service for a request token, giving it:
            * `oauth_token`
            * `oauth_consumer_key`
            * `oauth_timestamp`
            * `oauth_nonce`
            * `oauth_signature`
            * `oauth_signature_method`
            * `oauth_version`
        1. Service validates and responds with:
            * `oauth_token`
            * `oauth_token_secret`
        1. Client exchanges request token for access token- a signed request containing:
            * `oauth_token` <- Request token this time
            * `oauth_consumer_key`
            * `oauth_nonce`
            * `oauth_signature`
            * `oauth_signature_method`
            * `oauth_version`
        1. Service grants access token, sending back:
            * `oauth_token`
            * `oauth_token_secret`
        1. Client uses `oauth_token` and `oauth_token_secret` to make requests
* 3-legged
    * Most secure OAuth
    * Steps:
        1. Application sends a signed request to a service for a request token, giving it:
            * `oauth_consumer_key`
            * `oauth_timestamp`
            * `oauth_nonce`
            * `oauth_signature`
            * `oauth_signature_method`
            * `oauth_version`
            * `oauth_callback`
        1. Service validates and responds with request token:
            * `oauth_token`
            * `oauth_token_secret`
            * `oauth_callback_confirmed`
        1. Redirect user to service provider with `oauth_token`, user authorizes service
        1. Provider redirects back to consumer callback with:
            * `oauth_token`
            * `oauth_verifier`
        1. Client exchanges request token for access token- a signed request containing:
            * `oauth_token` <- Request token this time
            * `oauth_consumer_key`
            * `oauth_nonce`
            * `oauth_signature`
            * `oauth_signature_method`
            * `oauth_version`
            * `oauth_verifier`
        1. Service grants access token, sending back:
            * `oauth_token`
            * `oauth_token_secret`
            * `oauth_callback_confirmed`
        1. Client uses `oauth_token` and `oauth_token_secret` to make requests

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
    * Steps:
        1. Client makes request to token refresh URI with:
            * `grant_type="refresh_token"`
            * `refresh_token`
            * `client_id`
            * `client_secret`
        1. Service validates and responds with:
            * `access_token`
            * `issued_at`
