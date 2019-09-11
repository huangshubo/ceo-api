# trade-api-demo

- - - - - -

## 仓库代码说明

* com.ceo.apidemo.apidemo.client： rest接口

* com.ceo.apidemo.apidemo.wsclient： websocket接口
 > demo1 java客户端
 >
 > demo2 html代码 html可直接运行


## 接口说明

CEO为用户提供了两种调用接口的方式，分别为：Rest和WebSocket，开发者可根据自身需求来选择适合自己的方式查询市场深度信息、交易和查询相关的交易记录

----

##### REST API说明：
REST，即Representational State Transfer的缩写，是目前最流行的一种互联网软件架构。它利用了Web的现有特征和能力， 能更好地使用现有Web标准中的一些准则和约束。

##### WebSocket API说明：
WebSocket 是 HTML5 开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。WebSocket 使得客户端和服务器之间的数据交换变得更加简单，允许服务端主动向客户端推送数据。在 WebSocket API 中，浏览器和服务器只需要完成一次握手，两者之间就直接可以创建持久性的连接，并进行双向数据传输。

----

##### 访问地址：
* REST：https://api.ceobi.com/
* WebSocket：wss://api.ceobi.com/websocket

----

## API接口

#### REST接口：
* [获取全币种行情](#获取全币种行情)
* [行情](#行情)
* [委托记录](#委托记录)
* [历史成交](#历史成交)
* [K线](#K线)
* [获取用户信息](#获取用户信息)
* [委托下单](#委托下单)
* [取消委托](#取消委托)
* [获取委托买单或卖单](#获取委托买单或卖单)
* [获取用户信息](#获取用户信息)
* [获取多个委托买单或卖单](#获取多个委托买单或卖单)
* [获取用户充值地址](#获取用户充值地址)
* [获取用户的数字币提现地址](#获取用户的数字币提现地址)
* [获取数字币提现记录](#获取数字币提现记录)
* [获取数字币充值记录](#获取数字币充值记录)
* [Response状态](#Response状态)
* [签名方式](#签名方式)

#### WebSocket接口：

* [Ws获取全部市场行情](#Ws获取全部市场行情)
* [Ws获取市场行情](#Ws获取市场行情)
* [Ws获取市场深度](#Ws获取市场深度)
* [Ws获取历史成交](#Ws获取历史成交)
* [访问限制](#访问限制) 访问限制

---

## 接口详细

### **获取全币种行情**
*Request*
> Method: GET
>
> URL: api/market/allTicker
>
*Response*

```json
{
          "code": 1000,
          "message": "成功",
          "data": {
              "ceo_qc": { //市场名
                  "buy": "91.00000000", //买一价
                  "sell": "91.50000000", //卖一价
                  "last": "90.00000000", //最新成交价
                  "vol": "0.00000000", //成交量(最近的24小时)
                  "high": "0.00000000", //最高价
                  "low": "0.00000000" //最低价
              },
              "eth_ceo": {
                  "buy": "52.18000000",
                  "sell": "53.30000000",
                  "last": "53.30000000",
                  "vol": "5.00000000",
                  "high": "53.30000000",
                  "low": "53.00000000"
              },
              ......
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| data        |  包含所有交易对的数组   |

**示例**

[python](#获取市场列表信息-python-demo)

----

### **行情**

### **委托记录**

### **历史成交**

### **K线**

### **获取用户信息**

### **委托下单**

### **取消委托**

### **获取委托买单或卖单**

### **获取用户充值地址**

### **获取用户的数字币提现地址**

### **获取数字币提现记录**

### **获取数字币充值记录**

### **Response状态**

### **签名方式**

### **Ws获取全部市场行情**

### **Ws获取市场行情**

### **Ws获取市场深度**

### **Ws获取历史成交**

### **访问限制**

### **获取全币种行情**

* GET `api/market/allTicker`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |

**返回值**

```json
{
    "code": 200,
    "data": [
        "btc_usdt",
        "eth_usdt"
    ],
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| data        |  包含所有交易对的数组   |

**示例**

[python](#获取市场列表信息-python-demo)

----

### **行情**

* GET `api/market/ticker`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |

**返回值**

```json
{
    "code": 200,
    "data": {
        "ETC_BTC": {
            "priceScale": 6,
            "quantityScale": 2,
            "minAmount": 0.0001,
            "buyFeeRate": 0.002,
            "sellFeeRate": 0.002
        },
        "BTC_USDT": {
            "priceScale": 2,
            "quantityScale": 6,
            "minAmount": 0.1,
            "buyFeeRate": 0.002,
            "sellFeeRate": 0.002
        }
    },
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| priceScale        |  价格精度   |
| quantityScale        |  数量精度   |
| minAmount        |  最小量   |
| buyFeeRate        |  买单费率   |
| sellFeeRate        |  卖单费率   |

**示例**

[python](#获取交易对信息-python-demo)

----

## **获取深度信息**

* GET `/open/api/v1/data/depth`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| depth        | integer   |  √   |  返回的深度个数   |
| market        | string   |  √   |  交易对名称   |

**返回值**

```json
{
    "code": 200,
    "data": {
        "asks": [
            {
                "price": "7061.82",
                "quantity": "2.759119"
            },
            {
                "price": "7062.4",
                "quantity": "0.01764"
            }
        ],
        "bids": [
            {
                "price": "7061.8",
                "quantity": "0.160269"
            },
            {
                "price": "7059.68",
                "quantity": "0.26862"
            }
        ]
    },
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| price        |  价格   |
| quantity        |  数量   |

**示例**

[python](#获取深度信息-python-demo)

----

## **获取单个币种成交记录信息**

* GET `/open/api/v1/data/history`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| market        | string   |  √   |  交易对名称   |

**返回值**

```json
{
    "code": 200,
    "data": [
        {
            "tradeTime": "2019-05-13 14:12:58.787",
            "tradePrice": "7051.04",
            "tradeQuantity": "0.0189",
            "tradeType": "1"
        },
        {
            "tradeTime": "2019-05-13 14:12:58.494",
            "tradePrice": "7051.04",
            "tradeQuantity": "0.023551",
            "tradeType": "1"
        }
    ],
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| tradeTime        |  成交时间   |
| tradePrice        |  成交价格   |
| tradeQuantity        |  成交量   |
| tradeType        |  成交类型1/2 (买/卖)   |

**示例**

[python](#获取单个币种成交记录信息-python-demo)

----

## **获取市场行情信息**

* GET `/open/api/v1/data/ticker`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| market        | string   |  ×   |  交易对   |

**返回值**

```json
{
    "code": 200,
    "data": {
        "volume": "29821.449121",
        "high": "7512.22",
        "low": "6791.23",
        "buy": "7054.5",
        "sell": "7054.95",
        "open": "7304.1",
        "last": "7054.46"
    },
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| volume        |  24小时成交量   |
| high        |  24小时最高价   |
| low        |  24小时最低价   |
| buy        |  买一价   |
| sell        |  卖一价   |
| open        |  开盘价   |
| last        |  最后成交价   |

**示例**

[python](#获取市场行情信息-python-demo)

----

## **获取市场k线信息**

* GET `/open/api/v1/data/kline`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| market       | string   |  √   |  交易对   |
| interval     | string   |  √   |  时间间隔(分钟制:1m，5m，15m，30m，60m。小时制:1h，天制:1d，月制:1M)|
| startTime    | long     |  √   |  起始时间(单位秒,毫秒数/1000 ) |
| limit        | long     |  ×   |  返回条数 |

**返回值说明**

```json
{
    "code": 200,
    "data": [
        [
            1557728040,
            "7054.7",
            "7056.26",
            "7056.29",
            "7054.16",
            "9.817734",
            "69264.52975125"
        ],
        [
            1557728100,
            "7056.26",
            "7042.17",
            "7056.98",
            "7042.16",
            "23.694823",
            "167007.92840231"
        ],
        [
            1557728160,
            "7042.95",
            "7037.11",
            "7043.27",
            "7036.53",
            "22.510102",
            "158461.98283462"
        ]
    ],
    "msg": "OK"
}
```

| 返回值       |  说明   |
| :--------:  | :-----:  |
| time        |  开始时间 (单位秒,毫秒数/1000 )  |
| open        |  开盘价   |
| close       |  收盘价   |
| high        |  最高价   |
| low         |  最低价   |
| vol         |  成交量   |
| amount      |  计价货币成交量   |

**示例**

[python](#获取市场K线信息-python-demo)

----

## **获取账户资产信息**

* GET `/open/api/v1/private/account/info`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| req_time          | string   |  √   |  请求时间戳   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "BTC": {
        "frozen": "0",
        "available": "130440.28790112"
    },
    "ETH": {
        "frozen": "27.6511928",
        "available": "12399653.86856669"
    }
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| frozen        |  冻结量   |
| available        |  可用量   |

**示例**

[python](#获取账户资产信息-python-demo)

----

## **获取当前委托信息**

* GET `/open/api/v1/private/current/orders`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| market          | string   |  √   |  交易对   |
| page_num           | integer   |  √   |  页数   |
| page_size           | integer   |  √   |  每页大小   |
| req_time            | string   |  √   |  请求时间戳   |
| trade_type            | integer   |  √   |  交易类型，0/1/2 (所有/买/卖)   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "code": 200,
    "data": [
        {
            "id": "4921e6be-cfb9-4058-89d3-afbeb6be7d78",
            "market": "MX_ETH",
            "price": "0.439961",
            "status": "1",
            "totalQuantity": "2",
            "tradedQuantity": "0",
            "tradedAmount": "0",
            "createTime": "2019-05-13 14:31:11",
            "type": 1
        },
        {
            "id": "6170091f-c977-49bf-baa8-b643c70452c7",
            "market": "MX_ETH",
            "price": "0.4399605",
            "status": "1",
            "totalQuantity": "1",
            "tradedQuantity": "0",
            "tradedAmount": "0",
            "createTime": "2019-05-13 14:30:51",
            "type": 1
        }
    ],
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| id        |  订单id   |
| market        |  交易对   |
| price        |  挂单价   |
| status        |  订单状态，1:未成交 2:已成交 3:部分成交 4:已撤单 5:部分撤单   |
| totalQuantity        |  挂单总量   |
| tradedQuantity        |  挂单成交量   |
| tradedAmount        |  挂单成交量(计价币)   |
| createTime        |  订单创建时间   |
| type        |  订单类型1/2 (买/卖)   |

**示例**

[python](#获取当前委托信息-python-demo)

----

## **下单**

* POST `/open/api/v1/private/order`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| market          | string   |  √   |  交易对   |
| price            | string   |  √   |  交易价格   |
| quantity            | string   |  √   |  交易数量   |
| req_time            | string   |  √   |  请求时间戳   |
| trade_type            | integer   |  √   |  交易类型：1/2 (买/卖)   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "code": 200,
    "data": "de5a6819-5456-45da-9e51-ee258dd34422",
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| data        |  订单id   |

**示例**

[python](#下单-python-demo)

----

## **取消订单**

* DELETE `/open/api/v1/private/order`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| market          | string   |  √   |  交易对   |
| req_time            | string   |  √   |  请求时间戳   |
| trade_no             | string   |  √   |  委托单号   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "code": 200,
    "data": null,
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |

**示例**

[python](#取消订单-python-demo)

----

## **查询账号历史委托记录**

* GET `/open/api/v1/private/orders`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| req_time          | string   |  √   |  请求时间戳   |
| market          | string   |  √   |  交易对   |
| trade_type            | string   |  √   |  交易类型，1/2 (买/卖)   |
| page_num          | integer   |  √   |  页数   |
| page_size             | integer   |  √   |  每页大小   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "code": 200,
    "data": [
        {
            "id": "f5718b8a-8f93-4880-8e95-281fe28efb91",
            "market": "OMG_ETH",
            "price": "0.011546000000000000",
            "status": "2",
            "totalQuantity": "46.520000000000000000",
            "tradedQuantity": "46.520000000000000000",
            "tradedAmount": "0.537119920000000000",
            "createTime": "2019-04-26 16:37:47.0",
            "type": 1
        },
        {
            "id": "845fdde0-6837-4d56-af8c-e43d72495cc1",
            "market": "OMG_ETH",
            "price": "0.011543000000000000",
            "status": "2",
            "totalQuantity": "7.920000000000000000",
            "tradedQuantity": "7.920000000000000000",
            "tradedAmount": "0.091420560000000000",
            "createTime": "2019-04-26 11:05:42.0",
            "type": 1
        }
    ],
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| id        |  订单id   |
| market        |  交易对   |
| price        |  成交价格   |
| status        |  订单状态，1:未成交 2:已成交 3:部分成交 4:已撤单 5:部分撤单   |
| totalQuantity        |  订单总量   |
| createTime        |  订单时间   |
| type        |  交易类型：1/2 (买/卖)   |

**示例**


[python](#查询账号历史委托记录-python-demo)

----

## **查询订单状态**

* GET `/open/api/v1/private/order`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |
| api_key         | string   |  √   |  您的api key   |
| req_time          | string   |  √   |  请求时间戳   |
| market          | string   |  √   |  交易对   |
| trade_no            | string   |  √   |  订单id，如果有多个，用英文逗号分隔，一次最多查询20个   |
| sign          | string   |  √   |  请求签名   |

**返回值**

```json
{
    "code": 200,
    "data": {
        "id": "f5718b8a-8f93-4880-8e95-281fe28efb91",
        "market": "OMG_ETH",
        "price": "0.011546",
        "status": "2",
        "totalQuantity": "46.52",
        "tradedQuantity": "46.52",
        "tradedAmount": "0.53711992",
        "createTime": "2019-04-26 16:37:47",
        "type": 1
    },
    "msg": "OK"
}
```

**返回值说明**

| 返回值        |  说明   |
| :--------:   | :-----:  |
| id        |  订单id   |
| market        |  交易对   |
| price        |  下单价格   |
| status        |  订单状态，1:未成交 2:已成交 3:部分成交 4:已撤单 5:部分撤单   |
| totalQuantity        |  订单总量   |
| tradedQuantity        |  成交总量   |
| tradedAmount        |  成交量（计价货币）   |
| createTime        |  下单时间   |
| type        |  交易类型：1/2 (买/卖)   |


