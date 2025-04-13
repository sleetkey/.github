# Sleet Key
🔐 Alternative near key management and login solutions, rotate and own your keys
<br/>
And use your keys to sign into near dapps and sign transactions

---

### what sleet key is and what it is not
sleet key is an alternative solution for both users and devs to manage their near account keys and to login to apps and to sign transactions. **But sleet key is not the recommend way to do this nor is it a recommendation to manage keys in this way.**
<br/>
Sleet key is a work in progress. Make sure you know what you are doing, and make sure you keep your keys safe. Remember you can always rotate your keys, but no one can hep you if you lose access to your near account key or if you remove your key without adding a new one.

### the very minimum, how you can use sleet key
sleet key can be thought of as a standard way to encrypt your near private key and save it locally on your device, you can do it with a number of different tools. We provide examples using OpenSSL CLI to securely encrypt your private key with a password and store it in a JSON file. You can then use this encrypted key to authenticate with NEAR dApps and un-encrypt with password when you need to sign a transaction.

### how developers can make apps that you can log into with sleet key
Developers can integrate Sleet Key authentication by implementing the following flow:
1. Prompt users to upload their encrypted JSON key file
2. Request the user's decryption password
3. Decrypt the private key using OpenSSL or crypto-js
4. Use the decrypted key to authenticate with NEAR Protocol
5. Implement proper security measures to handle the decrypted key in memory
6. Provide clear instructions for users to rotate their keys if needed


---





---

copyright: 2025 by sleet.near