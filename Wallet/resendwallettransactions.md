## resendwallettransactions

**resendwallettransactions**

The `resendwallettransactions` method immediately re-broadcasts unconfirmed wallet transactions to all peers. This method is intended only for testing; the wallet code periodically re-broadcasts automatically.

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name             | Type     | Description                                    |
| ---------------- | -------- | ---------------------------------------------- |
| "transaction_id" | (string) | an array of the rebroadcasted transaction id's |

#### 📌 Examples

Command:

```bash
./komodo-cli resendwallettransactions
```

Show Response

```bash
[
  "4e847051279ead30fb2d8d53cc0d4649f62c85a44b23f90152d2ef4ed6af2006"
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "resendwallettransactions", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    "4e847051279ead30fb2d8d53cc0d4649f62c85a44b23f90152d2ef4ed6af2006"
  ],
  "error": null,
  "id": "curltest"
}
```