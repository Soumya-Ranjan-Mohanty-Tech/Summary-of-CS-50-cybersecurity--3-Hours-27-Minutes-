# Summary-of-CS-50-cybersecurity--3-Hours-27-Minutes-

# CS50 Intro to Cybersecurity (Part 1–3) — The Complete Condensed Study Guide

```text
Identity
   ↓
Authentication
   ↓
Authorization
   ↓
Cryptography
   ↓
Secure Communication
   ↓
Secure Storage
   ↓
Secure Systems
   ↓
Future Threats (Quantum Computing)
```

---

# 1. Authentication and Authorization

## Authentication = Who are you?

The process of proving your identity.

Examples:

* Username + Password
* Fingerprint
* Face ID
* OTP
* Passkey

Example:

```
Website asks:
Who are you?

You prove:
I am Soumya.

Authentication successful.
```

---

## Authorization = What can you access?

After identity is verified, the system decides what resources you may use.

Example:

```
Employee login successful

Can access:
✓ Email

Cannot access:
✗ Payroll database
```

---

# 2. Password Security

## Dictionary Attack

Attacker tries common words from a list.

Example:

```
password
football
india123
welcome
qwerty
```

Weak passwords fall quickly.

---

## Brute Force Attack

Attacker systematically tries every possible password.

Example:

```
0000
0001
0002
0003
...
9999
```

A 4-digit PIN:

```
10^4 = 10,000 combinations
```

Modern computers can test enormous numbers of combinations very quickly.

---

## Password Complexity

Increasing character sets dramatically increases possibilities.

### Digits only

```
0-9
```

10 possibilities per position.

---

### Letters

```
a-z
A-Z
```

52 possibilities.

---

### Letters + Numbers + Symbols

```
A-Z
a-z
0-9
!@#$%^&
```

Huge search space.

---

# 3. NIST Password Recommendations

The **National Institute of Standards and Technology (NIST)** publishes modern password guidelines.

Important points:

### Minimum Length

At least:

```
8 characters
```

---

### Maximum Length

Allow at least:

```
64 characters
```

---

### Accept Special Characters

Examples:

```
!
@
#
$
%
```

---

### Accept Unicode

Examples:

```
你好
नमस्ते
😊
```

---

### Block Weak Passwords

Reject:

```text
password123
qwerty
admin
123456
```

---

### Avoid Password Hints

Bad:

```text
First pet?
Mother's maiden name?
```

Attackers may discover these.

---

### No Forced Password Changes

Changing passwords every month often leads users to choose weaker passwords.

Bad:

```
Password1
Password2
Password3
```

---

### Rate Limiting

Limit login attempts.

Example:

```
5 failed attempts

Account locked temporarily
```

This slows brute-force attacks.

---

# 4. Multi-Factor Authentication (MFA)

Authentication factors fall into three categories.

---

## Knowledge Factor

Something you know.

Examples:

```
Password
PIN
Security answer
```

---

## Possession Factor

Something you have.

Examples:

```
Phone
Authenticator app
Security key
```

---

## Inherence Factor

Something you are.

Examples:

```
Fingerprint
Face
Iris scan
Voice
```

---

## Why MFA- Multi Factor Athentication Works

Attacker needs multiple independent factors.

Example:

```
Password
+
Phone OTP
```

Password alone is insufficient.

---

# 5. One-Time Passwords (OTP)

Temporary code.

Example:

```
683294
```

Valid only briefly.

---

# 6. SIM Swapping

Attacker convinces telecom provider:

```
"I am the customer."
```

Provider transfers phone number to attacker’s SIM.

Result:

```
Victim OTPs
↓
Attacker receives them
```

**Therefore**:

Prefer:

```
 [Authenticator Apps]
```

instead of:

```
SMS OTP
```

whenever possible.

---

# 7. [Malware] - Malicious software and [Keyloggers] - Records keystrokes

Malware:

```
Malicious software
```

Examples:

* Virus
* Worm
* Trojan
* Spyware

---

## Keylogger

Records keystrokes.

Captures:

```
Passwords
Credit cards
Emails
Messages
```

Even strong passwords fail if malware records them.

---

# 8. Credential Stuffing

Attacker already possesses leaked credentials.

Example:

```
Username:
abc@gmail.com

Password:
hello123
```

They try same credentials elsewhere.

Because users reuse passwords.

Defense:

* Unique passwords
* Password manager
* MFA

---

# 9. Social Engineering

Manipulating humans instead of computers.

Examples:

```
Pretending to be support staff
Pretending to be a bank
Pretending to be a coworker
```

---

# 10. Phishing

Fake communications designed to steal credentials.

Examples:

* Email
* SMS
* Website

Always verify:

```
URL
Domain name
HTTPS
```

---

# 11. Man-in-the-Middle (MITM)

Attacker sits between two parties.

```
Alice
 ↕
Eve
 ↕
Bob
```

Eve may:

* Read
* Modify
* Inject
* Forward

communications.

Defense:

* TLS
* HTTPS
* WPA
* Digital certificates

---

# 12. Password Managers

Store strong unique passwords.

Examples:

* Apple iCloud Keychain
* Google Password Manager
* Microsoft Credential Manager

Benefits:

* Unique passwords everywhere
* Resistant to credential stuffing
* No memorization burden

---

# 13. Hash Functions

A hash function converts arbitrary-length input into fixed-length output.

Example:

```
apple
↓
8d93a4...
```

---

## Properties

### Fixed Length Output

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

### One-Way

Easy:

```
Input → Hash
```

Hard:

```
Hash → Input
```

---

# 14. Password Storage

Websites should store:

```
Hash(password)
```

not:

```
password
```

---

During login:

```
User enters password
↓
Hash generated
↓
Compare hashes
```

Match:

```
Authenticated
```

---

# 15. Rainbow Tables

Precomputed database:

```
Password → Hash
```

Example:

```
apple → xyz
banana → abc
```

Allows rapid cracking.

---

# 16. Salting

Random value added before hashing.

Example:

```
password + salt
↓
hash
```

Benefits:

* Same password ≠ same hash
* Defeats rainbow tables
* Makes mass cracking harder

Every user should have a unique salt.

---

# 17. Cryptography

Science of securing information.

Goals:

* Confidentiality
* Integrity
* Authentication
* Non-repudiation

---

# 18. Codes vs Ciphers

## Codes

Whole words mapped.

Example:

```text
"Bluebird"
=
"Attack"
```

Require codebook.

---

## Ciphers

Algorithm transforms characters/bits.

Example:

```text
HELLO
↓
KHOOR
```

More flexible.

Modern cryptography uses ciphers.

---

# 19. Symmetric Encryption

Same key for encryption and decryption.

```text
Encrypt
 ↓
Secret Key
 ↓
Decrypt
```

Both parties need identical key.

Examples:

* AES
* Triple DES

---

## Problem

How do both parties obtain the secret key securely?

This leads to public-key cryptography.

---

# 20. Asymmetric Encryption

Uses two keys:

```text
Public Key
Private Key
```

---

Public key:

```text
Shared openly
```

Private key:

```text
Kept secret
```

---

Anyone can encrypt using public key.

Only private key owner can decrypt.

---

# 21. RSA

Popular public-key algorithm.

---

## Key Generation

Choose primes:

```text
p
q
```

Compute:

```text
n = p × q
```

Compute:

```text
φ(n)=(p−1)(q−1)
```

Choose:

```text
e
```

Compute:

```text
d
```

Result:

```text
Public Key=(n,e)

Private Key=(n,d)
```

---

## Security

Based on difficulty of factoring large numbers.

---

# 22. Diffie–Hellman Key Exchange

Purpose:

```text
Securely create shared secret
```

without sending secret itself.

---

Alice:

```text
A = g^a mod p
```

Bob:

```text
B = g^b mod p
```

Exchange A and B publicly.

---

Shared secret:

```text
S = g^(ab) mod p
```

Both compute same value.

Attacker cannot easily derive it.

---

# 23. Key Derivation Function (KDF)

Transforms shared secret into strong symmetric key.

Examples:

* HKDF
* SHA-256

Produces:

```text
AES key
```

used for encryption.

---

# 24. Diffie-Hellman Weakness

No authentication.

Attacker can impersonate parties.

Classic MITM attack.

Solution:

```text
Certificates
Digital Signatures
```

---

# 25. Perfect Forward Secrecy (PFS)

Generate temporary keys for each session.

After session:

```text
Delete keys
```

Benefits:

If server compromised later:

```text
Old traffic remains protected
```

Implemented using:

* DHE
* ECDHE

---

# 26. Digital Signatures

Purpose:

* Verify identity
* Verify integrity

---

Process:

Document

↓

Hash

↓

Sign hash with private key

↓

Digital signature

---

Verification:

Document

↓

Hash

↓

Compare with hash recovered using public key

---

If identical:

```text
Document unchanged
Signature valid
```

---

# 27. Passkeys (WebAuthn)

Modern replacement for passwords.

Each website gets:

```text
Public Key
Private Key
```

pair.

---

Website stores:

```text
Public Key
```

Device stores:

```text
Private Key
```

---

Login:

Website sends challenge.

Device signs challenge.

Website verifies signature.

Advantages:

* No passwords
* Phishing resistant
* No credential stuffing

---

# 28. Encryption in Transit

Protects moving data.

Example:

```text
Browser ⇄ Website
```

Uses:

* TLS
* HTTPS

---

## End-to-End Encryption (E2EE)

Only sender and recipient can read messages.

Examples:

* WhatsApp
* iMessage

Even service provider should not see contents.

---

# 29. Encryption at Rest

Protects stored data.

Example:

```text
Laptop SSD
Phone storage
Database
```

Uses encryption while data sits idle.

---

## Full Disk Encryption (FDE)

Encrypts entire storage drive.

Examples:

* BitLocker
* FileVault

Benefits:

Stolen device ≠ stolen data.

---

# 30. Secure Deletion

Deleting file usually removes references only.

Data may still exist.

Secure deletion:

```text
Overwrite bits
```

with:

* zeros
* ones
* random values

---

# 31. TPM and Secure Enclave

Hardware security modules.

Store encryption keys securely.

Examples:

* TPM (Windows)
* Secure Enclave (Apple)

Protect against physical theft and tampering.

---

# 32. Ransomware

Attacker encrypts victim’s files.

Then demands payment.

Example:

```text
Pay 5 BTC
or lose data
```

---

FDE does NOT stop ransomware.

Reason:

Files are already decrypted while you are logged in.

---

# 33. Backup Strategy (3-2-1-1-0)

Maintain:

### 3 copies

Original + 2 backups

### 2 media types

SSD + HDD

### 1 offsite copy

Cloud

### 1 immutable copy

Air-gapped/locked

### 0 restore errors

Test backups regularly

---

# 34. Wi-Fi Security

Standards:

* WPA
* WPA2
* WPA3

Encrypt traffic between:

```text
Device ⇄ Router
```

Prevent wireless eavesdropping.

---

# 35. Packet Sniffing

Capturing network packets.

Tools:

* Wireshark
* tcpdump

---

Legitimate:

* Troubleshooting
* Security analysis

---

Malicious:

* Password theft
* Cookie theft
* Session hijacking

---

HTTPS prevents reading packet contents.

---

# 36. Cookies and Sessions

After login:

Server sends:

```text
Set-Cookie
```

Browser stores:

```text
session=1234abcd
```

Future requests include cookie.

This allows websites to remember users.

---

Risk:

Session hijacking.

Defense:

```text
HTTPS
Secure cookies
```

---

# 37. TLS and Certificates

TLS secures HTTP.

Result:

```text
HTTPS
```

---

Website owns:

```text
Public Key
Private Key
```

---

Certificate contains:

* Domain name
* Public key
* Expiration date
* Digital signature

Format:

```text
X.509
```

---

# 38. Certificate Authorities (CA)

Trusted organizations.

Examples:

* DigiCert
* Let's Encrypt
* GlobalSign

---

CA signs website certificates.

Browser verifies signature.

If valid:

```text
Connection trusted
```

---

# 39. Quantum Computing

Classical bit:

```text
0 or 1
```

Quantum bit:

```text
0 and 1 simultaneously
```

(superposition)

Potentially massive computational power.

---

# 40. Threat to Cryptography

Shor's Algorithm can break:

* RSA
* Diffie-Hellman
* ECC

by solving currently hard mathematical problems efficiently.

---

# 41. Post-Quantum Cryptography (PQC)

Designed to resist quantum attacks.

Examples:

### ML-KEM (Kyber)

Key exchange / key encapsulation.

### ML-DSA (Dilithium)

Digital signatures.

### Falcon

Alternative signature scheme.

---

# 42. Hybrid Cryptography

Current deployment:

```text
Classical DH
+
ML-KEM
↓
KDF
↓
AES Key
```

Secure if either mechanism remains secure.

Used by modern infrastructure such as browsers and major network providers.

---

# The 15 Most Important Things to Remember

1. Authentication proves identity.
2. Authorization determines permissions.
3. Strong passwords + MFA are essential.
4. Credential reuse leads to credential stuffing attacks.
5. Hash passwords; never store plaintext passwords.
6. Salt hashes to defeat rainbow tables.
7. Symmetric encryption uses one key (AES).
8. Asymmetric encryption uses public/private keys (RSA).
9. Diffie–Hellman creates shared secrets.
10. Digital signatures provide authenticity and integrity.
11. TLS + certificates secure HTTPS.
12. Passkeys replace passwords using public-key cryptography.
13. Full Disk Encryption protects stolen devices.
14. Backups defeat ransomware.
15. Quantum computers threaten RSA/DH, leading to post-quantum cryptography.

If you truly understand these 15 points and how they connect, you have captured the core ideas from the entire 3 hours 27 minutes of material.
