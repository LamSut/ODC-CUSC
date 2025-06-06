# DIGITAL SIGNATURE GENERATION WITH OPENSSL

**Note:** This guide is for practice only. In real-world applications, digital certificates must be issued by a trusted Certificate Authority (CA) or provided by your institution to ensure authenticity and security.

# Objective

Generate the following SSL files using OpenSSL:

```
ssl/
├── private.key       # Private key
├── request.csr       # Certificate Signing Request
└── certificate.crt   # Self-signed certificate
```

# Steps to Create a Digital Signature Using OpenSSL

## Step 1: Install OpenSSL

### On Ubuntu/Debian
```bash
sudo apt update
sudo apt install openssl
```

### On macOS (using Homebrew)
```bash
brew install openssl
```

### On Windows

1. Download OpenSSL for Windows: https://slproweb.com/products/Win32OpenSSL.html
2. Install and add OpenSSL to your system PATH.

## Step 2: Generate Private Key

```bash
openssl genrsa -out private.key 2048
```

This creates a 2048-bit private key file named `private.key`.

## Step 3: Generate a Certificate Signing Request (CSR)

```bash
openssl req -new -key private.key -out request.csr
```

You will be prompted to enter information such as:

- Country Name (2 letter code)
- State or Province Name
- Locality Name
- Organization Name
- Common Name (e.g., your domain name or localhost)

## Step 4: Generate a Self-Signed Certificate

```bash
openssl x509 -req -days 365 -in request.csr -signkey private.key -out certificate.crt
```

This creates a self-signed certificate valid for 365 days.

# Result

You should now have the following files:

- `private.key` – Your private key
- `request.csr` – The CSR used for signing
- `certificate.crt` – Your self-signed certificate

