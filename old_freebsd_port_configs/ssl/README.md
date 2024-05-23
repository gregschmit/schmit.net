# SSL (Secure Sockets Layer)

This directory is meant to contain the private keys, host certificates, intermediate certificates, and certificate signing requests (CSRs) that you may need on the server.

## Helpful `OpenSSL` Commands

 - How to generate a private key:

`openssl genpkey -algorithm rsa -pkeyopt rsa_keygen_bits:4096 -out key.pem`

 - How to generate a CSR from a private key:

`openssl req -new -key key.pem -out csr.pem`

 - How to sign a certificate (in this case, with your own key - this is known as a self-signed certificate):

`openssl x509 -req -days 365 -in csr.pem -signkey key.pem -out crt.pem`

 - How to directly create a self-signed certificate without a CSR:
 
`openssl req -x509 -new -nodes -sha256 -days 256 -key key.pem -out crt.pem`

## Creating and using your own Certificate Authority

 1. First, create your root key/certificate (keep this very private) and your root certificate:

`openssl genpkey -algorithm rsa -pkeyopt rsa_keygen_bits:4096 -out root-key.pem`

`openssl req -x509 -new -nodes -key root-key.pem -sha256 -days 1024 -out root-crt.pem`

 2. Create the client key/CSR (prefereably do this on the client itself, not on the CA as this reveals the client private key to the CA):

`openssl genpkey -algorithm rsa -pkeyopt rsa_keygen_bits:4096 -out client-key.pem`

`openssl req -new -key client-key.pem -out client-csr.pem`

 3. Sign the certificate with your CA:

`openssl x509 -req -days 500 -sha256 -in client-csr.pem -CA root-crt.pem -CAkey root-key.pem -CAcreateserial -out client-crt.pem`
