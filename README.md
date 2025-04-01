**Conclusion: SSH / TLS Handshake Analysis and Protocol Functionality**

This project served as a deep investigation into the Secure Shell (SSH) protocol, specifically its handshake process, cryptographic algorithm negotiation, and how it compares structurally and functionally to the TLS (Transport Layer Security) handshake. Through hands-on analysis, this project revealed not only the internal workings of SSH, but also its critical role in secure remote system management.

At the core of this project was the relationship between the SSH client (MacBook) and SSH server (Dell Windows 11). The client initiates a connection to the server over port 22, prompting a structured cryptographic handshake. This begins with the server presenting its public host key—a persistent cryptographic identifier unique to SSH servers—and continues through a key exchange algorithm (e.g., Curve25519), during which a shared session key is securely established using Diffie-Hellman. Unlike TLS, which relies on certificate authorities for trust, SSH uses a Trust on First Use (TOFU) model, placing more responsibility on the client to track known hosts.

One of the key educational insights of this project is the ordering and purpose of encryption. In SSH, encryption is established before authentication, ensuring credentials and session activity remain protected from the start. This contrasts with TLS, where the server is authenticated first using a certificate, and only afterward is encryption initiated. SSH's early encryption prioritizes confidentiality of authentication, while TLS prioritizes validation of trust. This distinction is foundational in understanding when and why each protocol is used in practice.

This distinction directly influences the real-world application of each protocol. SSH is ideally suited for administrative access, remote management, and automation, where the priority is to protect login credentials and all session activity from the outset—often in environments where trust relationships are pre-established. In contrast, TLS is designed for broader, often public-facing communication, such as accessing websites or APIs, where verifying the server’s identity through a certificate chain is essential before any private data is exchanged. The early encryption in SSH minimizes risk in environments where confidentiality is paramount from the very first packet, while TLS supports scalable, certificate-based trust suitable for securing data in transit across large and distributed systems like the web.

From a technical standpoint, this project explored the tools used by analysts to enumerate SSH capabilities (Nmap scans), observe negotiation processes (via verbose SSH logging), and compare protocol structures (via side-by-side TLS analysis). Although Wireshark packet filtering challenges prevented a successful packet-layer visualization, the fallback strategy—using ssh -vvv logging—offered direct insight into handshake negotiations, algorithm selection, and authentication paths.

This project demonstrated that Secure Shell, while often recognized for remote login, is fundamentally a protocol that establishes secure, authenticated communication channels. Through hands-on analysis of the handshake process, we observed how encryption and authentication are tightly integrated to form the foundation for broader SSH-based functions.

Clarified the SSH handshake sequence and cryptographic process.

Differentiated SSH from TLS in purpose, encryption timing, and trust models.

Reinforced the client-server relationship within secure communication protocols.

Provided hands-on exposure to real-world reconnaissance tools (Nmap) and protocol-level diagnostics.

Built a reference foundation for identifying and validating secure communication in enterprise systems.
