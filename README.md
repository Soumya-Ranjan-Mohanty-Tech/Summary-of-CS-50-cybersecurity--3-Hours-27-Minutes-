# Summary-of-CS-50-cybersecurity--3-Hours-27-Minutes-

# CS50 Intro to Cybersecurity 

---

# MODULE 1 — Foundations of Cybersecurity

Cryptography is the science of protecting information by converting readable data (plaintext) into unreadable data (ciphertext) so that only authorized parties can access it.

The three primary goals are:

Confidentiality: Prevent unauthorized people from reading data.
Integrity: Ensure data has not been modified.
Authentication: Verify the identity of the sender.

Cybersecurity is broadly about:

* Securing accounts
* Securing data
* Securing systems
* Preserving privacy
* Preventing unauthorized access

The entire field revolves around 3 big questions:

```
1. Who are you?
2. Should you have access?
3. How do we protect the data?
```

---

# MODULE 2 — Authentication and Authorization

---

# 2.1 Authentication

## Definition

Authentication means:

```
Proving who you are digitally.
```

The system asks:

```
"Are you really the owner of this account?"
```

Examples:

* Username + Password
* Fingerprint
* Face ID
* Passkey
* OTP

---

# 2.2 Authorization

## Definition

Authorization means:

```
Determining what an authenticated user is allowed to access.
```

Example:

```
You successfully log into a company account
(Authentication)

But you may not have permission to access payroll files
(Authorization)
```

---

# 2.3 Username

A username is:

* a digital identity,
* usually unique,
* used to identify users.

Example:

```text
soumya123
```

---

# 2.4 Password

A password is:

* a secret memorized string,
* used to prove identity.

Good passwords should be:

* long,
* random,
* unique.

---


---


# What is a Hash Function?

A hash function converts data of any size into a fixed-size output called a hash (digest).

**Example**
Message:
"Hello"

SHA-256 Output:
185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969

**Important Properties**
Same input → same output
Tiny change in input → completely different hash
Fast to compute
One-way function
Fixed-length output

**Common Hash Algorithms**
SHA-256
SHA-384
SHA-512

---

---
# SYMMETRIC ENCRYPTION

Definition:
The same key is used for:

Encryption
Decryption
Example

**AES = Advanced Encryption Standard**
Plaintext
   ↓
AES + Key
   ↓
Ciphertext
**Receiver**
Ciphertext
   ↓
AES + Same Key
   ↓
Plaintext
**Advantages**
Very fast
Efficient
**Disadvantage**
Both parties must somehow obtain the same secret key.

---

---

# ASYMMETRIC (PUBLIC KEY) CRYPTOGRAPHY

Definition:
Uses two mathematically related keys:

Public Key: Can be shared with everyone.

Private Key: Must remain secret.

**Encryption Process**
Message
   ↓
Encrypt with Public Key
   ↓
Ciphertext
Only corresponding Private Key can decrypt.

**Main Algorithms**

RSA = Rivest Shamir Adleman
ECC = Elliptic Curve Cryptography
DSA = Digital Signature Algorithm
ECDSA = Elliptic Curve Digital Signature Algorithm

---

---

# DIFFIE–HELLMAN KEY EXCHANGE
**What is Diffie-Hellman?**

Diffie-Hellman (DH) is:

**NOT**

An encryption algorithm.

**IS**

A Key Exchange Algorithm.
Its purpose is to create a shared secret over an insecure network.

**Public Values**

Both parties agree on:

**Generator**
g

Example:

g = 2

**Prime Number**
p

A very large prime.

**Alice**
Private Key:
a

Public Key:
A = g^a mod p

**Bob**
Private Key:
b

Public Key:
B = g^b mod p

**Exchange**

Alice sends:
A

Bob sends:
B

**Shared Secret**

Alice computes:

S(A) = B^a mod p

Bob computes:

S(B) = A^b mod p

Result:

S = g^(ab) mod p

Since:

ab = ba

Both obtain the same secret.

**Why Important?**

Neither side transmitted:
a
or
b

Only public values were exchanged.


---

---

# KEY DERIVATION FUNCTIONS (KDF)

**Problem**
Raw secret:
S
may contain mathematical structure.

**Solution**
Feed S into a Key Derivation Function.
**Examples**
HKDF = HMAC-based Key Derivation Function
SHA-256

**Output**
A strong symmetric key.
Example:
256-bit AES Key

**Why HKDF is Preferred**
**Extract Phase**
Removes patterns.
**Expand Phase**
Produces exact key length.

**Example:**
AES-128
AES-256


---

---

# USING AES AFTER DIFFIE-HELLMAN

**Process:**
DH Shared Secret
      ↓
HKDF
      ↓
AES Key
      ↓
Encrypt Messages

After the handshake, all communication is performed using AES.


---

---






---

---
# MODULE 3 — Password Attacks

Attackers try to discover passwords.


# 3.1 Dictionary Attack

## Definition

A dictionary attack means:

```
Trying common words from a predefined list.
```

Attackers use files containing:

* English words,
* common passwords,
* leaked passwords,
* predictable patterns.

Examples:

```
password
india123
football
qwerty
welcome
```

Why effective?

Because humans choose predictable passwords.

---

# 3.2 Brute Force Attack

## Definition

A brute force attack means:

```
Trying every possible password combination systematically.
```

Instead of guessing likely passwords,
the attacker tests ALL possibilities.

---

## Example: 4-digit PIN

Possible values:

```text
0000 → 9999
```

Total:

10^4 = 10000

Modern computers can test thousands or millions of combinations per second.

---

# 3.3 Why Longer Passwords Matter

If password length increases:

```
Search space increases exponentially.
```

Example:

Digits only:

```
10 possibilities per position
```

Letters:

```
52 possibilities
```

Letters + digits + symbols:

```
90+ possibilities
```

Longer passwords become dramatically harder to brute force.

---

# MODULE 4 — Password Cracking Demonstrations

Python programs can automate brute forcing.

---

# 4.1 Digits Only

```python id="mbofro"
from string import digits

for i in digits:
    for j in digits:
        for k in digits:
            for l in digits:
                print(i, j, k, l)
```

---

## Explanation

### `from string import digits`

Imports:

```text
0123456789
```

---

## Nested Loops

Each loop iterates through every digit.

Example:

```text
i → first digit
j → second digit
k → third digit
l → fourth digit
```

The program generates:

```text
0000
0001
0002
...
9999
```

---

# 4.2 ASCII Letters

ASCII = American Standard Code for Information Interchange.

It is a character encoding standard.

```python id="5i4e0p"
from string import ascii_letters
```

Includes:

* uppercase letters,
* lowercase letters.

---

# 4.3 Letters + Digits + Symbols

```python id="l3qh8g"
from string import ascii_letters, digits, punctuation
```

This massively increases possible combinations.

---

# MODULE 5 — NIST Password Guidelines

NIST =
National Institute of Standards and Technology

NIST publishes cybersecurity standards.

---

# 5.1 Password Length

Minimum:

```
8 characters
```

Recommended:

```
Allow at least 64 characters
```

Longer passwords are harder to brute force.

---

# 5.2 Allowed Characters

Accept:

* letters,
* numbers,
* symbols,
* spaces,
* Unicode.

---

# 5.3 Unicode

Unicode allows characters from all languages.

Examples:

```text
नमस्ते
你好
😊
```

---

# 5.4 Block Weak Passwords

Reject:

* common passwords,
* leaked passwords,
* repetitive passwords,
* sequential passwords.

Examples:

```text
123456
password
abcdef
```

---

# 5.5 Avoid Context-Specific Passwords

Do NOT use:

* website name,
* username,
* personal information.

Bad example:

```text
gmail123
```

---

# 5.6 Password Hints

Avoid security questions.

Examples:

```text
First pet?
Mother's maiden name?
```

Attackers may discover answers online.

---

# 5.7 Password Rotation

NIST says:

```
Do not force arbitrary password changes.
```

Because users create weaker patterns like:

```
Password1
Password2
Password3
```

---

# 5.8 Rate Limiting

Rate limiting means:

```
Limiting login attempts.
```

Example:

```
5 failed logins
→ temporary lockout
```

This slows brute force attacks.

---

# MODULE 6 — Multi-Factor Authentication (MFA)

MFA =

```
Multi-Factor Authentication
```

Also called:

```
2FA = Two-Factor Authentication
```

---

# 6.1 Knowledge Factor

Something you KNOW.

Examples:

* Password
* PIN

---

# 6.2 Possession Factor

Something you HAVE.

Examples:

* Phone
* Security key
* [Authenticator app]

---

# 6.3 Inherence Factor

Something you ARE.

Examples:

* Fingerprint
* Face
* Iris

These are biometrics.

---

# 6.4 OTP

OTP =

```
One-Time Password
```

Temporary login code.

Example:

```
682193
```

---

# 6.5 SIM Swapping

SIM =

```
Subscriber Identity Module
```

Attack:

* attacker impersonates victim,
* telecom provider transfers phone number,
* attacker receives OTPs.

Therefore:

Prefer:

* authenticator apps,
* security keys,

instead of SMS OTP.

---

# MODULE 7 — Malware

Malware =

```
Malicious Software
```

Examples:

* Virus
* Worm
* Trojan
* Spyware

---

# 7.1 Keylogger

A keylogger records:

* keystrokes,
* passwords,
* messages,
* sensitive information.

Even strong passwords fail if malware captures them.

---

# MODULE 8 — Credential Stuffing

Credential =

```
Login information
```

Usually:

* username,
* password.

---

# 8.1 Credential Stuffing Attack

Attackers use leaked credentials from one website on another website.

Because many users reuse passwords.

Defense:

* unique passwords,
* password managers,
* MFA.

---

# MODULE 9 — Social Engineering and Phishing

---

# 9.1 Social Engineering

Manipulating humans instead of hacking computers.

Examples:

* pretending to be support staff,
* pretending to be a bank,
* creating urgency.

---

# 9.2 Phishing

Phishing =

```
Fake communications designed to steal information.
```

Examples:

* fake email,
* fake login page,
* fake SMS.

Always verify:

* URL,
* domain name,
* HTTPS.

---

# MODULE 10 — Password Managers

Password managers:

* generate passwords,
* store passwords securely,
* autofill credentials.

Examples:

* Apple iCloud Keychain
* Google Password Manager
* Microsoft Credential Manager

Benefits:

* strong passwords,
* unique passwords,
* prevents reuse.

---

# MODULE 11 — Hash Functions

Hash function =

```
Mathematical function converting arbitrary-length input into fixed-length output.
```

Example:

```
apple
↓
hash
```

---

# 11.1 Important Properties

---

## Fixed-Length Output

Small input:

```
cat
```

Large input:

```
Entire book
```

Both produce fixed-length hashes.

---

## One-Way Function

Easy:

```
Input → Hash
```

Hard:

```
Hash → Original input
```

Therefore hashes are not encryption.

---

# MODULE 12 — Password Storage

Websites should NOT store plaintext passwords.

Instead:

```
Password
↓
Hash Function
↓
Hash stored in database
```

---

# Login Process

User enters password:

```
Entered password
↓
Hash generated
↓
Compare hashes
```

If hashes match:

```
Authentication successful
```

---

# MODULE 13 — Hash Attacks

---

# 13.1 Dictionary Attack Against Hashes

Attackers:

* hash common words,
* compare hashes with stolen database.

---

# 13.2 Brute Force Against Hashes

Try:

* numbers,
* letters,
* symbols.

Hash each candidate and compare.

---

# 13.3 Rainbow Table

Rainbow table =

```
Precomputed password-to-hash database.
```

Example:

```
password → hash
banana → hash
```

Speeds up cracking.

---

# MODULE 14 — Salting

Salt =

```
Random value added before hashing.
```

Example:

```
password + salt
↓
hash
```

---

# Why Salting Matters

Without salt:

* identical passwords produce identical hashes.

With salt:

* hashes become unique.

Benefits:

* defeats rainbow tables,
* slows mass attacks.

---

# MODULE 15 — Cryptography

Cryptography =

```
Science of protecting information using mathematics.
```

Goals:

* confidentiality: Ensure no unauthorised persons intersept the password
* integrity: Ensure data in tansit is not modified
* authentication: Identify right sender
* non-repudiation.

---

# MODULE 16 — Codes vs Ciphers

---

# 16.1 Codes

Replace words/phrases with other words.

Require:

```
Codebook
```

---

# 16.2 Ciphers

Algorithmically transform letters/bits.

Modern cryptography uses ciphers.

---

# MODULE 17 — Encryption and Decryption

Encryption:

```
Plaintext → Ciphertext
```

Decryption:

```
Ciphertext → Plaintext
```

---

# MODULE 18 — Keys

Key =

```
Secret value controlling cryptographic algorithm behavior.
```

Algorithms can be public.

Security depends on secrecy of keys.

---

# MODULE 19 — Symmetric Encryption

Same key used for:

* encryption,
* decryption.

Examples:

* AES
* Triple DES

AES =

```
Advanced Encryption Standard
```

DES =

```
Data Encryption Standard
```

---

# Problem of Symmetric Encryption

How do both parties securely share the key?

This leads to asymmetric cryptography.

---

# MODULE 20 — Asymmetric Cryptography

Also called:

```
Public Key Cryptography
```

Uses:

* Public Key
* Private Key

Public key:

```
Shared publicly
```

Private key:

```
Kept secret

Main Algorithms
RSA = Rivest Shamir Adleman
ECC = Elliptic Curve Cryptography
DSA = Digital Signature Algorithm
ECDSA = Elliptic Curve Digital Signature Algorithm


```

---

# MODULE 21 — RSA

RSA =
Rivest–Shamir–Adleman

Named after creators:

* Rivest,
* Shamir,
* Adleman.

---

# 21.1 RSA Key Generation

Choose prime numbers:

```
p
q
```

Compute:

n = p * q

Compute Euler's Totient:

\phi(n)=(p-1)(q-1)

Choose:

```
e
```

Compute:

```
d
```

Public key:

```
(n,e)
```

Private key:

```text
(n,d)
```

---

# 21.2 RSA Encryption

c = m^e \mod n

Where:

* m = message,
* e = public exponent,
* n = modulus,
* c = ciphertext.

---

# 21.3 RSA Decryption

m = c^d \mod n

Where:

* d = private exponent.

---

# MODULE 22 — Diffie-Hellman Key Exchange

Purpose:

```
Securely create shared secret over insecure network.
```
**DIFFIE–HELLMAN KEY EXCHANGE**
**What is Diffie-Hellman?**
Diffie-Hellman (DH) is:

**NOT**

An encryption algorithm.

**IS**

A Key Exchange Algorithm.

Its purpose is to create a shared secret over an insecure network.
---

# 22.1 Public Parameters

Shared publicly:

* g = generator,
* p = large prime.

---

# 22.2 Private Values

Alice chooses:

```
a
```

Bob chooses:

```
b
```

These remain secret.

---

# 22.3 Public Values

Alice computes:

A = g^a \mod p

Bob computes:

B = g^b \mod p

---

# 22.4 Shared Secret

Alice:

S = B^a \mod p

Bob:

S = A^b \mod p

Both compute same secret.

---

# MODULE 23 — Key Derivation Functions (KDF)

KDF =

```
Key Derivation Function
```

Purpose:

```
Convert shared secret into secure AES key.
```

Examples:

* HKDF
* SHA-256

HKDF =

```
HMAC-based Key Derivation Function
```

SHA =

```
Secure Hash Algorithm

**Example**
256-bit AES Key

[Why HKDF is Preferred]
**Extract Phase**
Removes patterns.
**Expand Phase**
Produces exact key length.

Example:

AES-128
AES-256


```

---
**USING AES AFTER DIFFIE-HELLMAN** 
DH Shared Secret
      ↓
HKDF
      ↓
AES Key
      ↓
Encrypt Messages

``
``
``

# MODULE 24 — Man-in-the-Middle Attack

MITM =

```
Man-in-the-Middle
```

Attacker secretly intercepts communication.

Can:

* read,
* alter,
* inject,
* forward traffic.

**Defense**:

* TLS,
* certificates,
* digital signatures.
* RSA
* ECDSA


---

# MODULE 25 — Perfect Forward Secrecy (PFS)

PFS =

```
Perfect Forward Secrecy: Compromise of today's keys must not reveal yesterday's communications.
```

Uses temporary session keys.

Even if long-term keys are stolen later:

```
Past sessions remain safe.
```

**Achieved Using**
**DHE**
Diffie-Hellman Ephemeral
**ECDHE**
Elliptic Curve Diffie-Hellman Ephemeral

**Process**
**Every session**:
New private keys
New shared secret
New AES key

**After session**:
Delete keys.

**Benefit**
Even if server private key is stolen later:
Past traffic remains secure.

---

# MODULE 26 — Digital Signatures

Purpose:

* authenticity,
* integrity,
* non-repudiation.

**Standard**: X.509

**Contains**:
Domain name
Public key
Validity period
Signature

---

# Signing Process

Document
↓
Hash
↓
Sign hash using private key
↓
Digital signature

---

# Verification

Recipient:

* hashes document,
* decrypts signature using public key,
* compares hashes.

If identical:

```
Signature valid
```

---

# CERTIFICATE AUTHORITIES (CA)

CA = Certificate Authority

**Examples**:
DigiCert
Let's Encrypt
GlobalSign
Function

Verify website identity.

Digitally sign certificates.

# MODULE 27 — TLS and HTTPS

TLS =

```
Transport Layer Security
```

SSL =

```
Secure Sockets Layer
```

SSL is older version of TLS.

HTTPS =

```
HyperText Transfer Protocol Secure
```

---

# TLS Purpose

Encrypt communication between:

```
Browser ⇄ Website
```
# WIRESHARK VIEW OF TLS
Wireshark

**Network protocol analyzer**.

Client Hello Contains: key_share
"Client public key".

Server Hello Contains:key_share
"Server public key".

Cipher Suite

Example:
TLS_AES_256_GCM_SHA384

**Meaning**:
AES-256 encryption
GCM = Galois Counter Mode
SHA-384 hashing
Application Data

After handshake:

All packets become encrypted.
---

# MODULE 28 — Certificates

Certificate =

```
Digitally signed public key document.
```

Contains:

* domain/website name,
* public key,
* expiration date,
* signature.

Standard:

```text
X.509
```

---

# MODULE 29 — Certificate Authorities (CA)

CA =

```
Certificate Authority
```

Trusted organizations that sign certificates.

Examples:

* DigiCert
* Let's Encrypt
* GlobalSign

**Function**

Verify website identity.
Digitally sign certificates.

Browsers trust CAs.

---

# Certificate Verification

Browser:

* downloads certificate,
* hashes certificate,
* verifies signature using CA public key.

If hashes match:

```
Certificate trusted.
```

---
**CERTIFICATE CHAIN**
Root CA
    ↓
Intermediate CA
    ↓
Website Certificate


``
``
``

# MODULE 30 — Passkeys and WebAuthn

WebAuthn =

```
Web Authentication
```

Passkeys replace passwords.

Uses:

* public/private key pairs,
* biometrics,
* challenge-response authentication.

---

# Login Process

Website sends challenge:

```
Random data
```

Device:

* signs challenge with private key.

Website:

* verifies using public key.

Benefits:

* phishing resistant,
* no passwords,
* no credential stuffing.
* Unique keys per website.

---

# MODULE 31 — Encryption in Transit

Protects moving data.

Examples:

```
Browser ⇄ Website
```

Uses:

* TLS,
* HTTPS.

**Examples**
TLS(Transport Layer Protocol)
HTTPS (Hyper text protocol secure)
WPA (WiFi Protected Access)

---

# 31.1 End-to-End Encryption

Only sender and receiver can read messages.

Examples:

* WhatsApp
* iMessage

Even service provider should not read messages.

---

# MODULE 32 — Encryption at Rest

Protects stored data.

Examples:

* SSD,
* HDD,
* phone storage.

---

# Full Disk Encryption (FDE)

Encrypts entire storage drive.

Examples:

* BitLocker (Windows)
* FileVault (macOS)


If device stolen:

```
Data remains unreadable.
```

---

# MODULE 33 — Secure Deletion

Deleting file normally:

```
Only removes reference.
```

Data may still exist.

Secure deletion:

```
Overwrite bits with new data.
```

---
# SSD FIRMWARE & BAD SECTORS

SSD firmware may lock damaged sectors.

If encryption enabled from Day 1:Old data remains encrypted.

If enabled later:Old unencrypted remnants may persist.

--
--
--

# MODULE 34 — Ransomware

Ransomware:

* encrypts victim files,
* demands payment.

Problem:
FDE(Full Disk Encryption) does NOT protect while device is unlocked.

**Important Distinction**
FDE Protects Against: Physical theft.
Ransomware Exploits: Logical access while device is unlocked.


---

# MODULE 35 — Backup Strategy

3-2-1-1-0 Rule:

* 3 copies,
* 2 media types,
* 1 offsite copy,
* 1 immutable copy,
* 0 restore errors.

Protects against ransomware.

---

# MODULE 36 — TPM and Secure Enclave

TPM =

```
Trusted Platform Module: Dedicated hardware security chip.
```

**Purpose**
Store encryption secrets securely.
Secure hardware chip storing encryption keys.

Apple equivalent:

```
Secure Enclave
```

---

# Measured Boot

System measures:

* BIOS,
* firmware,
* kernel.

**Boot Sequence**
Power On
 ↓
BIOS/UEFI
 ↓
Kernel
 ↓
TPM Verification
 ↓
Release Encryption Key
 ↓
Boot OS

**If altered**:

```
TPM refuses key release.
```
**PCR** Platform Configuration Registers.
Store measurements of system state.

If measurements change:TPM refuses key release.


---

# MODULE 37 — Wi-Fi Security

WPA =

```
Wi-Fi Protected Access
```

Versions:

* WPA
* WPA2
* WPA3

Encrypts:

```
Device ⇄ Router
```

---

# MODULE 38 — Packet Sniffing

Packet sniffing =

```
Capturing and analyzing network packets.
```

Packets contain:

* source IP,
* destination IP,
* protocol,
* payload.

Tools:

* Wireshark
* tcpdump
* 
**Malicious Uses**
Password theft
Cookie theft
Session hijacking


---

# MODULE 39 — Cookies and Sessions

**Cookie** =

```
Small data stored by browser.
```

Used to remember user sessions.

**Server sends**:

```
Set-Cookie
```

**Browser later sends**:

```
Cookie
```

**Example**
Server sends: Set-Cookie: session=1234abd
Browser later sends: Cookie: session=1234abd

**Risk**
Without HTTPS:Cookies can be stolen.
Leading to:Session Hijacking.


---

# Session Hijacking

Attacker steals session cookie.

Defense:

```
HTTPS
```

---

# MODULE 40 — Quantum Computing

Classical bit:

```
0 or 1
```

Quantum bit (qubit):

```
0 and 1 simultaneously
```

This is called:

```
Superposition
```
**State Explosion**

1 Qubit:2 states
2 Qubits:4 states
3 Qubits: 8 states
32 Qubits:~4 billion states

---

# MODULE 41 — Threat to Cryptography

Quantum computers running:
Shor's Algorithm: A quantum algorithm.

**can break**:

* RSA,
* Diffie-Hellman,
* ECC.

**By solving**:

Integer Factorization
Discrete Logarithms

efficiently.

ECC =

```
Elliptic Curve Cryptography
```

---

# MODULE 42 — Post-Quantum Cryptography (PQC)

PQC =

```
Post-Quantum Cryptography
```

Designed to resist quantum attacks.

NIST: National Institute of Standards and Technology------------- standardized new algorithms.

ML-KEM: Module-Lattice-Based Key Encapsulation Mechanism

Formerly:Kyber

---

# ML-KEM

ML-KEM =

```
Module-Lattice-Based Key Encapsulation Mechanism
```

Formerly:

```
Kyber
```

Used for:

```
Quantum-safe key exchange.
```

**Key Generation**
Alice creates: Public Key (pk), Private Key (sk)

**Encapsulation**
Bob:
Generates random symmetric key.
Encrypts it using pk.
Produces ciphertext: ct

**Decapsulation**
Alice: Uses sk.
Recovers same symmetric key.

**Underlying Mathematics**

MLWE: Module Learning With Errors.

**Uses**:
Lattices
High-dimensional geometry
Deliberate mathematical noise


---

# ML-DSA

ML-DSA =

```
Module-Lattice Digital Signature Algorithm
```

Formerly:

```
Dilithium
```

Quantum-safe digital signatures.

---

# Falcon

Alternative lattice-based --------------signature algorithm.

Smaller signatures but------------------ more complex implementation.

---

# MODULE 43 — Hybrid Cryptography

Modern systems combine:

* classical cryptography,
* post-quantum cryptography.

Example:

```
Classical Secret
+
Post-Quantum Secret
↓
KDF(Key derivation function)
↓
Final AES(Advanced encryption standard) Key
```

Provides security if either system remains secure.


# The complete modern security stack is:

**Hash Functions
      ↓
Symmetric Encryption (AES)
      ↓
Asymmetric Cryptography
      ↓
Diffie-Hellman Key Exchange
      ↓
HKDF Key Derivation
      ↓
TLS / HTTPS
      ↓
Digital Signatures
      ↓
Certificates & CAs
      ↓
Passkeys / WebAuthn
      ↓
Wi-Fi Security (WPA3)
      ↓
End-to-End Encryption
      ↓
Full Disk Encryption
      ↓
TPM / Secure Enclave
      ↓
Backups (3-2-1-1-0)
      ↓
Post-Quantum Cryptography
      ↓
ML-KEM + ML-DSA + Hybrid TLS**










---

