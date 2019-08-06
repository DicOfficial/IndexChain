## z_getoperationstatus

**z_getoperationstatus ([ "operationid", ... ])**

The `z_getoperationstatus` message queries the operation status and any associated result or error data of any `operationid` stored in local memory. The operation will remain in memory (unlike `z_getoperationresult`, which removes the data from the local memory).

### Arguments

| Name          | Type              | Description                                                  |
| ------------- | ----------------- | ------------------------------------------------------------ |
| "operationid" | (array, optional) | a list of operation ids we are interested in; if an array is not provided, the method examines all operations known to the node |

### Response

| Name               | Type                    | Description                                                  |
| ------------------ | ----------------------- | ------------------------------------------------------------ |
| "id"               | (string)                | the operation id                                             |
| "status"           | (string)                | the status of the operation; can be `success`                |
| "creation_time"    | (numeric)               | the creation time, in seconds since epoch (Jan 1 1970 GMT)   |
| "error" : { ... }  | (array of json objects) |                                                              |
| "code"             | (numeric)               | the associated error code                                    |
| "message"          | (string)                | a message to indicate the nature of the error, if such a message is available |
| "method"           | (string)                | the name of the method used in the operation                 |
| "params" : { ... } | (array of json objects) |                                                              |
| "fromaddress"      | (string)                | the address from which funds are drawn                       |
| "amounts": [ ... ] | (array of json objects) |                                                              |
| "address"          | (string)                | the receiving address                                        |
| "amount"           | (numeric)               | the amount to receive                                        |
| "minconf"          | (numeric)               | indicates the required number of mining confirmations        |
| "fee"              | (numeric)               | the fee                                                      |

#### 📌 Examples

Command:

```bash
./komodo-cli z_getoperationstatus
```

Show Response

```json
[
  {
    "id": "opid-b650b582-c2f5-43e0-9a65-9fe23f65c1a5",
    "status": "failed",
    "creation_time": 1537288268,
    "error": {
      "code": -6,
      "message": "Insufficient funds, no UTXOs found for taddr from address."
    },
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

Command:

```bash
./komodo-cli z_getoperationstatus '["opid-47e12224-8477-4cd4-852d-d8c3ddbc6375"]'
```

Show Response

```json
[
  {
    "id": "opid-47e12224-8477-4cd4-852d-d8c3ddbc6375",
    "status": "executing",
    "creation_time": 1537289777,
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
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_getoperationstatus", "params": [["opid-47e12224-8477-4cd4-852d-d8c3ddbc6375"]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "id": "opid-47e12224-8477-4cd4-852d-d8c3ddbc6375",
      "status": "success",
      "creation_time": 1537289777,
      "result": {
        "txid": "2b988a708db2b8d99a92bbff65a57d0d73fdb22c30fc3f3e4f81ab15cfeafc45"
      },
      "execution_secs": 45.200043917,
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