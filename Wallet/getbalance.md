## getbalance

**getbalance ( "account" minconf includeWatchonly )**

The `getbalance` method returns the server's total available balance.

The **account** input is deprecated.

### Arguments

| Name             | Type                            | Description                                                  |
| ---------------- | ------------------------------- | ------------------------------------------------------------ |
| "account"        | (string, optional)              | DEPRECATED if provided, it MUST be set to the empty string `""` or to the string `"*"` |
| minconf          | (numeric, optional, default=1)  | only include transactions confirmed at least this many times |
| includeWatchonly | (bool, optional, default=false) | also include balance in watchonly addresses (see `importaddress`) |

### Response

| Name   | Type      | Description      |
| ------ | --------- | ---------------- |
| amount | (numeric) | the total amount |

#### 📌 Examples

The total amount in the wallet:

Command:

```bash
./komodo-cli getbalance
```

Show Response

```bash
10.05000000
```

The total amount in the wallet where at least five blocks are confirmed:

Command:

```bash
./komodo-cli getbalance "*" 5
```

Show Response

```bash
10.05000000
```

As a json rpc call:

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getbalance", "params": ["", 6] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": 10.09234883,
  "error": null,
  "id": "curltest"
}
```