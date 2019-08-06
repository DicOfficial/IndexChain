## zcbenchmark

**zcbenchmark benchmarktype samplecount**

The `zcbenchmark` method runs a benchmark of the selected `benchmarktype`. This benchmark is calculated `samplecount` times.

When finished, the method returns the running times of each sample.

### Arguments

| Name            | Type               | Description                   |
| --------------- | ------------------ | ----------------------------- |
| "benchmarktype" | (string, required) | the type of the benchmark     |
| "samplecount"   | (numeric)          | the number of samples to take |

### Response

| Name          | Type      | Description                                          |
| ------------- | --------- | ---------------------------------------------------- |
| "runningtime" | (numeric) | the time it took to run the selected `benchmarktype` |

Output:

```json
[
  {
    "runningtime": runningtime
  },
  {
    "runningtime": runningtime
  }
  ...
]
```