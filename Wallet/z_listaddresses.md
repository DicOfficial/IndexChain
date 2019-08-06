## z_listaddresses

**z_listaddresses ( includeWatchonly )**

The `z_listaddresses` method returns the list of z addresses belonging to the wallet.

See also **z_importviewingkey**.

### Arguments

| Name             | Type                            | Description                      |
| ---------------- | ------------------------------- | -------------------------------- |
| includeWatchonly | (bool, optional, default=false) | also include watchonly addresses |

### Response

| Name        | Type     | Description                         |
| ----------- | -------- | ----------------------------------- |
| "z_address" | (string) | a z address belonging to the wallet |

#### 📌 Examples

Command:

```bash
./komodo-cli z_listaddresses
```

Show Response

```json
[
  "ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP",
  "ztbUD83kXgHt3A1M282wFvT9Ms6SiBCd6GSbQbPa2C7UtPojVZjPENytFqu7JxgnsgL9EN42xWnyhhzniHYSRJDnEPTgo3Y"
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_listaddresses", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    "ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP",
    "ztbUD83kXgHt3A1M282wFvT9Ms6SiBCd6GSbQbPa2C7UtPojVZjPENytFqu7JxgnsgL9EN42xWnyhhzniHYSRJDnEPTgo3Y"
  ],
  "error": null,
  "id": "curltest"
}
```