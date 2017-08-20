* When communicating over the internet, remember that you're not communicating directly. You have to go through your router, ISP, the person you're communicating with's ISP, and possibly a variety of third parties. If one of those systems is compromised, you are subject to a man-in-the-middle attack.

## Handshaking

1. The client tells the server which encryption methods it supports, and gives the server a randomly generated number
1. The server responds with the list of encryption methods it supports, as well as its certificate, and a random number of its own
    * A certificate has the server's domain, the certificate issuer (who will verify the authenticity of the server), the server's public key, and a signature
        * The signature is a hash of all of the certificate's data encrypted with their private key
    * Servers use the same public/private key pair for all clients, so these keys only get used during the handshake
1. The client validates the certificate
    1. It applies the public key to the signature in the certificate to get its signature, and then hashes the certificate, and verifies that they're the same- this verifies the integrity of the certificate
    1. The browser verifies the certificate with an issuer, or "Trusted root certification authority." The issuer provides a copy of the site's certificate, which should match.
1. The client generates another 48-byte random number, called a "Premaster secret." It encrypts this with the server's public key, which it got from the certificate, and sends it to the server
1. The client and server independently create a 384-bit "master secret" by hashing the premaster secret and the 2 random numbers that were generated earlier. At this point, the random numbers and premaster secret are discarded.

## Transmitting Data With HTTPS

* The 384-bit master secret are split into 3 128-bit sections:
    1. An encryption key for something like AES
    1. A starting value for a blockchain (to prevent headers from getting cribbed)
    1. A Message Authentication Code (MAC), which ensures data wasn't altered during transmission. It's added to the end of the transmission, before encryption.
