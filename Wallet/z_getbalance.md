## z_getbalance

**z_getbalance "address" ( minconf )**

The `z_getbalance` method returns the balance of a t address or z address belonging to the node’s wallet.

CAUTION: If **address** is a watch-only z address, the returned balance may be larger than the actual balance, as spends cannot be detected with incoming viewing keys.

### Arguments

| Name      | Type                           | Description                                                  |
| --------- | ------------------------------ | ------------------------------------------------------------ |
| "address" | (string)                       | the selected z or t address                                  |
| minconf   | (numeric, optional, default=1) | only include transactions confirmed at least this many times |

### Response

| Name   | Type      | Description                                                  |
| ------ | --------- | ------------------------------------------------------------ |
| amount | (numeric) | the total amount received at this address (in the relevant COIN value) |

#### 📌 Examples

The total amount received by address "myaddress" at least 5 blocks confirmed

Command:

```bash
./komodo-cli z_getbalance "ztfF6SFBfq2qha73dAgsXnL86F8air32CXKxJg8aYtEPJFdLcw4y3zWzBasocnx1V9GLnnFeKnkPvkScjNkQBfWn2kBDmkn"
```

Show Response

```bash
0.01980000
```

Command:

```bash
./komodo-cli z_getbalance "ztfF6SFBfq2qha73dAgsXnL86F8air32CXKxJg8aYtEPJFdLcw4y3zWzBasocnx1V9GLnnFeKnkPvkScjNkQBfWn2kBDmkn" 5
```

Show Response

```bash
0.01980000
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_getbalance", "params": ["ztfF6SFBfq2qha73dAgsXnL86F8air32CXKxJg8aYtEPJFdLcw4y3zWzBasocnx1V9GLnnFeKnkPvkScjNkQBfWn2kBDmkn", 5] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": 0.0198,
  "error": null,
  "id": "curltest"
}
```