# P2P-File-Sharing
# 🔒 Secure P2P Encrypted File Transfer Tool

A lightweight, high-security peer-to-peer (P2P) file transfer utility built in **Python** using raw **TCP sockets** and **AES-GCM** authenticated encryption. Designed for direct cross-platform execution between **Windows** and **Android (Termux)**, it establishes a zero-trust encrypted tunnel that bypasses third-party cloud relays and ensures complete data confidentiality in transit.

---

## 🛠️ Tech Stack & Prerequisites

- **Language:** Python 3.x
- **Network Layer:** Raw TCP Sockets (`socket` module)
- **Encryption Standard:** AES-GCM (Advanced Encryption Standard with Galois/Counter Mode via `cryptography`)
- **Supported Platforms:** Windows 10/11 (Sender) & Android via Termux (Receiver)

---

## 📐 Architecture & Workflow

1. **Socket Handshake:** The sender script binds to a local port and awaits an incoming TCP socket connection from the receiver.
2. **Metadata Stream:** Filename and file size descriptors are transmitted across the tunnel.
3. **Chunk-Based Encryption:** Files are read and encrypted chunk-by-chunk using a unique random 12-byte nonce per block to prevent replay attacks.
4. **Decryption & Verification:** The receiver authenticates and decrypts each chunk on the fly before writing the verified binary output directly to disk.
