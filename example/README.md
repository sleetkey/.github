# Examples

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
# Corrected decryption command
ENCRYPTED_KEY=$(jq -r '.private_key' example.near.json)
DECRYPTED_KEY=$(echo "$ENCRYPTED_KEY" | openssl enc -d -aes-256-cbc -pbkdf2 -a -k 'your_password')


# Display the decrypted key
echo "Decrypted private key: $DECRYPTED_KEY"
```


---

copyright: 2025 by sleet.near