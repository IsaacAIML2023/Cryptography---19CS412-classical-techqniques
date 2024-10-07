# Cryptography---19CS412-classical-techqniques
# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To encrypt and decrypt the given message by using Ceaser Cipher encryption algorithm.


## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

1.	In Ceaser Cipher each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
2.	For example, with a left shift of 3, D would be replaced by A, E would become B, and so on.
3.	The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the   
    scheme, A = 0, B = 1, Z = 25.
4.	Encryption of a letter x by a shift n can be described mathematically as,
                       En(x) = (x + n) mod26
5.	Decryption is performed similarly,
                       Dn (x)=(x - n) mod26


## PROGRAM:

``` 

#include <stdio.h>
#include <string.h>

void encrypt(char message[], int shift) {
    char ch;
    for (int i = 0; message[i] != '\0'; ++i) {
        ch = message[i];
        if (ch >= 'a' && ch <= 'z') {
            ch = ch + shift;
            if (ch > 'z') {
                ch = ch - 'z' + 'a' - 1;
            }
            message[i] = ch;
        } else if (ch >= 'A' && ch <= 'Z') {
            ch = ch + shift;
            if (ch > 'Z') {
                ch = ch - 'Z' + 'A' - 1;
            }
            message[i] = ch;
        }
    }
    printf("Encrypted message: %s\n", message);
}

void decrypt(char message[], int shift) {
    char ch;
    for (int i = 0; message[i] != '\0'; ++i) {
        ch = message[i];
        if (ch >= 'a' && ch <= 'z') {
            ch = ch - shift;
            if (ch < 'a') {
                ch = ch + 'z' - 'a' + 1;
            }
            message[i] = ch;
        } else if (ch >= 'A' && ch <= 'Z') {
            ch = ch - shift;
            if (ch < 'A') {
                ch = ch + 'Z' - 'A' + 1;
            }
            message[i] = ch;
        }
    }
    printf("Decrypted message: %s\n", message);
}

int main() {
    char message[100];
    int shift;

    printf("Enter a message: ");
    gets(message);  // reads a line of text

    printf("Enter shift amount: ");
    scanf("%d", &shift);

    // Make a copy of the message to decrypt later
    char encrypted_message[100];
    strcpy(encrypted_message, message);

    encrypt(encrypted_message, shift);
    decrypt(encrypted_message, shift);

    return 0;
}
```


## OUTPUT:
### Simulating Caesar Cipher
![CRYOP1CAE](https://github.com/user-attachments/assets/73d229bd-7f14-4e10-a8b6-c60d8e214998)




Input : mukesh

Encrypted Message :  pxnhvk

Decrypted Message :  mukesh

## RESULT:
The Caeser Cipher program is executed successfully
----------
