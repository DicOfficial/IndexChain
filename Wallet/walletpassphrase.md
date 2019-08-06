## walletpassphrase

**walletpassphrase "passphrase" (timeout)**

The `walletpassphrase` method is neither active nor visible in the `help` method until the [encryptwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#encryptwallet) passphrase is set.

This feature is available only on chains where `-ac_public` is enabled. Chains that feature private transactions cannot use this feature.

The `walletpassphrase` method unlocks the wallet using the passphrase that was set by the [encryptwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#encryptwallet) method.

The `timeout` argument can be included to limit the length of time (in seconds) the wallet will remain unlocked.

### Arguments

| Name         | Type                          | Description                                                  |
| ------------ | ----------------------------- | ------------------------------------------------------------ |
| "passphrase" | (string)                      | the passphrase that was set by the `encryptwallet` method    |
| timeout      | (number in seconds, optional) | the amount of time for which the wallet should remember the passphrase |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli walletpassphrase
```

Show Response

```bash
(none)
```