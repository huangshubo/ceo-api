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
* GET [api/market/allTicker](#获取全币种行情) 获取全币种行情
* GET [api/market/ticker](#行情) 行情
* GET [api/market/entrust](#委托记录) 委托记录
* GET [api/market/trades](#历史成交) 历史成交
* GET [api/market/kline](#K线) K线
* GET [api/deal/accountInfo](#获取用户信息) 获取用户信息
* GET [api/deal/order](#委托下单) 委托下单
* GET [api/deal/cancelOrder](#取消委托) 取消委托
* GET [api/deal/getOrder](#获取委托买单或卖单) 获取委托买单或卖单
* GET [api/deal/accountInfo](#获取用户信息) 获取用户信息
* GET [api/deal/getOrders](#获取多个委托买单或卖单) 获取多个委托买单或卖单
* GET [api/deal/getUserAddress](#获取用户充值地址) 获取用户充值地址
* GET [api/deal/getWithdrawAddress](#获取用户的数字币提现地址) 获取用户的数字币提现地址
* GET [api/deal/getWithdrawRecord](#获取数字币提现记录) 获取数字币提现记录
* GET [api/deal/getChargeRecord](#获取数字币充值记录) 获取数字币充值记录
* [Response状态](#Response状态) Response状态
* (#签名方式) 签名方式

#### WebSocket接口：

* [Ws获取全部市场行情](#Ws获取全部市场行情) Ws获取全部市场行情
* [Ws获取市场行情](#Ws获取市场行情) Ws获取市场行情
* [Ws获取市场深度](#Ws获取市场深度) Ws获取市场深度
* [Ws获取历史成交](#Ws获取历史成交) Ws获取历史成交
* [访问限制](#访问限制) 访问限制

---

## 接口详细

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

### **获取全币种行情**

* GET `api/market/allTicker`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |

**返回值**


### **获取market/ticker**

* GET `api/market/ticker`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |

**返回值**



### **Response状态**

* GET `Response状态`

**请求参数**

| 参数        | 类型   |  是否必须   |  说明   |
| :--------:   | :-----:  |  :-----:  |  :-----:  |

**返回值**
