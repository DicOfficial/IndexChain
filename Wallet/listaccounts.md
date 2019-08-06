## listaccounts

**listaccounts ( minconf includeWatchonly )**

DEPRECATED

The **listaccounts** method returns an object that has account names as keys and account balances as values.

### Arguments

| Name             | Type                            | Description                                                  |
| ---------------- | ------------------------------- | ------------------------------------------------------------ |
| minconf          | (numeric, optional, default=1)  | only include transactions with at least this many confirmations |
| includeWatchonly | (bool, optional, default=false) | include balances in watchonly addresses (see 'importaddress') |

### Response

| Name             | Type      | Description                                                  |
| ---------------- | --------- | ------------------------------------------------------------ |
| "account_number" | (numeric) | the property name is the account name, and the value is the total balance for the account |

#### 📌 Examples

Command:

```bash
./komodo-cli listaccounts 6
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listaccounts", "params": [6] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```