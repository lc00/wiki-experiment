## Notes

* Used for authentication, as well as secure data exchange
* Super compact, so it can be used in urls, headers, etc.
* Stateless, so works well with RESTful APIs

## Structure

The structure of a JWT is `header.payload.signature`.

### Header

The header has two parts- the type of token (`JWT`) and the hashing algorithm (either RSA or SHA256). This is `Base64Encoded` into the first part of the signature.

```json
{
    "alg": "HS256",
    "typ": "JWT"
}
```

### Payload

This contains a set of "claims" about a user, which are `Base64Encoded` into the second part of the signature. There are three types of claims:

* Reserved Claims (Standard):
    * `iss`: Issuer
    * `exp`: Expiration
    * `sub`: Subject
    * `aud`: Audience
* Public Claims (User-defined, but should be registered)
* Private Claims (Defined between parties using them)

```json
{
    "sub": "1234567890",
    "name": "Kyle Coberly",
    "admin": true
}
```

### Signature

Using the algorithm specified in the header, hash the encoded `header.payload` with your secret.

### Use in Authentication

* JWT is returned from the server, stored in local storage or cookie, and sent in the authorization header on each request: `Authorization: Bearer 1234.zxcv.asdf`
