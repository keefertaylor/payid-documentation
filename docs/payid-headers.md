---
id: payid-headers
title: PayID Headers
sidebar_label: PayID Headers
---

See also: [PayID API Reference](https://api.payid.org).

The PayID protocol has specific header requirements for requests and responses.

### Request headers

The values accepted for XRP are:

| Accept header                 |              Description |
| ----------------------------- | -----------------------: |
| application/xrpl-mainnet+json | Returns mainnet xAddress |
| application/xrpl-testnet+json | Returns testnet xAddress |
| application/xrpl-devnet+json  |  Returns devnet xAddress |

PayID is a fundamentally neutral protocol. When you make a request, the HTTP `Accept` header of the request specifies the payment network and environment, and PayID is therefore capable of returning a user's address information for any network in which that user participates.

An example request has this form.

```HTTP
GET /{user} HTTP/1.1

Accept: application/xrpl-testnet+json
```

Some different header options are shown here, with example values.

| Currency | Header                        | Address payload                                                   |
| :------- | :---------------------------- | :---------------------------------------------------------------- |
| BTC      | application/btc+json          | { address: '1BvBMSEYstWetAu4m4GFg7xJaNVN2' }                      |
| XRP      | application/xrpl-mainnet+json | { address: "rw2ciyaNshpHe7bCHo4bRWq6pqqynnWKQg", tag: "67298042"} |
| ACH      | application/ach+json          | { account: '363023456079',routing: '011302838'}                   |
| All      | application/payid+json        | Variable depending on the contents of each address                |

## Headers for GET requests for PayID Public API

This launch of PayID includes those headers specific to the Xpring ecosystem. Each payment network is free to establish its own standard headers. These headers should be submitted with every GET request, but not POST.

### Header for all addresses

|     Accept header      |            Description            |
| :--------------------: | :-------------------------------: |
| application/payid+json | Returns all addresses for a PayID |

### Headers for XRP

|         Accept header         |       Description        |
| :---------------------------: | :----------------------: |
| application/xrpl-mainnet+json | Returns mainnet xAddress |
| application/xrpl-testnet+json | Returns testnet xAddress |
| application/xrpl-devnet+json  | Returns devnet xAddress  |

### Headers for ACH

|    Accept header     |            Description             |
| :------------------: | :--------------------------------: |
| application/ach+json | Returns account and routing number |

### Headers for BTC

|        Accept header         |       Description       |
| :--------------------------: | :---------------------: |
| application/btc-mainnet+json | Returns mainnet address |
| application/btc-testnet+json | Returns testnet address |

### Headers for ETH

|           Accept header           |       Description       |
| :-------------------------------: | :---------------------: |
|   application/eth-mainnet+json    | Returns mainnet address |
| application/eth-testnet-name+json | Returns testnet address |

Ethernet has a number of different testnets. Refer to <a href="https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md">EIP 155</a>.