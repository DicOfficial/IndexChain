## getrawchangeaddress

**getrawchangeaddress**

The `getrawchangeaddress` returns a new address that can be used to receive change.

This is for use with raw transactions, NOT normal use.

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name      | Type     | Description |
| --------- | -------- | ----------- |
| "address" | (string) | the address |

#### 📌 Examples

Command:

```bash
./komodo-cli getrawchangeaddress
```

Show Response

```bash
RS8oqzbjShKhftmuk2RpRmHH2hTAukp6yP
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getrawchangeaddress", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN",
  "error": null,
  "id": "curltest"
}
```