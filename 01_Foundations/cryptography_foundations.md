# Foundations of Cryptography

### Plaintext
* **Definition:** The original, unencrypted message or data that is readable and understandable.
* **Example:** A password in cleartext (`"my_secret_password123"`), a bank account number, or a standard text message.
* **Context:** This is the input to an encryption algorithm and the output of a decryption algorithm.

### Ciphertext
* **Definition:** The scrambled, unreadable data produced by applying an encryption algorithm to plaintext.
* **Example:** `7b9e2a1c4f8d...`
* **Context:** It is designed to look like random noise to anyone who intercepts it, ensuring confidentiality during transmission or storage.

### Encryption
* **Definition:** The process of converting plaintext into ciphertext using a specific mathematical algorithm and a key.
* **Mathematical Representation:** $$	ext{Ciphertext} = E(K, 	ext{Plaintext})$$
  *(Where $E$ = Encryption Function, $K$ = Key)*
* **Purpose:** Ensures confidentiality so unauthorized parties cannot understand the data.

### Decryption
* **Definition:** The reverse of encryption; the process of converting ciphertext back into readable plaintext using a specific algorithm and a key.
* **Mathematical Representation:** $$	ext{Plaintext} = D(K, 	ext{Ciphertext})$$
  *(Where $D$ = Decryption Function)*
* **Purpose:** Allows authorized recipients who possess the correct key to read the original message.

---

## The Core Mechanisms

### Key
* **Definition:** A piece of information (typically a long string of random bits) that determines the functional output of a cryptographic algorithm.
* **Analogy:** If the encryption algorithm is a physical deadbolt lock, the key is the actual physical key that turns it.
* **Types:**
  * **Symmetric Key:** The *same* key is used for both encryption and decryption (e.g., AES). Fast, but key distribution is difficult.
  * **Asymmetric Key (Public/Private):** A pair of keys is used. Data encrypted with the Public Key can only be decrypted by the corresponding Private Key (e.g., RSA, ECC).

![Symmetric vs Asymmetric Encryption](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Symmetric_asymmetric_encryption.svg/640px-Symmetric_asymmetric_encryption.svg.png)

### Brute Force
* **Definition:** A cryptographic attack method where an attacker tries every possible key combination until the correct one is found.
* **Vulnerability Factor:** The success of a brute-force attack depends entirely on the size of the key space.
  * A 56-bit key (DES) can be cracked in hours today.
  * An AES-128 bit key has $2^{128}$ combinations, making it computationally impossible to brute-force with current technology.

### Entropy
* **Definition:** A measure of randomness, unpredictability, or uncertainty in a system, particularly regarding key generation or passwords.
* **Role in Cryptography:** High entropy means a key or password is truly random and unpredictable, making it highly resistant to guessing or brute-force attacks.
* **Example:** * `Password123` has **low entropy** (predictable pattern).
  * `fX9!mQ2@zP9L` has **high entropy** (unpredictable and random).
