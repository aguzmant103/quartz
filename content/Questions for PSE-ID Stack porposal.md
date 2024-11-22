- Creates nullifiers for every web2 identity using TLSNotary and zkEMAIL
- Uses vOPRF to generate deterministic yet unknown salts
- It's done trough MPC salting which nobody can know

Questions:
- How is it deterministic?
- How come nobody can claim my username and register if my username is public?
- In Semaphore you typically have a private key. How do you generate a private key that only the user can claim it?
- 

Benefits:
- Ability to create secure nullifiers without the issuer knowning mine
- Also creating a big group anonymous group that is opt-out (permissionlessly instead of Semaphore)
