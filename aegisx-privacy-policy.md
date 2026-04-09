# AEGISX Privacy Policy

**Effective Date:** April 9, 2026
**Last Updated:** April 9, 2026

AEGISX is a private, end-to-end encrypted messaging platform operated by Frontier Capital Services LLC ("we," "us," "our") and built exclusively for Excelsior Family Office. AEGISX is invitation-only and is not available to the general public.

This policy explains what information AEGISX collects, what it does NOT collect, and how the post-quantum cryptographic architecture protects user content from us, from Apple, from network operators, and from any third party.

---

## 1. Summary

- We **cannot** read your messages, files, or call audio/video. They are encrypted on your device with keys that never leave your device.
- We **do** know who you are (account email), which conversations you participate in, and when messages are exchanged. We cannot see what was said.
- We **do not** sell, share, or monetize any data.
- We **do not** use analytics, advertising, tracking pixels, or third-party SDKs that profile users.
- AEGISX uses NIST FIPS 203 post-quantum cryptography (ML-KEM-1024) combined with classical Curve25519 in a hybrid construction.

---

## 2. Information We Collect

**Account information**
- Email address
- Display name
- Hashed password (Argon2id, never stored in plaintext)
- Organization membership

**Cryptographic public keys**
- X25519 public key
- ML-KEM-1024 public key
- These are public by design and do not reveal message content.

**Device information**
- Apple Push Notification (APNs) device token, used solely to deliver content-blind push notifications
- Device platform (iOS) and model name (e.g., "iPhone 14")

**Encrypted message envelopes**
- Sealed ciphertext bytes that the server stores but cannot decrypt
- Sender and recipient user IDs
- Conclave (group) membership
- Timestamps
- SHA-256 hash of the ciphertext for tamper-evident audit

**Encrypted attachments**
- Sealed ciphertext bytes of files you upload
- File size and MIME type
- We cannot view, scan, or index attachment content

**Audit log**
- Account creation, login, key upload, message send, and similar metadata events
- Used for security investigations and compliance

---

## 3. Information We Do NOT Collect

- **Message content** — encrypted on your device before transmission, undecryptable by us
- **Attachment content** — encrypted on your device before upload
- **Voice and video call content** — peer-to-peer SRTP, does not transit our servers in plaintext
- **Contact lists** — we do not import or access your iOS Contacts
- **Location data** — we do not request or store location
- **Browsing or app usage analytics** — no third-party analytics SDKs
- **Advertising identifiers (IDFA/IDFV)** — we do not collect or use them
- **Cookies or tracking pixels**
- **Biometric data** — Face ID and Touch ID are processed entirely on your device by iOS; we never receive biometric templates

---

## 4. How Encryption Works

Every AEGISX message is encrypted on your device with a hybrid post-quantum scheme:

1. **X25519 (Curve25519)** elliptic-curve Diffie-Hellman provides classical forward secrecy
2. **ML-KEM-1024 (FIPS 203, the NIST-standardized version of CRYSTALS-Kyber)** provides post-quantum key encapsulation
3. The two shared secrets are combined via **HKDF-SHA-256** following NIST SP 800-56C
4. The combined key is used with **XSalsa20-Poly1305** authenticated encryption to seal the message
5. Your private keys are stored in the **iOS Keychain** with access control set to `kSecAttrAccessibleWhenUnlockedThisDeviceOnly`, encrypted at rest by a hardware key held in the **Apple Secure Enclave**

To decrypt a message, an attacker must defeat both X25519 and ML-KEM-1024. Even a future cryptographically-relevant quantum computer cannot break ML-KEM-1024.

We cannot recover your messages if you lose access to your device. There is no backdoor, key escrow, or recovery mechanism on our side.

---

## 5. Data Retention

- **Sealed message ciphertext:** retained until you delete the conversation or trigger cryptographic erasure
- **Account information:** retained for the life of your account
- **Audit log:** retained for 12 months for security investigation purposes
- **Push tokens:** retained until you sign out or revoke them
- **Cryptographic erasure:** when you delete a conversation, we destroy the associated ephemeral keys, rendering any retained ciphertext bytes permanently undecryptable

---

## 6. How We Share Information

We do not share your information with anyone, with two narrow exceptions:

- **Service providers we cannot operate without:** Railway (server hosting), Apple (APNs delivery). These providers see encrypted bytes only; they cannot read message content.
- **Legal compulsion:** if served with a valid legal order, we will provide whatever data we possess. Because messages are encrypted with keys we do not have, we can produce only metadata (account info, sealed ciphertext bytes, timestamps), never plaintext.

We do not sell data. We do not share data for advertising. We do not participate in data broker networks.

---

## 7. Your Rights

Under GDPR, CCPA, and similar laws, you have the right to:

- **Access** the data we hold about you
- **Correct** inaccurate data
- **Delete** your account and all associated data
- **Export** your data in a machine-readable format
- **Object** to processing
- **Withdraw consent** at any time

To exercise any of these rights, contact us at the address below.

---

## 8. Children

AEGISX is not intended for users under 18. We do not knowingly collect data from minors.

---

## 9. International Data Transfers

Server infrastructure is hosted in the United States (Railway, AWS). By using AEGISX you acknowledge that your encrypted data may be processed in the United States. Because the data transferred is encrypted ciphertext that we cannot read, the privacy implications of cross-border transfer are minimal.

---

## 10. Encryption Export Compliance

AEGISX implements standardized cryptography (X25519, ML-KEM-1024, XSalsa20-Poly1305, AES-256-GCM, HKDF-SHA-256). Per Apple's encryption export classification, AEGISX qualifies as exempt under U.S. Export Administration Regulations §740.17(b)(1) because it uses non-proprietary cryptography for authentication and confidentiality.

---

## 11. Changes to This Policy

We will notify users of material changes via in-app notification and email. Continued use after notification constitutes acceptance.

---

## 12. Contact

**Frontier Capital Services LLC**
Email: javier@frontiercapitaltrust.com

For security disclosures, please email the same address with "AEGISX SECURITY" in the subject line.
