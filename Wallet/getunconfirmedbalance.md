## getunconfirmedbalance

**getunconfirmedbalance**

The `getunconfirmedbalance` method returns the server's total unconfirmed balance.

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
./komodo-cli getunconfirmedbalance
```

Show Response

```bash
10.05000000
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getunconfirmedbalance", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": 10.05,
  "error": null,
  "id": "curltest"
}
```