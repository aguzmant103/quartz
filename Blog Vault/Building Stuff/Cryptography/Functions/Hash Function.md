- **Hash Functions (e.g., SHA-256, BLAKE2)**:
    
    - **Input**: Variable-length message.
    - **Output**: A fixed-length hash.
    - **Key**: No key involved in basic hash functions.
    - **Properties**: Collision resistance, preimage resistance, and second preimage resistance.
    - **Usage**: Often used for integrity checks, digital signatures, and storing passwords.
- **PRFs**:
    
    - **Input**: Secret key and a message.
    - **Output**: A value that is computationally indistinguishable from random for anyone who does not know the secret key.
    - **Key**: Yes, the output depends on the secret key.
    - **Usage**: Used for key derivation, encryption, authentication (like HMAC), and in various cryptographic protocols.