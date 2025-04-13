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
    "private_key": "ed25519:PRIVATE_KEY_HERE",
    "network_id": "mainnet" // optional
}
```

### Using OpenSSL

```sh
sudo apt install openssl  # Debian-based (Ubuntu)
brew install openssl      # macOS (Homebrew)
```

```sh
# To encrypt
openssl enc -aes-256-cbc -salt -pbkdf2 -in example.near.json -out example.near.enc -k 'your_password'
# To decrypt
openssl enc -d -aes-256-cbc -pbkdf2 -in example.near.enc -out example.near.json -k 'your_password'
```


---

copyright: 2025 by sleet.near