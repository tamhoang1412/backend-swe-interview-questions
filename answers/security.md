# SECURITY

## Hash vs Encrypt vs Encode

Hashing is the act of transforming data from arbitrary size to a fixed size value. For example the module operator.

Encode is a way to transform data to another form to preserve usability. For example, 2 bit 0 and 1 can represent almost every kind of data we know.

Encryption is the act of transforming data to another form to preserve confidentiality. For example, AES encryption uses a secret key to transform data into an encrypted string. Only the person who has the same key can decrypt the encrypted string and read the message.

## Are there any way we can crack Hash

We can always try to guess the original string by calculating the hash of every possible input then comparing the result with the hash string. However, due to hashing collision, there might be more than one input that has the same output.

## Symmetric vs asymmetric encryption? AES vs RSA?

Symmetric encryption uses the same key for both encrypting and decrypting data.

Asymmetric encryption uses a public key to encrypt and a private key to decrypt data.

## Fast Hash vs Slow Hash?

Fast Fash is the type of hash function with fast computation time and Slow Hash is the type hash function with slow computation time. Fast Hash is used for checking the integrity of data, while slow hash is used for hashing password.

## When we use Encode??

We use Encode so data can be represented in a better use form. For example, we transform text, audio, image into 1 and 0 so computers can understand, store, process, etc.

## What is the perfect hash function?

A perfect hash function of a set is a hash function that maps distinct elements of this set to elements of another set without any collisions.

## What is the load factor of hashing?

When a map initiates, two things need to be considered are the initial capacity and the load factor. The initial capacity is the capacity of the hash table underlying the map. When the load is bigger than the load factor, it means the underlying table is quite full, a process called rehashing happens, a twice bigger size hash table is allocated to store the data of the map.

## SSL/TLS

To be defined.

## How to verify a certificate? How many kinds of certificates are there?

To be defined.

## What is CA? how to verify certificate of a CA?

CA stands for certificate authority. It is an entity that verifies the certificate of servers.

When a server and a client want to establish an SSL connection, the server will send its public key to the client. So how the client knows this public key is the right one, and no man in the middle tries to interfere in this conversation. To do that, the server also sent a certificate with the public key. The client will ask the CA to verify if the public key is the correct key of the one in the certificate.

## What is digital signature? What is HMAC?

Digital signature is a mathematical scheme to verify the authenticity of data.

HMAC stands for hash based message authentication code, is used to verify both data integrity and data authenticity.

## How to store credential information efficiency? (user password, config key, database credential, user information, secret key,.... )

First, we need to know if we need to access the original value or not.

For data like passwords, we don't need to access the raw password of users, so we can use some hashing function to hash the password and store it in the database.

For data like user information, the raw data will need to be retrieved in some cases, so we need to use encryption, instead of hashing. To reduce the risk of data compromise, we need to store data and the encryption key in 2 different places.

## Describe a way to defense DDOS? (actually, there are many kinds of DDOS not just network or memory, so this question is pretty complicated)

Block IP address, apply rate limit for IP, for users.
