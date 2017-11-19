## Concepts

### Sessions

Sessions store user information so that you don't need to look it up or reauthenticate every time

* You can store sessions in a data store on the server, and access them with a key stored in a cookie on the user's browser
* You can store sessions in JWTs, which are encrypted and decrypted by the server, and kept in local storage on the user's browser

### Verification

Once you have a user's credentials, you need to make sure they are a valid user.

* Hashing, etc. happens here
* You can use their credentials to look them up in a database

### Strategies

* Local - Username/Password from a form, stored locally
* Basic - Username/Password from a header, stored locally
* OAuth/Social - User redirects to a third-party site, returns with an authorization key
* JWT - Encrypt/Decrypt a session that the app makes, but the user stores

### Third-Party Authentication

* Generally have to get a client ID and client secret from them, and send OAuth requests to them with these
* You may also have to white-list callback URLs/patterns
* Your app sends a user to a route that fires off the OAuth redirect
* When the user's browser redirects to the third-party, it knows how to get back to the site because of the callback URL
* The callback URL should try to authenticate the user, redirect back to login in case of a failure, or redirect to a route in case of success
