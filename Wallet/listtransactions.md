## listtransactions

**listtransactions ( "account" count from includeWatchonly )**

The `listtransactions` method returns up to `count` most recent transactions skipping the first `from` transactions for `account`.

### Arguments

| Name             | Type                            | Description                                                  |
| ---------------- | ------------------------------- | ------------------------------------------------------------ |
| "account"        | (string, optional)              | DEPRECATED the account name; should be `"*"`                 |
| count            | (numeric, optional, default=10) | the number of transactions to return                         |
| from             | (numeric, optional, default=0)  | the number of transactions to skip                           |
| includeWatchonly | (bool, optional, default=false) | include transactions to watchonly addresses (see `importaddress`) |

### Response

| Name               | Type      | Description                                                  |
| ------------------ | --------- | ------------------------------------------------------------ |
| "account"          | (string)  | DEPRECATED the account name associated with the transaction; it will be "" for the default account |
| "address"          | (string)  | the address of the transaction; not present for move transactions (category = move) |
| "category"         | (string)  | The transaction category. This property can be `send`        |
| "amount"           | (numeric) | The amount. This value is negative for the `send`category, and for the `move` category for moves outbound. It is positive for the `receive` category and for the `move` category for inbound funds. |
| "vout"             | (numeric) | the vout value                                               |
| "fee"              | (numeric) | the amount of the fee; this is negative and only available for the `send` category of transactions |
| "confirmations"    | (numeric) | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations" | (numeric) | the raw confirmations of the transaction; available for `send` and `receive` category of transactions (number of blocks on top of this transaction's block) |
| "blockhash"        | (string)  | the block hash containing the transaction; available for the `send` and `receive` categories of transactions |
| "blockindex"       | (numeric) | the block index containing the transaction; available for the `send` and `receive` categories of transactions |
| "txid"             | (string)  | the transaction id; available for the `send` and `receive` categories of transactions |
| "time"             | (numeric) | the transaction time in seconds since epoch (midnight Jan 1 1970 GMT) |
| "timereceived"     | (numeric) | the time received in seconds since epoch (midnight Jan 1 1970 GMT); available for the `send`and `receive` categories of transactions |
| "comment"          | (string)  | whether a comment is associated with the transaction         |
| "otheraccount"     | (string)  | for the `move` category of transactions; indicates the account which sent the funds (for receiving funds, positive amounts), or went to (for sending funds, negative amounts) |
| "size"             | (numeric) | transaction size in bytes                                    |

#### 📌 Examples

Command:

```bash
./komodo-cli listtransactions
```

Show Response

```json
[
  {
    "account": "",
    "address": "RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs",
    "category": "generate",
    "amount": 0.00010000,
    "vout": 0,
    "rawconfirmations": 99,
    "confirmations": 99,
    "generated": true,
    "blockhash": "0eb4edeb5141a7670ef8be413873e1bef4f6f321867a2b8d67a616cdc7df1e77",
    "blockindex": 0,
    "blocktime": 1536976212,
    "expiryheight": 0,
    "txid": "3041aa7374e530d4d28e14620dd2bb9d2ff0bf71dd1106f08bc9f02fce44598e",
    "walletconflicts": [
    ],
    "time": 1536976211,
    "timereceived": 1536976211,
    "vjoinsplit": [
    ],
    "size": 99
  }
  , ... (9 responses ommitted from documentation for brevity)
]
```

Command:

```bash
./komodo-cli listtransactions "*" 20 100
```

Show Response

```json
[
  {
    "account": "",
    "address": "RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs",
    "category": "generate",
    "amount": 0.00010000,
    "vout": 0,
    "rawconfirmations": 99,
    "confirmations": 99,
    "generated": true,
    "blockhash": "0eb4edeb5141a7670ef8be413873e1bef4f6f321867a2b8d67a616cdc7df1e77",
    "blockindex": 0,
    "blocktime": 1536976212,
    "expiryheight": 0,
    "txid": "3041aa7374e530d4d28e14620dd2bb9d2ff0bf71dd1106f08bc9f02fce44598e",
    "walletconflicts": [
    ],
    "time": 1536976211,
    "timereceived": 1536976211,
    "vjoinsplit": [
    ],
    "size": 99
  }
  , ... (9 responses ommitted from documentation for brevity)
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listtransactions", "params": ["*", 20, 100] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  [
    {
      "account": "",
      "address": "RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs",
      "category": "generate",
      "amount": 0.0001,
      "vout": 0,
      "rawconfirmations": 99,
      "confirmations": 99,
      "generated": true,
      "blockhash": "0eb4edeb5141a7670ef8be413873e1bef4f6f321867a2b8d67a616cdc7df1e77",
      "blockindex": 0,
      "blocktime": 1536976212,
      "expiryheight": 0,
      "txid": "3041aa7374e530d4d28e14620dd2bb9d2ff0bf71dd1106f08bc9f02fce44598e",
      "walletconflicts": [],
      "time": 1536976211,
      "timereceived": 1536976211,
      "vjoinsplit": [],
      "size": 99
    }
    , ... (9 responses ommitted from documentation for brevity)
  ],
  "error": null,
  "id": "curltest"
}
```