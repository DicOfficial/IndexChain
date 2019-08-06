## listlockunspent

**listlockunspent**

The `listlockunspent` method returns a list of temporarily non-spendable outputs.

See the **lockunspent** call to lock and unlock transactions for spending.

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name   | Type      | Description               |
| ------ | --------- | ------------------------- |
| "txid" | (string)  | the transaction id locked |
| "vout" | (numeric) | the vout value            |

#### 📌 Examples

Command:

```bash
./komodo-cli listlockunspent
```

Show Response

```json
[
  {
    "txid": "d7ba45296c66e16eb61f27a4eef8848c7f5579fe801f277c1b0e074a4f47d6fd",
    "vout": 0
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listlockunspent", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "txid": "d7ba45296c66e16eb61f27a4eef8848c7f5579fe801f277c1b0e074a4f47d6fd",
      "vout": 0
    }
  ],
  "error": null,
  "id": "curltest"
}
```