## walletpassphrasechange

**walletpassphrasechange "oldpassphrase" "newpassphrase"**

The `walletpassphrasechange` method is neither active nor visible in the `help` method until the [encryptwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#encryptwallet) passphrase is set.

This feature is available only on chains where `-ac_public` is enabled. Chains that feature private transactions cannot use this feature.

The `walletpassphrasechange` method changes `"oldpassphrase"` to `"newpassphrase"`.

### Arguments

| Name            | Type     | Description        |
| --------------- | -------- | ------------------ |
| "oldpassphrase" | (string) | the old passphrase |
| "newpassphrase" | (string) | the new passphrase |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli walletpassphrasechange "oldpassphrase" "newpassphrase"
```

Show Response

```bash
(none)
```