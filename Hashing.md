* Hashing- Transforming something into a number in a specified range
* Hash/Hash Code/Hash Value- The result of hashing

## Hash Functions

A hash function is a process for hashing something. Hashing a string always begins with turning the characters in the string into binary with something like ASCII. Good hash functions:

* Make full use of all available bits
* Are not reversible- There should be no direct way to recover a password from a hash
    * More than one passowrd can produce the same hash, which is called a collision
* Avalanche- Small changes should turn into big changes

## MD5

* Converts a string to a 512-bit block
    * First part of the block is the ASCII codes of the string
    * The last 64 bits store a binary representation of the length (in bits) of the original string
    * Middle part of the block starts with a `1` followed by all `0`s
* Starts with a standard pattern of 128 bits:

```
A | 01100111 01000101 00100011 00000001
B | 11101111 11001101 10101011 10001001
C | 10011000 10111010 11011100 11111110
D | 00010000 00110010 01010100 01110110
```

* The pattern is then hashed 64 times
    * 3 of the sections are transposed
    * A new section is created each time by using all 4 sections and a row of the encoded string with the irreversible `AND`, `OR`, and `NOT` operators
* Due to the number of irreversible operations, the resulting hash cannot be reversed into the password
* If the string is longer than 512 bits, it's split into multiple MD5 hashes. Similar to a block chain, each resulting hash is used as the basis for the next block.
    * This results in a 128-bit "digital signature" that can be used to verify any file

## Bitwise Operations Used In Hashing

* Binary Addition- Sums values of two binary numbers
* Bitwise `NOT`- Flips all the bits
* Bitwise `OR`- Results in a `1` if there's a `1` in the  same position of the first or second number. Not reversible like `XOR`.
* Bitwise `AND`- Results in a `1` if there's a `1` in the same position of both numbers. Not reversible.

## Passwords

* Store the hash of a password, not the password itself
* Use one hash function to hash the password for authentication, and another hash function to hash the password into an encryption key to encrypt the username and any other sensitive details
* Salt
    * Randomly generated
    * Stored with the password
    * Appended to the end of the password before hashing
    * Makes it harder to attack, because hash tables won't match, and every user's salt is different

## Attacks

 Hashes can themselves be hashed (hash-chaining, or iterative hashing) to decrease the likelihood of an attack matching. This trades increased security for decreased speed.

* Collision Attack- When someone intentionally tries to produce a malicious version of something with the same digital signature
* Basic Dictionary Attack- When someone tries a list of common passwords. Protect against by timing out after a certain number of failed attempts.
* Advanced Dictionary Attack- When someone has a bunch of hashed passwords, and compares them against the hashes from a dictionary
* Hash Tables- A precomputed list of what a wide variety of automatically generated passwords hash into to compare against a stolen list of hashed credentials. A table with all `[A-Z0-9]` 10-digit passwords would be 62^10, which would be require a million hard drives.
* Hash Chains- Making a hash table smaller by breaking it into collections of single hashes that can be "reduced" (back to password) and rehashed to be able to calculate lots more potential matches for a particular hash.
