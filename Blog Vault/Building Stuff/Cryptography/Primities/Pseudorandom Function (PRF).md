A **Pseudorandom Function** is a function that takes an input (often a key and a message) and produces an output that is indistinguishable from a truly random function to any observer who does not know the key. Essentially, given a secret key, the output should look random, but the function is deterministic and can be replicated if the same key and input are used again.

When [[Hash Function]] are paired with a key, they can be used as a PRF. For example:

- **HMAC (Hash-based Message Authentication Code)**: This uses a cryptographic hash function (e.g., SHA-256) along with a secret key to generate a keyed hash, which behaves like a PRF.
- **HKDF (HMAC-based Key Derivation Function)**: Uses HMAC as a PRF to derive multiple keys from a single shared secret.
- **CMAC (Cipher-based MAC)**: Another construction that can turn a block cipher like AES into a PRF.
- BLAKE