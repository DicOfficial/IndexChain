## setpubkey

**setpubkey pubkey**

The `setpubkey` method sets the indicated `pubkey`. This method can be used in place of the [pubkey](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#pubkey) launch parameter, when necessary.

Visit the section [pubkey](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#pubkey) to understand when it is essential to set a pubkey and the consequences of setting it.

This method works only once per daemon start. It can't be used to change the pubkey that has already been set.

### Arguments

| Name   | Type     | Description        |
| ------ | -------- | ------------------ |
| pubkey | (string) | the desired pubkey |

### Response

| Name      | Type      | Description                                       |
| --------- | --------- | ------------------------------------------------- |
| pubkey    | (string)  | the pubkey                                        |
| ismine    | (boolean) | indicates whether the address belongs to the user |
| R-address | (string)  | the public address associated with the pubkey     |

#### 📌 Examples

Command:

```bash
./komodo-cli setpubkey 0260801166cebdc9be1e3460ba9e4959fb29feee7725f565ffc296fa4636aa706f
```

Show Response

```bash
{
  "address": "RK47DQhSHJEMGFSiRtgki67xG3u1Qsq1Gw",
  "ismine": true,
  "pubkey": "0260801166cebdc9be1e3460ba9e4959fb29feee7725f565ffc296fa4636aa706f"
}
```

You can find the `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "setpubkey", "params": ["02f7597468703c1c5c8465dd6d43acaae697df9df30bed21494d193412a1ea193e"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
{
  "result": {
    "address": "RK47DQhSHJEMGFSiRtgki67xG3u1Qsq1Gw",
    "ismine": true,
    "pubkey": "0260801166cebdc9be1e3460ba9e4959fb29feee7725f565ffc296fa4636aa706f"
  },
  "error": null,
  "id": "curltest"
}
```