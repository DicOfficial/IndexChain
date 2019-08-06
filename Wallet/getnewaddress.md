## getnewaddress

**getnewaddress ( "account" )**

The `getnewaddress` method returns a new address for receiving payments.

### Arguments

| Name      | Type               | Description                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| "account" | (string, optional) | DEPRECATED: If provided, the account MUST be set to the empty string `""` to represent the default account; passing any other string will result in an error |

### Response

| Name      | Type     | Description     |
| --------- | -------- | --------------- |
| "address" | (string) | the new address |

#### 📌 Examples

Command:

```bash
./komodo-cli getnewaddress
```

Show Response

```bash
"RYDuQ2oQCCz1PQNxUQTDAaRinWKiCoT2E6"
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getnewaddress", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "R9iQRG6J9eY8SwaCcYZ65QJxg5UhgLC5Rx",
  "error": null,
  "id": "curltest"
}
```