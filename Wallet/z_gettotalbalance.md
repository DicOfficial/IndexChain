## z_gettotalbalance

**z_gettotalbalance ( minconf includeWatchonly )**

The `z_gettotalbalance` method returns the total value of funds, including both transparent and private, stored in the node’s wallet.

CAUTION: If the wallet contains watch-only z addresses the returned private balance may be larger than the actual balance, as spends cannot be detected with incoming viewing keys.

While the **interest** property is returned for all KMD-based coin daemons, only the main KMD chain utilizes the interest feature. KMD-based asset chains will always return a **0.00** interest value.

### Arguments

| Name             | Type                            | Description                                                  |
| ---------------- | ------------------------------- | ------------------------------------------------------------ |
| minconf          | (numeric, optional, default=1)  | only include private and transparent transactions confirmed at least this many times |
| includeWatchonly | (bool, optional, default=false) | also include balance in watchonly addresses (see 'importaddress' and 'z_importviewingkey') |

### Response

| Name          | Type      | Description                                             |
| ------------- | --------- | ------------------------------------------------------- |
| "transparent" | (numeric) | the total balance of transparent funds                  |
| "interest"    | (numeric) | the total balance of unclaimed interest earned          |
| "private"     | (numeric) | the total balance of private funds                      |
| "total"       | (numeric) | the total balance of both transparent and private funds |

#### 📌 Examples

Command:

```bash
./komodo-cli z_gettotalbalance
```

Show Response

```json
{
  "transparent": "9.98794883",
  "interest": "0.00",
  "private": "0.08205",
  "total": "10.06999883"
}
```

Command:

```bash
./komodo-cli z_gettotalbalance 5
```

Show Response

```json
{
  "transparent": "9.98794883",
  "interest": "0.00",
  "private": "0.08205",
  "total": "10.06999883"
}
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_gettotalbalance", "params": [5] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": {
    "transparent": "0.00615",
    "interest": "0.00",
    "private": "0.06205",
    "total": "0.0682"
  },
  "error": null,
  "id": "curltest"
}
```