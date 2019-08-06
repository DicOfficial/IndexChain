## backupwallet

**backupwallet "destination"**

The `backupwallet` method safely copies the `wallet.dat` file to the indicated destination. The `destination` input accepts only alphanumeric characters.

This method requires that the coin daemon have the **exportdir** runtime parameter enabled.

### Arguments

| Name          | Type               | Description                                                  |
| ------------- | ------------------ | ------------------------------------------------------------ |
| "destination" | (string, required) | the destination filename, saved in the directory set by the [exportdir](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#exportdir) runtime parameter |

### Response

| Name   | Type     | Description                           |
| ------ | -------- | ------------------------------------- |
| "path" | (string) | the full path of the destination file |

#### Examples

```bash
./komodo-cli backupwallet "mybackupdata"

/home/myusername/myexportdir/mybackupdata
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "backupwallet", "params": ["backupdata"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "/home/myusername/Desktop/backupdata",
  "error": null,
  "id": "curltest"
}
```