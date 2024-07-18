# Full name: Vo Thi Huynh Huong 19110084

# Lab 11: Encrypt and Decrypt Text file

## Task 4.1:  Encrypt and Decrypt Text file

- Step 01: Create text file named plain.txt with content: “My name is Huong”:

  ![Pic1](https://github.com/user-attachments/assets/b41f0d9d-50f5-414f-803f-60e15d4ff839)

- Step 02: To encrypt file plain.txt in aes-256 bit in cbc with key K:

  ![Pic2](https://github.com/user-attachments/assets/248a36a6-697f-4ebb-abe0-95b68240a7f4)
  
  ![Pic3](https://github.com/user-attachments/assets/58ff5075-8882-462e-b7c4-2cccaeba32fa)

- Step 03: To decrypt:

  ![Pic4](https://github.com/user-attachments/assets/e450297e-e9aa-4c03-a973-1d6fccf2c519)

- Step 04: For cbc:

  ![Pic5](https://github.com/user-attachments/assets/cef59ad6-e486-48ef-a196-48b28ae50fc6)

## Task 4.2:  Encryption Mode – ECB vs. CBC

```sh
    dd if=origin.bmp of=header.bin bs=1 count=54
 ```

  <img width="227" alt="Pic7" src="https://github.com/user-attachments/assets/ad580db9-226c-40f8-9cdd-8ce1201d8886">

```sh
    dd if=origin.bmp of=body.bin bs=1 skip=54
 ```

<img width="294" alt="Pic9" src="https://github.com/user-attachments/assets/d1631802-51b4-42c9-8a82-b955ed2e7537">

```sh
    openssl enc -aes-256-cbc -nosalt -in body.bin -out encrypted_body.bin -K [KEY] -iv [IV]
 ```

<img width="302" alt="Pic11" src="https://github.com/user-attachments/assets/c05ad747-680e-4bb2-b78c-299a5dbaf9cc">

```sh
    cat header.bin encrypted_body.bin > partially_encrypted.bmp
 ```
- Using the CBC (Cipher Block Chaining) to encrypt file:

Open the partically_encrypted.bmp file:

<img width="538" alt="Pic12" src="https://github.com/user-attachments/assets/1270a501-33fe-431a-ac07-4aa544ebddfc">

Looking at the image above, we can see that when encoding an image, the structure from the original image is sometimes still visible. Because the CBC mode guarantees that even identical plaintext blocks will produce different encrypted blocks due to the chaining mechanism.

- Using the ECB (Electronic Code Book) to encrypt file:

 Open the partically_encrypted_ecb.bmp file we see:
 
 <img width="538" alt="Pic13" src="https://github.com/user-attachments/assets/cf08a1c8-719a-46f6-b5f0-f77739c32ebb">

 Looking at the image above, we can see that when encoding an image, the structure from the original image is sometimes still visible. This occurs because ECB mode does not 
 offer adequate security for data containing repetitive patterns. Identical plaintext blocks are encrypted into identical ciphertext blocks, potentially exposing patterns 
 and allowing for some degree of reverse engineering of the original data.

+ In ECB mode, the encrypted image retains recognizable patterns that can reveal visual details of the original image, highlighting its unsuitability for encrypting images or data with repetitive patterns.

+ In contrast, CBC mode produces encrypted images that appear random and do not disclose any meaningful information about the original image, underscoring its ability to provide higher security and confidentiality for such data.
