## importaddress

**importaddress "address" ( "label" rescan )**

The `importaddress` method adds an address or script (in hex) that can be watched as if it were in your wallet, although it cannot be used to spend.

This call can take an increased amount of time to complete if rescan is true.

### Arguments

| Name      | Type                              | Description                        |
| --------- | --------------------------------- | ---------------------------------- |
| "address" | (string, required)                | the address to watch               |
| "label"   | (string, optional, default="")    | an optional label                  |
| rescan    | (boolean, optional, default=true) | rescan the wallet for transactions |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Import an address with rescan:

Command:

```bash
./komodo-cli importaddress "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN"
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli importaddress "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN" "testing" false
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "importaddress", "params": ["R9z796AehK5b6NCPeVkGUHSpJnawerf8oP", "testing", false] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": null,
  "error": null,
  "id": "curltest"
}
```