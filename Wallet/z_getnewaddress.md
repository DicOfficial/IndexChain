## z_getnewaddress

**z_getnewaddress**

The `z_getnewaddress` method returns a new z_address for receiving payments.

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name        | Type     | Description       |
| ----------- | -------- | ----------------- |
| "z_address" | (string) | the new z_address |

#### 📌 Examples

Command:

```bash
./komodo-cli z_getnewaddress
```

Show Response

```bash
ztbUD83kXgHt3A1M282wFvT9Ms6SiBCd6GSbQbPa2C7UtPojVZjPENytFqu7JxgnsgL9EN42xWnyhhzniHYSRJDnEPTgo3Y
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_getnewaddress", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "ztci8RzNSo2pdiDpAeHpz9Rp91hq12Mn7zcFfBR8Jjs2ydZUCTw8rLZzkVP888M4vGezpZVfsTR8orgxYK3N8gdgbBzakx3",
  "error": null,
  "id": "curltest"
}
```