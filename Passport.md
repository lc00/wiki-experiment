## Overview

1. `const passport = require("passport");`
1. Import a strategy:
    * `require("passport-http").BasicStrategy`
    * `require("passport-local").Strategy`
    * `require("passport-oauth").OAuthStrategy`
    * `require("passport-oauth").OAuth2Strategy`
    * `require("passport-facebook").Strategy;`
    * `require("passport-jwt").Strategy;`
    * `require("passport-slack").Strategy;`
1. `passport.use(new Strategy(options, verify));`
1. Set the right `options` for that strategy
1. Implement the `verify` function
1. Add the authentication to the relevant routes

## Setup

* Basic Auth on an API:
```js
passport.use(new BasicStrategy(verify));
```
* Username/Password on a form:
```js
passport.use(new LocalStrategy({
    usernameField: "username", // default
    passwordField: "password", // default
}, verify));
```
* OAuth 1.0a:
```js
passport.use("provider", new OAuthStrategy({
    requestTokenURL: "https://www.provider.com/oauth/request_token",
    accessTokenURL: "https://www.provider.com/oauth/access_token",
    userAuthorizationURL: "https://www.provider.com/oauth/authorize",
    consumerKey: "123-456-789",
    consumerSecret: "shhh-its-a-secret"
    callbackURL: "https://www.mysite.com/auth/provider/callback"
}, verify));
```
* OAuth 2.0:
```js
passport.use("provider", new OAuthStrategy({
    authorizationURL: "https://www.provider.com/oauth2/authorize",
    tokenURL: "https://www.provider.com/oauth2/token",
    clientId: "123-456-789",
    clientSecret: "shhh-its-a-secret"
    callbackURL: "https://www.mysite.com/auth/provider/callback"
}, verify));
```
* Facebook (OAuth 2.0):
```js
passport.use(new FacebookStrategy({
    clientID: FACEBOOK_APP_ID,
    clientSecret: FACEBOOK_APP_SECRET,
    callbackURL: "http://www.mysite.com/auth/facebook/callback"
}, verify));
```
* JWT:
```js
var ExtractJwt = require('passport-jwt').ExtractJwt;

passport.use(new JwtStrategy({
    jwtFromRequest = ExtractJwt.fromAuthHeaderAsBearerToken(),
    secretOrKey = "secret",
    issuer = "accounts.examplesoft.com",
    audience = "yoursite.net"
}, verify));
```

* Slack:
```js
passport.use(new SlackStrategy({
   clientID: "CLIENT_ID_HERE",
   clientSecret: "CLIENT_SECRET_HERE",
   callbackURL: "http://localhost:3000/auth/slack/callback"
}, verify));
```

## Verifying a user

User lookup, hashing, etc. happens here.

Basic:

```js
function verify(username, password, done){
    var user = {username: "u", password: "p"};
    if (username != user.username){
        done(null, false);
    } else if (password != user.password){
        done(null, false);
    } else {
        done(null, user);
    }
}
```

OAuth 1.0a:

```js
function(accessToken, accessTokenSecret, profile, done){
    // `profile` is what has the user information from the provider
}
```

OAuth 2.0:

```js
function(accessToken, refreshToken, profile, done){
    // `profile` is what has the user information from the provider
}
```

JWT:

```js
function(jwt, done){
    // `jwt` is the deserialized JWT
}
```

## Authenticating a Route

* Authenticated users return `true` for `request.isAuthenticated()`
* Basic Auth on an API:
```js
app.get("/authed",
    passport.authenticate("basic", {session: false}), (request, response) => {
        // request.user has the user object
        response.json(request.user);
    }
);
```
* Local Auth on a site:
```js
app.post("/login",
    passport.authenticate("local", {
        successRedirect: "/",
        failureRedirect: "/login",
        failureFlash: true // puts a message on the redirect with the reason for failure from verify
    })
);
```
* OAuth 1.0a and OAuth 2.0:

Facebook's type is "facebook"

```js
// This is the route the user hits
app.get("/auth/provider", passport.authenticate("provider"));
// In 2.0, you can also add scopes to the request
app.get("/auth/provider", passport.authenticate("provider", {scope: ["email"]}));

// This is the route the provider hits
app.get("/auth/provider/callback", passport.authenticate("provider", {
    successRedirect: "/",
    failureRedirect: "/login"
}));
```

## Session Serialization

```js
passport.serializeUser((user, next) => {
    next(null, user.id);
});
passport.deserializeUser((id, next) => {
    next(null, findUserById(id));
});

const session = require("express-session");
app.use(session({
    cookie: {
        //secure: true
    },
    resave: false,
    saveUnitialized: false,
    secret: "SECRET CODE HERE"
}));
app.use(passport.session());
```

## OAuth Profile Normalization

User profiles from OAuth get normalized to this format:

```js
{
    provider: "facebook",
    id: "1",
    displayName: "kylecoberly",
    name: {
        familyName: "Coberly",
        givenName: "Kyle",
        middleName: "Eldon"
    },
    email: [{
        value: "kyle.coberly@gmail.com",
        type: "personal"
    }],
    photos: [{
        value: "imageurl.com"
    }]
}
```

## Logout

```js
router.get("/logout", (request, response) => {
    request.logout();
    request.redirect("/login");
});
```
