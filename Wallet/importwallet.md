## importwallet

**importwallet "filename"**

The `importwallet` method imports transparent-address keys from a wallet-dump file (see [dumpwallet](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#dumpwallet)).

### Arguments

| Name       | Type               | Description     |
| ---------- | ------------------ | --------------- |
| "filename" | (string, required) | the wallet file |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli importwallet "path/to/exportdir/nameofbackup"
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "importwallet", "params": ["path/to/exportdir/nameofbackup"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": null,
  "error": null,
  "id": "curltest"
}
```