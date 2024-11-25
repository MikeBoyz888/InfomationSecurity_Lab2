# Lab #2, 19110054, Mai Dang Quang, INSE331280E_01FIE
# Task 1: Transfer files between computers
**Question 1**: 
Conduct transfering a single plaintext file between 2 computers, 
Using openssl to implementing measures manually to ensure file integerity and authenticity at sending side, 
then veryfing at receiving side.
**Answer 1**
## 1. Create a text file named `plain3.txt`:
*We write a message and save it in the text file:*<br>

```sh
echo "We will go west when the church bell ring." > plain3.txt
```
<img width="500" alt="Screenshot" src="https://private-user-images.githubusercontent.com/95457361/389347955-41e5d97f-32e1-41f5-a1a8-fe98f82b2191.png?raw=true"><br>

## 2. Generate a private key:

```sh
openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048
```

### 3. Extract the public key:

```sh
openssl rsa -in private.pem -pubout -out public.pem
```

### 4. Create a digital signature for the file:

```sh
openssl dgst -sha256 -sign private.pem -out signature.bin plain3.txt
```
 
### 5. Transfer the file including plain text, public key and digital signature to the receiving

### 6. On the receiving, verify the digital signature

```sh
openssl dgst -sha256 -verify public.pem -signature signature.bin plain3.txt
```

# Task 2: Transfering encrypted file and decrypt it with hybrid encryption. 
**Question 1**
Conduct transfering a file (deliberately choosen by you) between 2 computers. 
The file is symmetrically encrypted/decrypted by exchanging secret key which is encrypted using RSA. 
All steps are made manually with openssl at the terminal of each computer.

**Answer 1**
## 1. Create a text file named `plain4.txt`
*Write a message and save it in the text file*<br>

```sh
echo "There are 3 coming to the port." > plain4.txt
```