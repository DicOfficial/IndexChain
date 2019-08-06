## lockunspent

**lockunspent unlock [{ "txid": "txid", "vout": n }, ... ]**

The `lockunspent` method locks (unlock = `false`) or unlocks (unlock = `true`) specified transaction outputs. A locked transaction output will not be chosen by automatic coin selection, when spending the relevant coin. The locks are stored in memory only; at runtime a node always starts with zero locked outputs, and the locked output list is always cleared when a node stops or fails.

See the **listunspent** and **listlockunspent** calls to determine local transaction state and info.

### Arguments

| Name   | Type                | Description                                                  |
| ------ | ------------------- | ------------------------------------------------------------ |
| unlock | (boolean, required) | whether to unlock (true) or lock (false) the specified transactions |
| "txid" | (string)            | the transaction id                                           |
| "vout" | (numeric)           | the output number                                            |

### Response

| Name       | Type      | Description                        |
| ---------- | --------- | ---------------------------------- |
| true/false | (boolean) | whether the command was successful |

#### 📌 Examples

Command:

```bash
./komodo-cli lockunspent false '[{"txid":"d7ba45296c66e16eb61f27a4eef8848c7f5579fe801f277c1b0e074a4f47d6fd","vout":0}]'
```

Show Response

```bash
true
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "lockunspent", "params": [false, [{"txid":"d7ba45296c66e16eb61f27a4eef8848c7f5579fe801f277c1b0e074a4f47d6fd","vout":0}]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": true,
  "error": null,
  "id": "curltest"
}
```