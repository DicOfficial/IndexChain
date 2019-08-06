## z_exportwallet

**z_exportwallet "filename"**

The `z_exportwallet` method exports all wallet keys, including both t address and z address types, in a human-readable format. Overwriting an existing file is not permitted.

### Arguments

| Name       | Type               | Description                                                  |
| ---------- | ------------------ | ------------------------------------------------------------ |
| "filename" | (string, required) | the filename, saved to the directory indicated by the [exportdir](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#exportdir) parameter at daemon runtime (required) |

### Response

| Name   | Type     | Description                           |
| ------ | -------- | ------------------------------------- |
| "path" | (string) | the full path of the destination file |

#### 📌 Examples

Command:

```bash
./komodo-cli z_exportwallet "test"
```

Show Response

```bash
/home/myusername/mydirectory/test
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_exportwallet", "params": ["test"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "/home/myusername/mydirectory/test",
  "error": null,
  "id": "curltest"
}
```