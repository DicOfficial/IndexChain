## z_importkey

**z_importkey "z_privatekey" ( rescan startHeight )**

The `z_importkey` method imports `z_privatekey` to your wallet.

This call can take minutes to complete if **rescan** is true.

The optional parameters are currently not functional with KMD-based blockchains.

See also **z_exportkey**.

### Arguments

| Name           | Type                                         | Description                                                  |
| -------------- | -------------------------------------------- | ------------------------------------------------------------ |
| "z_privatekey" | (string, required)                           | the z_privatekey (see [z_exportkey](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#z-exportkey)) |
| rescan         | (string, optional, default=`"whenkeyisnew"`) | rescan the wallet for transactions; can be `yes`             |
| startHeight    | (numeric, optional, default=0)               | the block height at which to begin the rescan                |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli z_importkey DONOTUSExxxxxxxxxxxxxxxxBP6ipkmBxmEQbugcCQ16vUaWGFK
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli z_importkey DONOTUSExxxxxxxxxxxxxxxxBP6ipkmBxmEQbugcCQ16vUaWGFK whenkeyisnew 30000
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli z_importkey DONOTUSExxxxxxxxxxxxxxxxBP6ipkmBxmEQbugcCQ16vUaWGFK yes 20000
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_importkey", "params": ["DONOTUSExxxxxxxxxxxxxxxxBP6ipkmBxmEQbugcCQ16vUaWGFK", "no"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": null,
  "error": null,
  "id": "curltest"
}
```