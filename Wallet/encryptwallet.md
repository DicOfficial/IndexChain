## encryptwallet

**encryptwallet "passphrase"**

Using the `encryptwallet` method will shutdown the Indexchain daemon (`indexchain`).

This feature is available only on chains where `-ac_public` is enabled. Chains that feature private transactions cannot use this feature.

The `encryptwallet` method encrypts the wallet with the indicated `passphrase`.

This method is for first-time encryption only. After the first encryption, any calls that interact with private keys will require the passphrase via walletpassphrase prior to calling the corresponding method. This includes methods that create a transaction, dump a private key for an address, sign a transaction, etc.

### Arguments

| Name       | Type     | Description                                                  |
| ---------- | -------- | ------------------------------------------------------------ |
| passphrase | (string) | the passphrase for wallet encryption; the passphrase must be at least 1 character, but should be many |

### Response

| Text Response                                                |
| ------------------------------------------------------------ |
| wallet encrypted; Indexchain server stopping, restart to run with encrypted wallet. The keypool has been flushed, you need to make a new backup. |

#### 📌 Examples

##### Encrypt your wallet

Command:

```bash
./komodo-cli encryptwallet "mypassphrase"
```

Show Response

```bash
wallet encrypted; Komodo server stopping, restart to run with encrypted wallet. The keypool has been flushed, you need to make a new backup.
```

##### Unlock the wallet for 60 seconds

Command:

```bash
./komodo-cli walletpassphrase "mypassphrase" 60
```

Show Response

```bash
(disabled)
```

##### Lock the wallet again by removing the passphrase

Command:

```bash
./komodo-cli walletlock
```

Show Response

```bash
(No response)
```

As a json rpc call:

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "encryptwallet", "params": ["mypassphrase"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
{
    "result":"wallet encrypted; Komodo server stopping, restart to run with encrypted wallet. The keypool has been flushed, you need to make a new backup.",
    "error":null,
    "id":"curltest"
}
```