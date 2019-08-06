## importprivkey

**importkey "komodoprivkey" ( "label" rescan )**

The `importprivkey` method adds a private key to your wallet.

This call can take minutes to complete if **rescan** is true.

See also **dumpprivkey**.

### Arguments

| Name      | Type                              | Description                                                  |
| --------- | --------------------------------- | ------------------------------------------------------------ |
| "privkey" | (string, required)                | the private key (see [dumpprivkey](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#dumpprivkey)) |
| "label"   | (string, optional, default="")    | an optional label                                            |
| rescan    | (boolean, optional, default=true) | rescan the wallet for transactions                           |

### Response

| Name      | Type     | Description        |
| --------- | -------- | ------------------ |
| addresses | (string) | the public address |

#### 📌 Examples

Command:

```bash
./komodo-cli importprivkey "DONOTUSExxxxxxxxxxxxxxxxxxxxj4Xu9jjinhLpffhdtoKg5gar2"
```

Show Response

```bash
R9z796AehK5b6NCPeVkGUHSpJnawerf8oP
```

Command:

```bash
./komodo-cli importprivkey "DONOTUSExxxxxxxxxxxxxxxxxxxxj4Xu9jjinhLpffhdtoKg5gar2" "testing" false
```

Show Response

```bash
RFtA32tttJm89VWRWPCQtV8bkQ1FvE1MBG
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "importprivkey", "params": ["UwibHKsYfiM19BXQmcUwAfw331GzGQK8aoPqqYEbyoPrzc2965nE", "testing", false] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "RC5qhqgYRzf3dUXGAst9ah5LcuLjmMgT64",
  "error": null,
  "id": "curltest"
}
```