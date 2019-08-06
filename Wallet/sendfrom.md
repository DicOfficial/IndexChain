## sendfrom

**sendfrom "account" "address" amount ( minconf "comment" "comment-to" )**

DEPRECATED: Use **sendtoaddress** instead.

The `sendfrom` method sends an amount from `account` to `address`.

### Arguments

| Name         | Type                           | Description                                                  |
| ------------ | ------------------------------ | ------------------------------------------------------------ |
| "account"    | (string, required)             | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |
| "address"    | (string, required)             | the address to receive funds                                 |
| amount       | (numeric, required)            | the amount (transaction fee not included)                    |
| minconf      | (numeric, optional, default=1) | only use funds with at least this many confirmations         |
| "comment"    | (string, optional)             | a comment used to store what the transaction is for; this is not part of the transaction, just kept in your wallet |
| "comment-to" | (string, optional)             | an optional comment to store the name of the person or organization to which you're sending the transaction; this is not part of the transaction, it is only kept in your wallet |

### Response

| Name             | Type     | Description        |
| ---------------- | -------- | ------------------ |
| "transaction_id" | (string) | the transaction id |

#### 📌 Examples

Command:

```bash
./komodo-cli sendfrom "" "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu" 0.01
```

Show Response

```bash
(deprecated)
```

Command:

```bash
./komodo-cli sendfrom "tabby" "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu" 0.01 6 "donation" "seans outpost"
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "sendfrom", "params": ["tabby", "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu", 0.01, 6, "donation", "seans outpost"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```