An **Oblivious PRF** extends the concept of a [[Pseudorandom Function (PRF)]] by adding a privacy feature. In an OPRF, one party (the client) wants to compute a PRF on some input with the help of another party (the server), but the client does not learn the server’s secret key, and the server does not learn the client’s input.

This is useful for privacy-preserving computations where neither party should fully know what the other is doing, but they need to collaborate to produce a useful result.

- **Example**: In password-hashing protocols, you could use an OPRF to ensure that a server can assist in hashing a password without ever knowing what the password is.

### How an Oblivious Pseudorandom Function (OPRF) Works

An **Oblivious Pseudorandom Function (OPRF)** is a cryptographic construction that allows two parties (typically, a **client** and a **server**) to jointly compute a PRF over some input, such that:

- The **client** gets the PRF result.
- The **server** doesn't learn the client’s input (message).
- The **client** doesn't learn the server’s secret key.

#### Basic Idea of OPRF:

1. **Client Input**: The client has a message mmm and wants to compute Fk(m)F_k(m)Fk​(m), where FkF_kFk​ is a pseudorandom function keyed with the server’s secret key kkk.
2. **Blind Input**: The client "blinds" the input message using some cryptographic operation so that the server can’t learn the true input. For example, the client might multiply mmm by a blinding factor bbb to get m′m'm′, where m′=b⋅mm' = b \cdot mm′=b⋅m.
3. **Server Evaluation**: The client sends the blinded input m′m'm′ to the server. The server computes the PRF Fk(m′)F_k(m')Fk​(m′) over the blinded message without knowing what the original input mmm is, because mmm is hidden by bbb.
4. **Unblinding**: The server returns the result Fk(m′)F_k(m')Fk​(m′) to the client. The client then removes the blinding factor (essentially divides by bbb) to recover Fk(m)F_k(m)Fk​(m). Now, the client knows the PRF output for mmm, but the server never learned mmm, and the client never learned kkk.

#### Security:

- The **server** doesn’t know the client’s input because it only sees the blinded input m′m'm′.
- The **client** doesn’t know the server’s secret key kkk, so it can't compute FkF_kFk​ on its own.