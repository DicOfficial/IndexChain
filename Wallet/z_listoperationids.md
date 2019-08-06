## z_listoperationids

**z_listoperationids**

The `z_listoperationids` method returns the list of operation ids currently known to the wallet.

### Arguments

| Name     | Type               | Description                                           |
| -------- | ------------------ | ----------------------------------------------------- |
| "status" | (string, optional) | filter result by the operation's state e.g. "success" |

### Response

| Name          | Type     | Description                             |
| ------------- | -------- | --------------------------------------- |
| "operationid" | (string) | an operation id belonging to the wallet |

#### 📌 Examples

Command:

```bash
./komodo-cli z_listoperationids
```

Show Response

```bash
[
  "opid-47e12224-8477-4cd4-852d-d8c3ddbc6375",
  "opid-b650b582-c2f5-43e0-9a65-9fe23f65c1a5"
]
```

Command:

```bash
./komodo-cli z_listoperationids "success"
```

Show Response

```bash
[
  "opid-47e12224-8477-4cd4-852d-d8c3ddbc6375"
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_listoperationids", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    "opid-47e12224-8477-4cd4-852d-d8c3ddbc6375",
    "opid-b650b582-c2f5-43e0-9a65-9fe23f65c1a5"
  ],
  "error": null,
  "id": "curltest"
}
```