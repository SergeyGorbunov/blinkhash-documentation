## Introduction

This repository contains the current documentation for the Blinkhash Mining Pools's backend REST API (v1). The API itself is relatively simple. Each of its endpoints were designed to be self-explanatory while still providing users with standardized JSON-formatted responses, making it easy to search, filter and use our data. The base URL for all requests is https://www.blinkhash.com/api/v1. The complete URL varies depending on the endpoint of the resource being accessed. For instance, you can view the statistics for each of our supported pools via a GET request to this URL: https://www.blinkhash.com/api/v1/statistics.

### Need Support?

If you need help with an API-related matter, the first place to look is our Discord channel, where the developers are available to answer any questions.

## Documentation

Each of the following endpoints follow a simple structure, to promote ease of use. The status codes and JSON-formatted responses are standardized throughout. Regarding authentication, we've decided not to include any, in order to retain transparency and help our users remain anonymous. The endpoints themselves are also cached for two minutes, and consist of the following:

```
{
    endpoint: "example",
    errors: "",
    data: [Object],
}
```

The **Endpoint** field indicates the current endpoint, while the **Errors** field highlights any errors that may have arisen during the request. The **Data** field, on the other hand, contains the user's requested data. In order to add parameters, append them to the end using the following syntax: **/endpoint?parameter=parameter**. If you need to add more than one parameter, you can separate them using the **&** symbol.

---

### Blocks

The **Blocks** endpoint returns every block found by the users of the Blinkhash Mining Pool, separated into the individual pools supported and sorted by block height.  

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/blocks
* **Required Parameters:** None 
* **Optional Parameters:** 
```
pool=[pool]
worker=[worker]
```
* **Object (200):**
```
{
    Blinkhash: [
        {
            "pool": "Blinkhash",
            "symbol": "BHTC",
            "algorithm": "scrypt",
            "time": 1596089323305,
            "height": 1416,
            "blockHash": "ad8832bce1717f2e75da1104d3db929ca7f27cac0d98b325e0b512242d61a68d",
            "blockReward":50,
            "txHash":"291578aa7b9c7a0f254074b1b52df229fc493077abe9e3ea505c2e755529e648",
            "worker":"M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi",
            "soloMined":false,
            "confirmed":false,
            "confirmations":"1"
        },
        {
            "pool": "Blinkhash",
            "symbol": "BHTC",
            "algorithm": "scrypt",
            "time": 1596085696521,
            "height": 1415,
            "blockHash": "951c0fbcc035a27da35bb400f056be4030abc77d2d7b855761a17f2fedefddf4",
            "blockReward": 50,
            "txHash": "09d2b74894d6b314ce955a741394cdb1097c20bda94ac1ac5376b236bf4b180d",
            "worker": "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi",
            "soloMined": false,
            "confirmed": false,
            "confirmations": "2"
        },
        ...
    ],
    ...
}
```

---

### History

The **History** endpoint returns all historical data currently stored on the Blinkhash Mining Pool, separated into the individual pools supported. As this endpoint's main usage is for charting, each individual point of data is only stored for twelve hours (43200s) before being deleted.

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/history
* **Required Parameters:** None 
* **Optional Parameters:** 
```
pool=[pool]
```
* **Object (200):**
```
{
    Blinkhash: [
        {
            "time": 1596069584,
            "hashrateSolo": 0,
            "hashrateShared": 0,
            "workersSolo": 0,
            "workersShared": 0
        },
        {
            "time": 1596070242,
            "hashrateSolo": 1747.6266666666668,
            "hashrateShared": 1747.6266666666668,
            "workersSolo": 1,
            "workersShared": 1,
        },
        ...
    ]
    ...
}
```

---

### Partners

The **Partners** endpoint returns all currently active 'Partners' or 'Useful Links' for the Blinkhash Mining Pool. This most likely does not include all of them, however, as it only shows those with time left on their subscriptions.

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/partners
* **Required Parameters:** None 
* **Optional Parameters:** None
* **Object (200):**
```
{
    "Blinkhash": {
        "name": "Blinkhash",
        "type": "owner",
        "tier": "",
        "subscription": {
            "startDate": "",
            "endDate": ""
        },
        "url": "https://www.blinkhash.com/",
        "image": ""
    }
}
```

---

### Payments

The **Payments** endpoint displays information on any payments sent out to users of the Blinkhash Mining Pool, sorted by the time that they were sent out.

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/payments
* **Required Parameters:** None 
* **Optional Parameters:** 
```
pool=[pool]
worker=[worker]
```
* **Object (200):**
```
{
    "Blinkhash": [
        {
            "time": 1596105713506,
            "txid": "3a0e1a0383eb464dbe4d44a9c15fe2b714844b27b1fec124f95fae6b7c7d1962",
            "shares": 176,
            "workers": 3, 
            "paid": 643.4948, 
            "unpaid": {},
            "records": [
                {
                    "height": 1317,
                    "amounts": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 49.4996
                    },
                    "shares": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 16
                    },
                    "times": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 1
                    }
                },
                {
                    "height": 1318,
                    "amounts": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 16.49986667,
                        "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 32.99973333
                    },
                    "shares": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi":8,
                        "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm":16
                    },
                    "times": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 0,
                        "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 1
                    }
                },
                ...
            ],
            "totals": {
                "amounts": {
                    "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 428.99653334,
                    "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm":164.99866666, 
                    "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y": 49.4996
                },
                "shares": {
                    "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 112,
                    "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 56,
                    "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y": 8
                }
            }
        },
        ...
    ]
    ...
}
```

---

### Statistics

The **Statistics** endpoint displays basic information on each of the pools supported by the Blinkhash Mining Pool, including hashrate, ports, workers, and payments.

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/statistics
* **Required Parameters:** None 
* **Optional Parameters:** 
```
pool=[pool]
```
* **Object (200):**
```
{
    "Blinkhash": {
        "pool": "Blinkhash",
        "symbol": "BHTC",
        "algorithm": "scrypt",
        "featured": true,
        "ports": {
            "3010": {
                "enabled": true,
                "soloMining": false,
                "diff": 8,
                "varDiff": {
                    "minDiff": 8,
                    "maxDiff": 512,
                    "targetTime": 15,
                    "retargetTime": 90,
                    "variancePercent": 30
                }
            },
            "3011": {
                "enabled": true,
                "soloMining": true,
                "diff": 8,
                "varDiff": {
                    "minDiff": 8,
                    "maxDiff": 512,
                    "targetTime": 15,
                    "retargetTime": 90,
                    "variancePercent": 30
                }
            }
        },
        "statistics": {
            "invalidShares": "1",
            "lastPaid": "1596105725196",
            "paymentFees": 1,
            "paymentTime": 7200,
            "paymentMinimum": 0.05,
            "totalPaid": "643.49480000000000002",
            "validShares": "242",
            "validBlocks": "114",
            "blocks": {
                "lastHour": 12,
                "last24Hours": 114,
                "last7Days": 114
            },
            "hashrate": {
                "hashrate": 0,
                "hashrateShared": 0,
                "hashrateSolo": 0
            },
            "workers": {
                "workers": 0,
                "workersShared": 0,
                "workersSolo": 0
            }
        }
    },
    ...
}
```

---

### Wallets

The **Wallets** endpoint takes in a wallet address as a parameter and returns all relevant data, including blocks, payments, and workers.

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/wallets
* **Required Parameters:** 
```
worker=[worker]
```
* **Optional Parameters:** None
* **Object (200):**
```
{
    "worker": "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y",
    "balance": "0.00000000",
    "immature": "1435.48840000",
    "paid": "49.49960000",
    "unpaid": "0.00000000",
    "total": "1484.98800000",
    "blocks": {
        "Blinkhash": [
            {
                "pool": "Blinkhash",
                "symbol": "BHTC",
                "algorithm": "scrypt",
                "time": 1596084931511,
                "height": 1408,
                "blockHash": "9d7d0ee266822cde3fe228b720879bbeee550ba4377e988ddc18272ad3ad94b7",
                "blockReward":50,
                "txHash":"25282f5d30feb504fa4cbb0e76e14fe8f2275e733561161d9d32ce31227a5658",
                "worker":"bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y",
                "soloMined":true,
                "confirmed":false,
                "confirmations":"8"
            },
            {
                "pool": "Blinkhash",
                "symbol": "BHTC",
                "algorithm": "scrypt",
                "time": 1596084805666,
                "height": 1404,
                "blockHash": "44192a4bfa18af591bcb960db001841577cd7ac9741a8c101791aedc3850253c",
                "blockReward": 50,
                "txHash": "5e43d20b9aab81aaa029654db8acf81c1a183f8a8bcfd2313b4a1e266a6df143",
                "worker": "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y",
                "soloMined": true,
                "confirmed": false,
                "confirmations": "16"
            },
            ...
        ],
        ...
    },
    "payments": {
        "Blinkhash":[
            {
                "time": 1596105713506,
                "txid": "3a0e1a0383eb464dbe4d44a9c15fe2b714844b27b1fec124f95fae6b7c7d1962",
                "shares": 176,
                "workers": 3, 
                "paid": 643.4948, 
                "unpaid": {},
                "records": [
                    {
                        "height": 1317,
                        "amounts": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 49.4996
                        },
                        "shares": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 16
                        },
                        "times": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 1
                        }
                    },
                    {
                        "height": 1318,
                        "amounts": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 16.49986667,
                            "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 32.99973333
                        },
                        "shares": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi":8,
                            "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm":16
                        },
                        "times": {
                            "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 0,
                            "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 1
                        }
                    },
                    ...
                ],
                "totals": {
                    "amounts": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 428.99653334,
                        "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm":164.99866666, 
                        "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y": 49.4996
                    },
                    "shares": {
                        "M8aXXv5gC2bj7XKnP5mmBgjGg6if6k2QTi": 112,
                        "MRAF5XR5cpdtff7w5R6tymHzBqAjszb3wm": 56,
                        "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y": 8
                    }
                }
            },
            ...
        ],
        ...
    },
    "workers": {
        Blinkhash: [
            {
                "address": "bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y",
                "difficulty": 8,
                "validShares": 8,
                "invalidShares": 0,
                "hashrate": 1747.6266666666668,
                "soloMining": true
            },
            ...
        ],
        ...
    },
}
```

---

### Workers

The **Workers** endpoint displays information on any currently active workers on the Blinkhash Mining Pool, .

* **Method:** GET
* **URL:** https://www.blinkhash.com/api/v1/workers
* **Required Parameters:** 
* **Optional Parameters:**
```
pool=[pool]
```
* **Object (200):**
```
{
    "Blinkhash": [
        {
            "address":"bhtc1qdf3ant3rvw4szsvum4fefu5mr8k83y7nd5g39y",
            "difficulty":8,
            "validShares":8,
            "invalidShares":0,
            "hashrate":1747.6266666666668,
            "soloMining":true
        },
        ...
    ],
    ...
}
```
