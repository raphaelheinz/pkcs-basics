# How to convert between different PKCS formats

## Create pkcs8 private key
`openssl genrsa -out private.pem 4096`


## pkcs8

### pkcs8 private key -> pkcs1 public key
`openssl rsa -in private_pkcs8.pem -RSAPublicKey_out -out public_pkcs1.pem`

### pkcs8 public key -> pkcs1 public key
`openssl rsa -pubin -in public_pkcs8.pem -RSAPublicKey_out -out public_pkcs1.pem`

### pkcs8 private key -> x509 public key
`openssl rsa -in private.pem -out public.pem -pubout`

### pkcs8 private key -> pkcs1 private key
`openssl rsa -in private_pkcs8.pem -out private_pkcs1.pem -traditional`


## pkcs1

### pkcs1 public key -> pkcs8 public key
`openssl rsa -RSAPublicKey_in -in public_pkcs1.pem -pubout -out public_pkcs8.pem`

### pkcs1 private key -> pkcs8 private key
`openssl pkcs8 -topk8 -inform pem -in private_pkcs1.pem -outform pem -nocrypt -out private_pkcs8.pem`

`openssl pkcs8 -topk8 -inform pem -in private_pkcs1.pem -outform pem -out private_pkcs8-enc.pem`

