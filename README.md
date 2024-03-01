# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple python program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```python
## Encryption:

def caesar_cipher(text, shift):
    encrypted_text = ""
    for char in text:
        if char.isalpha():  # Check if the character is alphabet
            shifted = ord(char) + shift
            if char.islower():
                if shifted > ord('z'):
                    shifted -= 26
                elif shifted < ord('a'):
                    shifted += 26
            elif char.isupper():
                if shifted > ord('Z'):
                    shifted -= 26
                elif shifted < ord('A'):
                    shifted += 26
            encrypted_text += chr(shifted)
        else:
            encrypted_text += char
    return encrypted_text
text = "kaushik"
shift = 3


encrypted_text = caesar_cipher(text, shift)
print("Original Text:", text)
print("Encrypted Text:", encrypted_text)

## Decryption:

def caesar_decrypt(encrypted_text, shift):
    decrypted_text = ""
    for char in encrypted_text:
        if char.isalpha():  # Check if the character is alphabet
            shifted = ord(char) - shift
            if char.islower():
                if shifted > ord('z'):
                    shifted -= 26
                elif shifted < ord('a'):
                    shifted += 26
            elif char.isupper():
                if shifted > ord('Z'):
                    shifted -= 26
                elif shifted < ord('A'):
                    shifted += 26
            decrypted_text += chr(shifted)
        else:
            decrypted_text += char
    return decrypted_text


text = "kaushik"
shift = 3

decrypted_text = caesar_decrypt(encrypted_text, shift)
print("Decrypted Text:", decrypted_text)
```
## OUTPUT:

![Screenshot 2024-03-01 152026](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/129837020/609b9f69-316f-4744-8791-614460a8fc04)

## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple python program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```python

def generate_key_square(key):
    key = key.upper().replace(" ", "")
    key_square = ""
    for char in key:
        if char not in key_square:
            key_square += char
    alphabet = "ABCDEFGHIKLMNOPQRSTUVWXYZ"
    for char in alphabet:
        if char not in key_square:
            key_square += char
    return key_square

def prepare_text(text):
    text = text.upper().replace(" ", "")
    text = "".join(char for char in text if char.isalpha())
    if len(text) % 2 != 0:
        text += 'X'
    return text

def encrypt_pair(pair, key_square):
    row1, col1 = divmod(key_square.index(pair[0]), 5)
    row2, col2 = divmod(key_square.index(pair[1]), 5)
    if row1 == row2:
        return key_square[row1 * 5 + (col1 + 1) % 5] + key_square[row2 * 5 + (col2 + 1) % 5]
    elif col1 == col2:
        return key_square[((row1 + 1) % 5) * 5 + col1] + key_square[((row2 + 1) % 5) * 5 + col2]
    else:
        return key_square[row1 * 5 + col2] + key_square[row2 * 5 + col1]

def decrypt_pair(pair, key_square):
    row1, col1 = divmod(key_square.index(pair[0]), 5)
    row2, col2 = divmod(key_square.index(pair[1]), 5)
    if row1 == row2:
        return key_square[row1 * 5 + (col1 - 1) % 5] + key_square[row2 * 5 + (col2 - 1) % 5]
    elif col1 == col2:
        return key_square[((row1 - 1) % 5) * 5 + col1] + key_square[((row2 - 1) % 5) * 5 + col2]
    else:
        return key_square[row1 * 5 + col2] + key_square[row2 * 5 + col1]

def playfair_encrypt(plain_text, key):
    key_square = generate_key_square(key)
    plain_text = prepare_text(plain_text)
    encrypted_text = ""
    for i in range(0, len(plain_text), 2):
        encrypted_text += encrypt_pair(plain_text[i:i+2], key_square)
    return encrypted_text

def playfair_decrypt(encrypted_text, key):
    key_square = generate_key_square(key)
    decrypted_text = ""
    for i in range(0, len(encrypted_text), 2):
        decrypted_text += decrypt_pair(encrypted_text[i:i+2], key_square)
    return decrypted_text

# Example usage:
plain_text = "SHAYAM"
key = "PLAYFAIR EXAMPLE"

encrypted_text = playfair_encrypt(plain_text, key)
print("Encrypted Text:", encrypted_text)

decrypted_text = playfair_decrypt(encrypted_text, key)
print("Decrypted Text:", decrypted_text)



```
## OUTPUT:

![Screenshot 2024-03-01 152218](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/129837020/6dff1487-ff09-4816-896f-4e3f6b766ef1)

## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple python program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```python
import numpy as np

def generate_key_matrix(key):
    key = key.upper().replace(" ", "")
    n = int(len(key) ** 0.5)
    if n * n != len(key):
        raise ValueError("Key length must be a perfect square")
    key_matrix = np.array([ord(char) - ord('A') for char in key]).reshape(n, n)
    return key_matrix

def generate_inverse_key_matrix(key_matrix):
    determinant = np.linalg.det(key_matrix)
    inverse_matrix = np.linalg.inv(key_matrix)
    adjugate_matrix = np.round(inverse_matrix * determinant).astype(int)
    det_inv = pow(int(determinant), -1, 26)
    inverse_key_matrix = (adjugate_matrix * det_inv) % 26
    return inverse_key_matrix

## ENCRYPTION

def hill_encrypt(plain_text, key_matrix):
    plain_text = plain_text.upper().replace(" ", "").replace("J", "I")
    n = key_matrix.shape[0]
    while len(plain_text) % n != 0:
        plain_text += 'X'
    plain_text = [ord(char) - ord('A') for char in plain_text]
    plain_matrix = np.array(plain_text).reshape(-1, n)
    encrypted_matrix = np.dot(plain_matrix, key_matrix) % 26
    encrypted_text = ""
    for row in encrypted_matrix:
        for char in row:
            encrypted_text += chr(char + ord('A'))
    return encrypted_text

## DECRYPTION

def hill_decrypt(encrypted_text, key_matrix):
    n = key_matrix.shape[0]
    inverse_key_matrix = generate_inverse_key_matrix(key_matrix)
    encrypted_text = encrypted_text.upper().replace(" ", "").replace("J", "I")
    encrypted_text = [ord(char) - ord('A') for char in encrypted_text]
    encrypted_matrix = np.array(encrypted_text).reshape(-1, n)
    decrypted_matrix = np.dot(encrypted_matrix, inverse_key_matrix) % 26
    decrypted_text = ""
    for row in decrypted_matrix:
        for char in row:
            decrypted_text += chr(char + ord('A'))
    return decrypted_text

key = "HILL"
plaintext = "ShyamS"
key_matrix = generate_key_matrix(key)

encrypted_text = hill_encrypt(plaintext, key_matrix)
print("Plaintext:", plaintext)
print("Encrypted text:", encrypted_text)


decrypted_text = hill_decrypt(encrypted_text, key_matrix)
print("Decrypted text:", decrypted_text)

```
## OUTPUT:

![Screenshot 2024-03-01 152402](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/129837020/44703624-f93d-499d-8152-975f31963fb5)

## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple python program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```python

## ENCRYPTION

def vigenere_encrypt(plain_text, key):
    key = key.upper()
    encrypted_text = ""
    key_index = 0
    for char in plain_text:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            if char.islower():
                encrypted_char = chr((ord(char) - ord('a') + shift) % 26 + ord('a'))
            else:
                encrypted_char = chr((ord(char) - ord('A') + shift) % 26 + ord('A'))
            encrypted_text += encrypted_char
            key_index += 1
        else:
            encrypted_text += char
    return encrypted_text

## DECRYPTION

def vigenere_decrypt(encrypted_text, key):
    key = key.upper()
    decrypted_text = ""
    key_index = 0
    for char in encrypted_text:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            if char.islower():
                decrypted_char = chr((ord(char) - ord('a') - shift + 26) % 26 + ord('a'))
            else:
                decrypted_char = chr((ord(char) - ord('A') - shift + 26) % 26 + ord('A'))
            decrypted_text += decrypted_char
            key_index += 1
        else:
            decrypted_text += char
    return decrypted_text

plain_text = "kaushik"
key = "cipher"
encrypted_text = vigenere_encrypt(plain_text, key)
print("Original Text:", plain_text)
print("Encrypted Text:", encrypted_text)

decrypted_text = vigenere_decrypt(encrypted_text, key)
print("Decrypted Text:", decrypted_text)
```
## OUTPUT:
![Screenshot 2024-03-01 153658](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/129837020/cbe3679a-8075-4ab3-8595-01da6dd08b5b)


## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple python program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```python

## ENCRYPTION

def rail_fence_encrypt(plain_text, key):
    encrypted_text = ""
    rail = [''] * key
    direction = False
    row = 0

    for char in plain_text:
        rail[row] += char
        if row == 0 or row == key - 1:
            direction = not direction
        row += 1 if direction else -1

    for i in range(key):
        encrypted_text += rail[i]

    return encrypted_text

## DECRYPTION

def rail_fence_decrypt(encrypted_text, key):
    decrypted_text = ""
    rail = [''] * key
    direction = False
    row = 0
    index = 0

    for char in encrypted_text:
        rail[row] += '*'
        if row == 0 or row == key - 1:
            direction = not direction
        row += 1 if direction else -1

    for i in range(key):
        for j in range(len(rail[i])):
            if rail[i][j] == '*' and index < len(encrypted_text):
                rail[i] = rail[i][:j] + encrypted_text[index] + rail[i][j + 1:]
                index += 1

    row = 0
    direction = False
    for i in range(len(encrypted_text)):
        decrypted_text += rail[row][0]
        rail[row] = rail[row][1:]
        if row == 0 or row == key - 1:
            direction = not direction
        row += 1 if direction else -1

    return decrypted_text

plain_text = "kaushik"
key = 3
encrypted_text = rail_fence_encrypt(plain_text, key)
print("Original Text:", plain_text)
print("Encrypted Text:", encrypted_text)

decrypted_text = rail_fence_decrypt(encrypted_text, key)
print("Decrypted Text:", decrypted_text)
```
## OUTPUT:

![Screenshot 2024-03-01 153756](https://github.com/IsaacAIML2023/Cryptography---19CS412-classical-techqniques/assets/129837020/df1a492f-6663-4870-a18e-ee3870fcee9b)

## RESULT:
The program is executed successfully
