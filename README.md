# Secure Multiparty Computation for Privacy in Practice

Secure Multiparty Computation (SMC) is a cryptographic protocol that distributes computation across multiple parties, ensuring that no participant learns anything about the others' data except the final result. This paper focuses on different protocols for Private Set Intersection (PSI), which is the problem of computing the intersection of data sets managed by different organizations while keeping the data private.

## 1. Set Intersection Protocols

### 1.1 Naive Hash Protocol

The Naive Hash protocol uses cryptographic hash functions (e.g., SHA256, SHA3) to compute intersections. Each organization hashes their data and compares the hashes to find common elements. This method scales well but is insecure if the data is predictable, making it vulnerable to brute-force attacks.

### 1.2 Server-Aided Protocol

This protocol uses an untrusted server to aid in computing intersections:

1. Participants agree on a secret key `K` for a pseudo-random permutation `F`.
2. Each participant permutes their data using `F` and sends it to the server.
3. The server computes the intersection and returns it.

Security relies on the server being semi-honest and the participants being honest. The efficiency comes from minimizing cryptographic operations.

### 1.3 Diffie-Hellman Protocol

This protocol allows users to verify if they have matching credentials without revealing them:

1. Users A and B each have a secret and public number.
2. They exchange encrypted values based on their secrets.
3. They verify if their secrets match by checking the received values.

Security is based on hard problems like discrete logarithms. While it’s secure, it requires significant computation and communication overhead.

### 1.4 Oblivious Transfer (OT) Protocol

The OT protocol involves sending one of multiple messages to a receiver without knowing which one was received:

1. The sender generates two messages and random values.
2. The receiver chooses a message and sends a value derived from their choice.
3. The sender uses this value to create a response, allowing the receiver to get only the chosen message.

OT can be extended to multiple messages (1-out-of-N OT) and is used in more advanced PSI protocols.

## 2. Application and Testing of Protocols

### 2.1 Naive Hashing Security Issues

Naive Hashing is efficient but insecure against attacks if the data is predictable. It also suffers from high collision rates due to reduced hash output size.

### 2.2 Server-Aided Protocol Privacy Concerns

While this protocol scales well, using hash values rather than pseudo-random permutations can lead to similar privacy issues as Naive Hashing.

### 2.3 Diffie-Hellman Performance

Diffie-Hellman provides strong security but has high communication and computation overhead compared to other protocols.

### 2.4 OT-Based Protocol

OT-based protocols offer robust security but have higher communication costs. They are effective in protecting against attacks but involve larger data transfers.

## 3. Performance Analysis and Benchmarking

Testing showed that:

- **Naive Hashing**: Low communication overhead but vulnerable.
- **Server-Aided**: Slightly higher overhead but similar issues to Naive Hashing.
- **Diffie-Hellman**: High overhead with excellent security.
- **OT-Based**: Highest overhead but strongest security.

### Table: Packet and Byte Counts

| Protocol          | Total Packets | Total Bytes |
|-------------------|---------------|-------------|
| Naive Hashing     | 28            | 2408        |
| Server-Aided      | 32            | 3330        |
| Diffie-Hellman    | 30            | 5852        |
| OT Based          | 37            | 55072       |

## 4. PSI on Password Datasets

Testing on password datasets showed that:

- **OT-Based**: Offers the best security despite high communication costs.
- **Naive Hashing and Server-Aided**: Faster but less secure.
- **Diffie-Hellman**: Secure but slower.

