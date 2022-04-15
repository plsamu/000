# Theory

## Cryptography Systems Caption

### Generalistic names

#### Systems

*   **Public-key cryptography**, or **asymmetric cryptography**

    Is a cryptographic system that uses pairs of keys. Each pair consists of a _public key_ and a _private key_.

    E.g.

    * RSA**asymmetric cryptography**
    * ECC
    * ECDSA
    * ECDH
*   **Symmetric-key algorithms**

    Are algorithms for cryptography that use the same cryptographic keys for both the encryption of plaintext and the decryption of ciphertext. The keys may be identical, or there may be a simple transformation to go between the two keys.

    E.g.

    * AES
    * R5

#### Signature Schemes Family

*   **ECDSA**: _Elliptic Curve Digital Signature Algorithm (aka EC version of DSA)_

    Is a family of signature algorithms that can be used to sign a piece of data in such a way, that any change to the data would cause signature validation to fail: an attacker would not be able to correctly re-sign data after such a change. Also ECDSA only describes a method which can be used with different elliptic curves.
* **ECPVS**

#### Key exchange Schemes Family

*   **ECDH:** _Elliptic-curve Diffie–Hellman (aka EC version of DH)_

    Is a family of key exchange methods that two parties can use to negotiate a secure key over an insecure communication channel. Yet ECDH is just a method, that means you can use it with many different elliptic curves.

### Specific names

#### Signature Algorithm

*   **Ed25519**

    Is a specific type of ECDSA (or also EdDSA) that uses _SHA-512 + Curve25519 ._

    > The ECDSA family of signature schemes is related to EdDSA only because the mathematics behind it also involves elliptic curves. Any particular instance of ECDSA, such as ECDSA over the curve secp256k1 with SHA-256 (as Bitcoin uses), is incompatible with any other instance of it, such as ECDSA over the curve nistp521 with SHA-512. [source](https://crypto.stackexchange.com/questions/58380/ecdsa-eddsa-and-ed25519-relationship-compatibility)

## ECC Encryption / Decryption

[ECC Encryption / Decryption](https://cryptobook.nakov.com/asymmetric-key-ciphers/ecc-encryption-decryption)
