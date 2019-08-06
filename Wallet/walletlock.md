## walletlock

**walletlock**

The `walletlock` method is neither active nor visible in the `help` method until the [encryptwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#encryptwallet) passphrase is set.

This feature is available only on chains where `-ac_public` is enabled. Chains that feature private transactions cannot use this feature.

The `walletlock` method re-locks a wallet that has a passphrase enabled via [encryptwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#encryptwallet).

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli walletlock
```

Show Response

```bash
(none)
```