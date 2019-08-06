## z_getoperationresult

**z_getoperationresult ([ "operationid", ... ])**

The `z_getoperationresult` method retrieves the result and status of an operation which has finished, and then removes the operation from memory.

See also **z_getoperationstatus**.

### Arguments

| Name          | Type               | Description                                                  |
| ------------- | ------------------ | ------------------------------------------------------------ |
| "operationid" | (string, optional) | a list of operation ids to query; if not provided, the method examines all operations known to the node |

### Response

| Name               | Type                    | Description                                                |
| ------------------ | ----------------------- | ---------------------------------------------------------- |
| "id"               | (string)                | the operation id                                           |
| "status"           | (string)                | the result of the operation; can be `success`              |
| "creation_time"    | (numeric)               | the creation time, in seconds since epoch (Jan 1 1970 GMT) |
| "result": { ... }  | (array of json objects) |                                                            |
| "txid":            | (string)                | the transaction id                                         |
| "execution_secs"   | (numeric)               | the length of time to calculate the transaction            |
| "method"           | (string)                | the name of the method used in the operation               |
| "params": { ... }  | (json)                  |                                                            |
| "fromaddress"      | (string)                | the address from which funds are drawn                     |
| "amounts": [ ... ] | (array of json objects) |                                                            |
| "address"          | (string)                | the receiving address                                      |
| "amount"           | (numeric)               | the amount to receive                                      |
| "minconf"          | (numeric)               | the minimum number of confirmations required               |
| "fee"              | (numeric)               | the transaction fee                                        |

#### 📌 Examples

Command:

```bash
./komodo-cli z_getoperationresult '["opid-6e581ee5-4e90-4e70-8961-f95d8d28748c"]'
```

Show Response

```json
[
  {
    "id": "opid-6e581ee5-4e90-4e70-8961-f95d8d28748c",
    "status": "success",
    "creation_time": 1537287690,
    "result": {
      "txid": "65e01c8485f6a85fbf7093d8233864eed0f31e6e2eff22a7e468e92c37dc864c"
    },
    "execution_secs": 44.606282288,
    "method": "z_sendmany",
    "params": {
      "fromaddress": "RWUwHqRUYgxfYNNSHWkQuY5sh93VGiiPoX",
      "amounts": [
        {
          "address": "ztci8RzNSo2pdiDpAeHpz9Rp91hq12Mn7zcFfBR8Jjs2ydZUCTw8rLZzkVP888M4vGezpZVfsTR8orgxYK3N8gdgbBzakx3",
          "amount": 0.01
        }
      ],
      "minconf": 1,
      "fee": 0.0001
    }
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_getoperationresult", "params": [["opid-6a9da0dd-a950-4d95-848c-d3c18e44be03"]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "id": "opid-6a9da0dd-a950-4d95-848c-d3c18e44be03",
      "status": "success",
      "creation_time": 1537288235,
      "result": {
        "txid": "f0309f8dc2e33e108dec39285bc8755058375cf6e51bdb452fb45f3d14909fef"
      },
      "execution_secs": 44.978749064,
      "method": "z_sendmany",
      "params": {
        "fromaddress": "RWUwHqRUYgxfYNNSHWkQuY5sh93VGiiPoX",
        "amounts": [
          {
            "address": "ztci8RzNSo2pdiDpAeHpz9Rp91hq12Mn7zcFfBR8Jjs2ydZUCTw8rLZzkVP888M4vGezpZVfsTR8orgxYK3N8gdgbBzakx3",
            "amount": 0.01
          }
        ],
        "minconf": 1,
        "fee": 0.0001
      }
    }
  ],
  "error": null,
  "id": "curltest"
}
```