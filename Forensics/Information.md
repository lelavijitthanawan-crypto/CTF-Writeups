# CTF Write-ups

A collection of walkthroughs and write-ups for Cybersecurity Capture The Flag (CTF) challenges, focusing on technical methodology, tooling, and digital forensics.

---

## 📌 Forensics

### Challenge: Information
* **Platform:** CyLab Security Academy / picoCTF
* **Category:** Forensics
* **Difficulty:** Easy

#### Description
The challenge requires finding a hidden flag inside the provided image file `cat.jpg`.

#### Walkthrough

1. **Navigate to the Directory**  
   Move into the directory where the challenge file was downloaded:
   ```bash
   cd Downloads
   ```

2. **Inspect Metadata**
   Use exiftool to inspect the embedded metadata of the image:
   ```bash
    exiftool cat.jpg
    ```

3. **Analyze the Output**
   A suspicious string is found under the License metadata field:
   ```text
   YWNhZGVteXt0aGVfbTN0YWRhdGFfMXNfbXk4aWZpZWR9
   ```
   The pattern and character set indicate that this string is Base64 encoded.

5. **Decode the Flag**
   Decode the Base64 string to obtain the cleartext flag:
   ```bash
   echo "YWNhZGVteXt0aGVfbTN0YWRhdGFfMXNfbXk4aWZpZWR9" | base64 -d
   ```

   ### Flag:
   `academy{the_m3tadata_1s_********}`
