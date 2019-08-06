## settxfee

**settxfee amount**

The `settxfee` method sets the transaction fee per kB.

### Arguments

| Name   | Type                | Description                                                  |
| ------ | ------------------- | ------------------------------------------------------------ |
| amount | (numeric, required) | the transaction fee in COIN/kB rounded to the nearest 0.00000001 |

### Response

| Name       | Type      | Description                |
| ---------- | --------- | -------------------------- |
| true/false | (boolean) | returns true if successful |

#### 📌 Examples

Command:

```bash
./komodo-cli settxfee 0.00001
```

Show Response

```bash
true
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "settxfee", "params": [0.00001] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": true,
  "error": null,
  "id": "curltest"
}
```