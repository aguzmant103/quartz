A **Verifiable OPRF** adds verifiability to the [[Oblivious Pseudorandom Function (OPRF)]]. This means that not only does the server help compute the PRF in an oblivious way (without learning the client’s input), but the client can also verify that the server executed the protocol correctly without tampering with the result.

This verifiability is crucial in certain cryptographic protocols where you want to ensure that the server cannot cheat. The client can confirm that the computed PRF value is correct according to the server’s key without needing to know that key.

### How Verifiable Oblivious Pseudorandom Function (VOPRF) Works

#### How the Client Verifies in VOPRF:

1. **Client Input**: Like in an OPRF, the client blinds the input and sends it to the server.
2. **Server Evaluation**: The server computes the PRF over the blinded input and returns the result to the client. However, in a VOPRF, the server also produces a **proof** that it computed the PRF correctly. This proof is generated using cryptographic techniques like zero-knowledge proofs or signatures.
3. **Verification**: The client checks the proof using a **verification algorithm**. This algorithm takes the proof, the PRF output, and the server’s public key as inputs. If the proof is valid, it guarantees that the server used the correct key k and followed the protocol without tampering with the result.
    - The proof ensures that the server didn't cheat (e.g., by returning an incorrect PRF value or manipulating the input).
4. **Unblinding**: After verifying the correctness of the server’s computation, the client removes the blinding factor to recover the correct PRF value Fk(m).

#### Verifiability in VOPRF:

- The server provides a **cryptographic proof** that guarantees the PRF was computed honestly and with the correct key.
- The client uses the **server’s public key** to verify the proof, ensuring the result is correct even if the client cannot see the server’s secret key.

### Example Applications:

- **Password authentication**: The client can compute the PRF on a password, and the server helps without learning the password itself.
- **Anonymous tokens**: Clients can receive verifiable PRF outputs from the server, ensuring the result is correct while preserving privacy.

In summary:

- In an **OPRF**, the server computes the PRF without learning the client’s input, and the client doesn’t know the server’s secret key.
- In a **VOPRF**, the server additionally provides a proof that allows the client to verify the correctness of the server's computation, ensuring no tampering or malicious behavior from the server.