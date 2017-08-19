## Notes

* Any encryption can be broken- goal is to make it not worth it to an attacker
* Unencrypted version is called "plaintext", encrypted version is "ciphertext"
* Kerckhoff's principle- "The security of data should not depend on the method of encryption remaining a secret"

## Methods

### Transposition

* Same data, different order
* "Every third letter" - `123 456 789` becomes `147 258 369`
* Easy to encode and reverse
* Easily leaked

#### Cipher Keys

* Uses transposition, but has a secret number that determines what order things are moved in
* Message is `123 456 789`, secret is `321` - ciphertext is `356 924 712`
    * Start on the 3rd character, then count 2, then count 1
    * Continue from where you stopped, skip any characters you've already accounted for

### Substition

* Replacing data
* Resistant to cribs
* Simple substitution replaces one character for another
    * Makes it vulnerable to frequency analysis
    * Makes your encryption weaker the longer the message is
* Cipher key is a character map

### Polyalphabetic Substitution

* First `E` is replaced with an `A`, second `E` is replaced with a T, etc.
* _Tabula recta_ is a grid of alphabets:

```
    A B C D E F
  -------------
A | A B C D E F
B | B C D E F A
C | C D E F A B
D | D E F A B C
E | E F A B C D
F | F A B C D E
```

* If plaintext is `ABC` and the encryption key is `DEF`:
    * Row is plaintext, column is encryption key, intersection is cipher text
    * `A x D` = `D`
    * `B x E` = `F`
    * `C x F` = `B`
    * Ciphertext is `DFB`
    * To decrypt: Column is encryption key, intersection is cipher, row is plaintext
        * `D - D` = `A`
        * `F - E` = `B`
        * `B - F` = `C`
* To prevent frequency analysis, key needs to be as long as plaintext

## Key expansion

* Use a short key as a pointer to a location in a longer code book
* `2.2.3.4` -> Second Shakespeare play, 2nd act, 3rd scene, 4th sentence

## S-Box Table

* "Substitution Box"
* Maps each possible byte to another byte
* Designed to amplify small differences

## AES

* Advanced Encryption Standard
* AES is _symmetric_ - the same key needs to be used to encrypt and decrypt data
* Encryption keys in AES are binary numbers (often 128 bits)
    * Key expansions (by `XOR`ing bytes and using S-Boxes) creates 10 more keys
* Split the data into the same number of bits as the key
    * 128-bit key would have a 4x4 grid of bytes
* `XOR` the data with the original encryption key
* Encrypt the data in 10 rounds:
    * Subsitute each byte with its replacement byte from the S-Box table
    * Transpose bytes within their rows in the grid
    * Recalculate each byte by bitwise-rotating two bytes in their column and `XOR`ing them together
    * `XOR` the entire grid with the encryption key for that round that was generated with key expansion
* Different 16-byte blocks are block chained
* AES is secure because the value of any individual byte is influenced by the values of every other byte (this is called diffusion), and blockchaining further amplifies the diffusion across all the data

## Block chaining

* To prevent frequency analysis, different blocks of identical plaintext bytes produce different ciphertexts
* The first block is `XOR`ed with a random 128-bit number ("starting variable), which is stored along with the ciphertext
* Each previous ciphertext block is `XOR`ed with the next plaintext block before encryption, ensuring that two identical blocks will produce different ciphertexts

## Bitwise Operators

* `XOR` - `1`s in the second number flip the value of numbers in the first value
    * `1001` XOR `1100` results in `0101`
    * Can't predict what the original number is, but it reverses to the same number

## Attacks

* Brute force
* Cribs - Guesses about the plaintext content
* Known Plaintext Attack
    * Needs plaintext A, ciphertext A, and ciphertext B that was encrypted in the same way
    * Makes it easy to find a transposition pattern
