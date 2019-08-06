## z_exportkey

**z_exportkey "z_address"**

The `z_exportkey` method reveals the private z_key corresponding to `z_address`.

See also **z_importkey**.

### Arguments

| Name        | Type               | Description                       |
| ----------- | ------------------ | --------------------------------- |
| "z_address" | (string, required) | the z_address for the private key |

### Response

| Name  | Type     | Description     |
| ----- | -------- | --------------- |
| "key" | (string) | the private key |

#### 📌 Examples

Command:

```bash
./komodo-cli z_exportkey "ztffWAUUY9PnLiBVXY2pnX67kfm71SevtPC5d9LLM3xZqehy4XxV1FeyxPWcHGTiCd7GtQ17gk5jDTQxhHB13K1A7HT6hZH"
```

Show Response

```bash
DONOTUSExxxxxxxxxxxxxxxxV6EyPpaZFVDsqeNB6k8eoLFERdag
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_exportkey", "params": ["ztffWAUUY9PnLiBVXY2pnX67kfm71SevtPC5d9LLM3xZqehy4XxV1FeyxPWcHGTiCd7GtQ17gk5jDTQxhHB13K1A7HT6hZH"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "DONOTUSExxxxxxxxxxxxxxxxV6EyPpaZFVDsqeNB6k8eoLFERdag",
  "error": null,
  "id": "curltest"
}
```