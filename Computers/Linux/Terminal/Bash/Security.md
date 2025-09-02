---
created: 2024-02-21 14:50:39Z
---

# Encryption
## OpenSSL
Encrypt & decrypt files with a password protection.

	openssl enc -aes-256-ctr -in my.pdf -out my.pdf.enc
	openssl enc -aes-256-ctr -d -in my.pdf.enc -out my.pdf
