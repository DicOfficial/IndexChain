## z_exportviewingkey

**z_exportviewingkey "z_address"**

The `z_exportviewingkey` method reveals the viewing key corresponding to `z_address`.

See also **z_importviewingkey**.

### Arguments

| Name        | Type               | Description                       |
| ----------- | ------------------ | --------------------------------- |
| "z_address" | (string, required) | the z_address for the viewing key |

### Response

| Name   | Type     | Description     |
| ------ | -------- | --------------- |
| "vkey" | (string) | the viewing key |

#### 📌 Examples

Command:

```bash
./komodo-cli z_exportviewingkey "ztffWAUUY9PnLiBVXY2pnX67kfm71SevtPC5d9LLM3xZqehy4XxV1FeyxPWcHGTiCd7GtQ17gk5jDTQxhHB13K1A7HT6hZH"
```

Show Response

```bash
ZiVtf1yjjR9DeDNNgd4kvRgS1oovQwfK6xt2csfhTwpbUVjnC9RrEeuVkAfJrxN1jDR3d7vR6XmLne4vC9SCYR5F9XMzW19VJ
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_exportviewingkey", "params": ["ztffWAUUY9PnLiBVXY2pnX67kfm71SevtPC5d9LLM3xZqehy4XxV1FeyxPWcHGTiCd7GtQ17gk5jDTQxhHB13K1A7HT6hZH"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "ZiVtf1yjjR9DeDNNgd4kvRgS1oovQwfK6xt2csfhTwpbUVjnC9RrEeuVkAfJrxN1jDR3d7vR6XmLne4vC9SCYR5F9XMzW19VJ",
  "error": null,
  "id": "curltest"
}
```