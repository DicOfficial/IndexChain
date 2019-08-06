## z_importviewingkey

**z_importviewingkey "viewing_key" ( rescan startHeight )**

The `z_importviewingkey` adds a viewing key to your wallet. This method allows you to view the balance in a z address that otherwise does not belong to your wallet.

See also **z_exportviewingkey**.

This call can take minutes to complete if **rescan** is true.

The optional parameters are currently not functional for KMD-based blockchains.

### Arguments

| Name          | Type                                       | Description                                                  |
| ------------- | ------------------------------------------ | ------------------------------------------------------------ |
| "viewing_key" | (string, required)                         | the viewing key                                              |
| rescan        | (string, optional, default="whenkeyisnew") | whether to rescan the wallet for transactions; can be `"yes"` |
| startHeight   | (numeric, optional, default=0)             | block height to start rescan                                 |

### Response

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

#### 📌 Examples

Command:

```bash
./komodo-cli z_importviewingkey "ZiVtfYkeyRY3y8Wykm5zjLcnssEkVrkej6j3kQ5B1AE2qp2F3VsKzpoXTzD82hrvMjWB9WxCHbXXrXax2ceyHLWrnQDaMrMja"
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli z_importviewingkey "ZiVtfYkeyRY3y8Wykm5zjLcnssEkVrkej6j3kQ5B1AE2qp2F3VsKzpoXTzD82hrvMjWB9WxCHbXXrXax2ceyHLWrnQDaMrMja" no
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli z_importviewingkey "ZiVtfYkeyRY3y8Wykm5zjLcnssEkVrkej6j3kQ5B1AE2qp2F3VsKzpoXTzD82hrvMjWB9WxCHbXXrXax2ceyHLWrnQDaMrMja" whenkeyisnew 30000
```

Show Response

```bash
(none)
```

Command:

```bash
./komodo-cli z_importviewingkey "ZiVtfYkeyRY3y8Wykm5zjLcnssEkVrkej6j3kQ5B1AE2qp2F3VsKzpoXTzD82hrvMjWB9WxCHbXXrXax2ceyHLWrnQDaMrMja" yes 20000
```

Show Response

```bash
(none)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_importviewingkey", "params": ["ZiVtfYkeyRY3y8Wykm5zjLcnssEkVrkej6j3kQ5B1AE2qp2F3VsKzpoXTzD82hrvMjWB9WxCHbXXrXax2ceyHLWrnQDaMrMja", "no"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(none)
```