## zcrawreceive zcsecretkey encryptednote

**zcrawreceive zcsecretkey encryptednote**

DEPRECATED.

Decrypts `encryptednote` and checks if the coin commitments are in the blockchain as indicated by the "exists" result.

Output:

```json
{
  "amount": value,
  "note": noteplaintext,
  "exists": exists
}
```