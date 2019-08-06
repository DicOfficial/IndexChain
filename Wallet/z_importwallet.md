## z_importwallet

**z_importwallet "filename"**

The `z_importwallet` method imports t address and z address keys from a wallet export file.

See also **z_exportwallet**.

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
./komodo-cli z_importwallet "/mydirectory/nameofbackup"
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_importwallet", "params": ["/mydirectory/nameofbackup"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": null,
  "error": null,
  "id": "curltest"
}
```