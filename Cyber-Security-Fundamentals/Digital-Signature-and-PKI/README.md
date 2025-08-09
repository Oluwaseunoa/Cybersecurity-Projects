

# Understanding and Implementing Digital Signatures and Public Key Distribution

**Author:** Oluwaseun Osunsola  
**Environment:** Kali Linux (CLI-based)  
**Project link:** https://github.com/Oluwaseunoa/Cyber-Security-Projects/tree/main/Cyber-Security-Fundamentals/Steganography-Project

## 📌 Project Objective
The goal of this project is to:
- Understand how **digital signatures** work.
- Learn how to **generate key pairs** using GPG.
- Sign and verify messages using public–private key cryptography.
- Share public keys securely.
- Test the integrity verification feature by detecting tampered messages.

---

## 🛠 Tools Used
- **Operating System:** Kali Linux  
- **Software:** GPG (GNU Privacy Guard)  
- **Text Editor:** nano  
- **Terminal:** Bash Shell

---

## 📂 Project Structure
```

Digital-Signature-and-PKI/
├── img/                          # All project screenshots
├── Temmy_Download/               # Files that Temmy received
├── message.txt                   # Original message file
├── public_key.asc                # Exported public key
├── README.md                     # This project report
└── signed_message.sig            # Signed message file



````

---

## 🧩 Project Steps

### **Step 1: Generate a GPG Key Pair**
We start by generating a public–private key pair.  
Command:
```bash
gpg --full-generate-key
````

![Key Generation Start](./img/1.key_generation1.png)

---

### **Step 2: Choose Key Length**

For stronger encryption, `4096` bits should be chosen but we'll go with the default 3072 bits.
![Key Length Prompt](./img/2.key_lenght_prompt.png)

---

### **Step 3: Set Key Validity Period**

We set the key to be forever valid by choosing **0**.
![Key Validity Period](./img/3.key_validity_period.png)

---

### **Step 4: Identity Construction**

We provided:

* Name: Oluwaseun Osunsola
* Email: `oluwaseun.beicks@gmail.com` 
  ![Identity Construction](./img/4.identity_construction.png)

---

### **Step 5: Final Options and Passphrase Choice**

We confirmed the key type, length, validity, and then set a strong passphrase to protect the private key.
![Final Options & Passphrase](./img/5.keygen_final_options_and_paraphrase_choice.png)

---

### **Step 6: Create a Message**

We created a text file with a confidential message:

```bash
echo "This is a confidential memo from Seun to Temmy" > message.txt
cat message.txt
```

![Create and View Message](./img/6.create_write_into_and_cat_message-txt.png)

---

### **Step 7: Sign the Message**

We signed the message using:

```bash
gpg --armor --output signed_message.sig --sign message.txt
```

This produced a `.sig` file containing the message and its signature.
![Sign Message](./img/7.sign_message.txt.png)

---

### **Step 8: List Keys**

To confirm our key exists in the local GPG keyring:

```bash
gpg --list-keys
```

![List Keys](./img/8.list_keys_to_see.png)

---

### **Step 9: Export Public Key**

We exported the public key linked to our email:

```bash
gpg --armor --export oluwaseun.beicks@gmail.com > public_key.asc
```

![Export Public Key](./img/9.export_public_key.png)

---

### **Step 10: Verify the Key Export**

We checked that the `public_key.asc` file exists and contains the ASCII-armored key.
![Verify Key Was Created](./img/10.verify_the_key_was_created.png)

---

### **Step 11: Send Files to Receiver**

We sent **two files** to Temmy (acting as Alice in this simulation):

* `public_key.asc`
* `signed_message.sig`
  ![Files Sent](./img/11.public_key_and_signed_message_asc_files_sent_to_temmy.png)

---

## 🧩 Receiver's (Temmy’s) Steps

### **Step 12: Download Files**

Temmy downloads both files into her `Downloads` folder.
![Downloads](./img/12.Temmy_downloads_public_key-asc_and%20_signed_message-sig.png)

---

### **Step 13: Open Downloads Folder in Terminal**

She navigates to the Downloads folder via terminal.
![Open in Terminal](./img/13.Temmy_open_in_terminal.png)

---

### **Step 14: Import Public Key**

Temmy imports Oluwaseun’s public key:

```bash
gpg --import public_key.asc
```

![Import Public Key](./img/14.Temmy_export_public_key.png)

---

### **Step 15: Verify the Signature**

Temmy verifies that the signed file was indeed signed by Oluwaseun:

```bash
gpg --verify signed_message.sig
```

![Verify Signature](./img/15.Temmy_verify_the_signature_that_it_was_signed_by_Oluwaseun.png)

---

## 🔍 Integrity Testing

### **Step 16: Open Signed Message**

Temmy opens the signed file in nano.
![Nano Signed Message](./img/16.Temmy_nano_the_signed_message_file.png)

---

### **Step 17: View Signed Message Content**

The content is in ASCII-armored format (encoded and compressed message + signature).
![View Signed Message](./img/17.content_of_signed_message_in_nano.png)

---

### **Step 18: Tamper with the File**

Temmy deletes some characters from the encoded message block.
![Delete Characters](./img/18.Temmy_remove_some_characters_in_first_line.png)

---

### **Step 19: Verify Again — Failure**

After tampering, GPG detects corruption:

```bash
gpg --verify signed_message.sig
```

Output:

```
gpg: CRC error...
gpg: the signature could not be verified.
```

![Bad Signature Result](./img/19.bad_signature_result_due_to_deleted_character.png)

This confirms that **any alteration** to the signed content invalidates the signature.

---

## 📊 Learning Outcomes

* Learned how to **generate GPG keys** securely.
* Understood **public–private key encryption** and **digital signatures**.
* Practiced **signing** and **verifying** messages.
* Understood the importance of **key sharing** and **integrity verification**.
* Saw how **tampering** invalidates a signature.

---

## 💡 Real-World Applications

* **Secure email signing** (PGP, S/MIME)
* **Software distribution** (verifying signed binaries)
* **Git commit signing** (to prevent commit forgery)
* **Document authenticity checks** (contracts, agreements)

---


