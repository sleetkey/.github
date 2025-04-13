# Examples (outdated)

feilds
- near_account_id
- public_key
- private_key
- network_id - testnet, mainent


```json
{
    "near_account_id": "example.near",
    "public_key": "ed25519:PUBLIC_KEY_HERE",
    "private_key": "encrypted private key", // ed25519:PRIVATE_KEY_HERE
    "network_id": "mainnet"
}
```

### Using OpenSSL CLI

```sh
sudo apt install openssl  # Debian-based (Ubuntu)
brew install openssl      # macOS (Homebrew)
```

```sh
# Encrypt the private key directly
ENCRYPTED_KEY=$(echo -n "ed25519:PRIVATE_KEY_HERE" | openssl enc -aes-256-cbc -salt -pbkdf2 -a -k 'your_password')

# Update the JSON file with the encrypted key
jq --arg encrypted_key "$ENCRYPTED_KEY" '.private_key = $encrypted_key' example.near.json > temp.json && mv temp.json example.near.json
```

```sh
# Extract and decrypt the private key
ENCRYPTED_KEY=$(jq -r '.private_key' example.near.json)
DECRYPTED_KEY=$(echo "$ENCRYPTED_KEY" | openssl enc -d -aes-256-cbc -pbkdf2 -a -k 'your_password')


# Display the decrypted key
echo "Decrypted private key: $DECRYPTED_KEY"
```

---

# Outdated:
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

copyright: 2025 by sleet.near