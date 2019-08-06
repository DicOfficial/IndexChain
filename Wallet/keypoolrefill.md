## keypoolrefill

**keypoolrefill ( newsize )**

The `keypoolrefill` method refills the keypool.

### Arguments

| Name    | Type                             | Description          |
| ------- | -------------------------------- | -------------------- |
| newsize | (numeric, optional, default=100) | the new keypool size |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli keypoolrefill
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli keypoolrefill 100
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "keypoolrefill", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": null,
  "error": null,
  "id": "curltest"
}
```