## move

**move "fromaccount" "toaccount" amount ( minconf "comment" )**

DEPRECATED

The `move` method moves a specified amount from one account in your wallet to another.

### Arguments

| Name          | Type                           | Description                                                  |
| ------------- | ------------------------------ | ------------------------------------------------------------ |
| "fromaccount" | (string, required)             | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |
| "toaccount"   | (string, required)             | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |
| amount        | (numeric)                      | the quantity to move between accounts                        |
| minconf       | (numeric, optional, default=1) | only use funds with at least this many confirmations         |
| "comment"     | (string, optional)             | an optional comment, stored in the wallet only               |

### Response

| Name       | Type      | Description        |
| ---------- | --------- | ------------------ |
| true/false | (boolean) | true if successful |

#### 📌 Examples

Command:

```bash
./komodo-cli move "" "tabby" 0.01
```

Show Response

```bash
(deprecated)
```

Command:

```bash
./komodo-cli move "timotei" "akiko" 0.01 6 "happy birthday!"
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "move", "params": ["timotei", "akiko", 0.01, 6, "happy birthday!"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```