# EX-8-ADVANCED-ENCRYPTION-STANDARD ALGORITHM
# Aim:
To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

# ALGORITHM:
AES is based on a design principle known as a substitution–permutation.
AES does not use a Feistel network like DES, it uses variant of Rijndael.
It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits.
AES operates on a 4 × 4 column-major order array of bytes, termed the state
# PROGRAM:
```
#include <stdio.h>
#include <string.h>

void simpleAESEncrypt(char *plaintext, char *key,
                      unsigned char *ciphertext, int len)
{
    int i;

    for (i = 0; i < len; i++)
    {
        ciphertext[i] = plaintext[i] ^ key[i % strlen(key)];
    }
}

void simpleAESDecrypt(unsigned char *ciphertext, char *key,
                      char *decryptedText, int len)
{
    int i;

    for (i = 0; i < len; i++)
    {
        decryptedText[i] = ciphertext[i] ^ key[i % strlen(key)];
    }

    decryptedText[len] = '\0';
}

void printASCII(unsigned char *ciphertext, int len)
{
    printf("Encrypted Message (ASCII values): ");

    for (int i = 0; i < len; i++)
    {
        printf("%d ", ciphertext[i]);
    }

    printf("\n");
}

int main()
{
    char plaintext[100], key[100], decryptedText[100];
    unsigned char ciphertext[100];
    int len;

    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0';

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0';

    if (strlen(key) == 0)
    {
        printf("Key cannot be empty.\n");
        return 1;
    }

    len = strlen(plaintext);

    simpleAESEncrypt(plaintext, key, ciphertext, len);

    printASCII(ciphertext, len);

    simpleAESDecrypt(ciphertext, key, decryptedText, len);

    printf("Decrypted Message: %s\n", decryptedText);

    return 0;
}
```

# OUTPUT:
<img width="926" height="387" alt="image" src="https://github.com/user-attachments/assets/c9afad49-d7f3-4987-8e97-c86939ef9f8e" />


# RESULT:
Thus The program is executed successfully


