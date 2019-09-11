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
* [获取多个委托买单或卖单](#获取多个委托买单或卖单)
* [获取交易记录](#获取交易记录)
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
* [访问限制](#访问限制)

---

## 接口详细

### **获取全币种行情**
*Request*
> Method: GET
>
> URL: api/market/allTicker
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "ceo_qc": { //市场名
                  "buy": "91.00000000",  //买一价
                  "sell": "91.50000000", //卖一价
                  "last": "90.00000000", //最新成交价
                  "vol": "0.00000000",   //成交量(最近的24小时)
                  "high": "0.00000000",  //最高价
                  "low": "0.00000000"    //最低价
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
----
### **行情**
*Request*
> Method: GET
>
> URL: api/market/ticker
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:   | :-----:  |  :-----:  |  :-----:  |
> | market        | string   |  Y   |  市场名称   |
>
> api/market/ticker?market=ceo_qc
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "buy": "91.00000000",  //买一价
              "sell": "91.50000000", //卖一价
              "last": "90.00000000", //最新成交价
              "vol": "0.00000000",   //成交量(最近的24小时)
              "high": "0.00000000",  //最高价
              "low": "0.00000000",   //最低价
              "time": 1535012914     //时间
          }
}
```
----
### **委托记录**
*Request*
> Method: GET
>
> URL: api/market/entrust
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:   | :-----:  |  :-----:  |  :-----:  |
> | market        | string   |  Y   |  市场名称   |
>
> api/market/entrust?market=ceo_qc
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "b": [ //买
                  [
                      "11.37",      //价格
                      "877.627331"  //数量
                  ],
                  [
                      "11.01",
                      "1018.843536"
                  ],
              ],
              "s": [ //卖
                  [
                      "70.00", //
                      "1000.000000"
                  ],
                  [
                      "60.00",
                      "1000.000000"
                  ]
          ]
}
```
----
### **历史成交**
*Request*
> Method: GET
>
> URL: api/market/trades
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:   | :-----:  |  :-----:  |  :-----:  |
> | market        | string   |  Y   |  市场名称   |
>
> api/market/trades?market=bit_qc
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": [
              {
                  "amount": "5000.000000", //交易数量
                  "price": "0.400000",     //交易价格
                  "type": 2,               //交易类型，1(买)/2(卖)
                  "time": 1530144000       //交易时间(时间戳)
              },
              {
                  "amount": "5000.000000",
                  "price": "0.400000",
                  "type": 1,
                  "time": 1530144000
              },
              ......
          ]
}
```
----
### **K线**
*Request*
> Method: GET
>
> URL: api/market/kline
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> | market      | string   |  Y   |  市场名称   |
> | type        | string    |Y   |  时间   |
> | size        | int       | Y  |返回数据的条数限制(默认为1000，大于1000，只返回1000)|
>
> type 值为： 1min 3min 5min 15min 30min 1day 3day 1week 1hour 2hour 4hour 6hour 12hour
>
> api/market/kline?market=bit_qc&type=1week
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "sellCoin": "bit", //卖出货币
              "buyCoin": "qc", //买入货币
              "data": [
                  [
                      1518843600, //时间戳
                      "2550558.083140", //交易量
                      "1.322000", //开盘价
                      "1.396000", //最高价
                      "1.005000", //最低价
                      "1.031000" //收盘价
                  ],
              ......
          }
}
```
----
### **获取用户信息**
*Request*
> Method: GET
>
> URL: api/deal/accountInfo
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 accountInfo|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
>
> api/deal/accountInfo?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=accountInfo&
> sign=3967426b6a1aaa3f26a2c7b382a50621&reqTime=1535102429
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "base": {
                  "auth_google_enabled": false, //是否开通谷歌验证
                  "auth_mobile_enabled": true, //是否开通手机验证
                  "trade_password_enabled": true, //是否开通交易密码
                  "username": "test" //用户名
              },
              "coins": [
                  {
                      "enName": "btc", //币种英文名
                      "cnName": "比特币", //币种中文名
                      "symbol": "฿", //币种符号
                      "available": "86114.16208700", //可用资产
                      "freez": "0.00000000", //冻结资产
                      "unitDecimal": "2", //保留小数位
                      "isCanRecharge": true, //是否可充值
                      "isCanWithdraw": true //是否可提现
                  },
              ......
              ]
          }
}
```
----
### **委托下单**
*Request*
> Method: GET
>
> URL: api/deal/order
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 order|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |price|	float	|Y|	单价|
> |amount|	float	|Y	|交易数量|
> |tradeType|	int	|Y	|交易类型1/2[买/卖]|
> |currency	|string|	Y|	市场名字|
>
> api/deal/order?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=order&
> sign=f7169edac202a776b87811661817aeeb&reqTime=1535102429&price=60000&amount=0.113&tradeType=1&currency=btc_qc
>
*Response*

```html
{
              "code": 1000,
              "message": "委托挂单成功",
              "data": {
                  "orderId": "643" //订单ID
              }
}
```
----
### **取消委托**
*Request*
> Method: GET
>
> URL: api/deal/cancelOrder
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 cancelOrder|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	市场名字|
> |id|	int	|Y|	订单ID|
>
> api/deal/cancelOrder?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=cancelOrder&
> sign=1cb2d3c0d1fd708abb7eda37770172b5&reqTime=1535102429&id=626&currency=btc_qc
>
*Response*

```html
{
          "code": 1000,
          "message": "撤销成功",
          "data": ""
}
```
----
### **获取委托买单或卖单**
*Request*
> Method: GET
>
> URL: api/deal/getOrder
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getOrder|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	市场名字|
> |id|	int	|Y|	订单ID|
>
> api/deal/getOrder?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getOrder&
> sign=d712dfa60eaf5bc4053ebcd4af5ec253&reqTime=1535102429&id=626&currency=btc_qc
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "currency": "btc_qc", //市场
              "id": 626, //委托挂单号
              "price": "60000.000000", //单价
              "status": 2, ////挂单状态 (状态(0:交易中,1:已完成,2:已撤销, 3:部分成交))
              "total_amount": "0.113000", //挂单总数量
              "trade_amount": "0.000000", //已成交数量
              "trade_time": 1534301098, //委托时间
              "trade_money": "6793.560000", //总交易金额
              "type": 1 //挂单类型 1/2[buy/sell]
              "deal_money": "15.560000", //实际成交金额
          }
}
```
----
### **获取多个委托买单或卖单**
*Request*
> Method: GET
>
> URL: api/deal/getOrders
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getOrders|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	市场名字|
> |pageIndex|	int	|Y|	当前页数|
> |pageSize	|int	|Y	|每页数量 10-100|
> |tradeType|	int	|N|	交易类型1/2[buy/sell]|
> |tradeStatus|	int|	N|	交易状态 0:交易中,1:已完成,2:已撤销,3:部分成交,4:合并1与3|
>
> api/deal/getOrders?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getOrders&
>sign=6ed7b69018b4c151b2cf77f531a655a0&reqTime=1535102429&currency=btc_qc&pageIndex=1&pageSize=10&tradeStatus=1
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": [
              {
                  "currency": "btc_qc", //市场
                  "id": 631, //委托挂单号
                  "price": "60000.000000", //单价
                  "status": 0, //挂单状态 (状态(0:交易中,1:已完成,2:已撤销, 3:部分成交))
                  "total_amount": "0.113000", //挂单总数量
                  "trade_amount": "0.000000", //已成交数量
                  "trade_date": 1535162354, //委托时间
                  "trade_money": "6793.560000", //总交易金额
                  "type": 1 //挂单类型 1/2[buy/sell]
              },
              ......
          ]
}
```
----
### **获取交易记录**
*Request*
> Method: GET
>
> URL: api/deal/getTrades
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getTrades|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	市场名字|
> |pageIndex|	int	|Y|	当前页数|
> |pageSize|	int	|Y|	每页数量 10-100|
> |orderId	|int|	Y	|订单编号|
> |startTime|	int|	Y|	开始时间毫秒数|
> |endTime	|int	|Y|	结束时间毫秒数|
>
> api/deal/getTrades?accesskey=f11c8358-9b30-4a5c-9c2d-906e4adb71d0&method=getTrades&
> sign=6ed7b69018b4c151b2cf77f531a655a0&reqTime=1535102429&pageIndex=1&currency=ceo_qc&
> pageSize=10&orderId=16&startTime=1566355654&endTime=1566371318
>
*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": [
              {
                  "currency": "ceo_qc", //市场
                  "id": 571, //交易id
                  "price": "36.000000", //单价
                  "amount": "0.261040", //交易量
                  "type": 1, //交易类型 1/2[buy/sell]
                  "date": 1538276466, //时间
                  "fee": "0.000210" //手续费
              }
          ]
}
```
----
### **获取用户充值地址**
*Request*
> Method: GET
>
> URL: api/deal/getUserAddress
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getUserAddress|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	币名|
>
> api/deal/getUserAddress?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getUserAddress&
> sign=469595363c7a04a9b1f693273397cbc0&reqTime=1535102429&currency=gxs
>

*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "address": "qqfewfew", //地址
              "memo": "99" //备注
          }
}
```
----
### **获取用户的数字币提现地址**
*Request*
> Method: GET
>
> URL: api/deal/getWithdrawAddress
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getWithdrawAddress|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	币名|
>
> api/deal/getWithdrawAddress?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getWithdrawAddress&
> sign=620f6c274e4dd0e9cd8312a8765f2c17&reqTime=1535102429&currency=btc
>

*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": [
              "1DZdA2WAzcsSak3tQYRVwuXWeSqhLuVCoA",
              "1DZdA2WAzcsSak3tQYRVwuXWeSqhLuVCoc"
          ]
}
```
----
### **获取数字币提现记录**
*Request*
> Method: GET
>
> URL: api/deal/getWithdrawRecord
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getWithdrawRecord|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	币名|
> |pageIndex|	int|	Y|	当前页数|
> |pageSize|	int	|Y	|每页数量|
>
> api/deal/getWithdrawRecord?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getWithdrawRecord&
> sign=0e94e185a41dcf339491bd4c6c958dea&reqTime=1535102429&currency=btc&pageIndex=1&pageSize=10
>

*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "pageIndex": 1, //当前页数
              "pageSize": 10, //每页数量
              "totalCount": 7, //总数量
              "totalPage": 1, //总页数
              "list": [
                  {
                      "amount": "5.00000000", //提现金额
                      "fees": "0.00150000", //提现手续费
                      "id": 165558, //提现记录id
                      "manageTime": 0, //提现处理的时间的时间戳
                      "status": 0, //提币状态状态（0：等待处理；1：转出成功；2：已经审核；3：已经撤销）
                      "submitTime": 1534920264, //提现发起的时间的时间戳
                      "toAddress": "1DZdA2WAzcsSak3tQYRVwuXWeSqhLuVCoc" //提现的接收地址
                  },
                  ......
              ]
          }
}
```
----
### **获取数字币充值记录**
*Request*
> Method: GET
>
> URL: api/deal/getChargeRecord
>
> Parameters:
>
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |accesskey	   |   string	   |Y      |	accesskey    |
> |method	|string|	Y|	直接赋值 getChargeRecord|
> |reqTime|	int	|Y|	当前时间毫秒数|
> |sign	|string	|Y|	签名串|
> |currency	|string|	Y|	币名|
> |pageIndex|	int|	Y|	当前页数|
> |pageSize|	int	|Y	|每页数量|
>
> api/deal/getChargeRecord?accesskey=519b3346-7198-47e3-81b8-20ce13513835&method=getChargeRecord&
> sign=538b6d053c32cd83f97fd2cfadfb7f31&reqTime=1535102429&currency=eth&pageIndex=1&pageSize=10
>

*Response*

```html
{
          "code": 1000,
          "message": "成功",
          "data": {
              "pageIndex": 1, //当前页数
              "pageSize": 10, //每页数量
              "totalCount": 2, //总数量
              "totalPage": 1, //总页数
              "list": [
                  {
                      "address": "0x5de61aec70dc1654456f75aa964daf754d2a7f30",
                      "amount": "0.01050000",
                      "confirmTimes": 3,
                      "currency": "ETH",
                      "hash": "0x84d073ef430e53e5b21bb35831b135ce217a69efbadddc187b9380fa3fdd5a3b",
                      "id": 19813,
                      "status": 1,
                      "submit_time": 1511961018,
                      "type": "站外"
                  },
                  {
                      "address": "0x5de61aec70dc1654456f75aa964daf754d2a7f30",
                      "amount": "5.00000000",
                      "confirmTimes": 0,
                      "currency": "ETH",
                      "hash": "",
                      "id": 15,
                      "status": 1,
                      "submit_time": 1507882027,
                      "type": "系统充值"
                  }
              ]
          }
}
```
----
### **Response状态**
> 1000; //成功
>
> 1001; //一般错误
>
> 1002; //内部错误
>
> 1003; //验证不通过
>
> 1004; //网站维护中
>
> 1005;// API接口维护中
>
> 1006; //权限不足
>
> 1007; //无效的参数
>
> 1008; //无效的IP或与绑定的IP不一致
----
### **签名方式**
>请求参数按照ASCII值排序，然后通过hmac MD5加密
>
*javascript*
```javascript
    function sign(params, secretKey) {
            if (typeof params != 'object') {
                throw Error('参数必须为对象')
            }
            let preSign = [];
            for (let key of Object.keys(params).sort()) {
                preSign.push(key+'='+params[key]);
            }
            return CryptoJS.HmacMD5(preSign.join('&'), secretKey).toString();
    }
```
*php*
```php
    function sign(array $params, $secretKey)
    {
        ksort($params);
        $preSign = http_build_query($params, '', '&');
        $sign = hash_hmac('md5', $preSign, $secretKey);
        return $sign;
    }
```
*java*
> 代码库中 SignUtil.java
>
*postman 交易API测试*
> Params
>
> | 参数名        |     值      |
> | :--------:  | :-----:   |
> |reqTime|{{sign}}	|
> |sign	|{{reqTime}}|
>
*Pre-request Script*
```javascript
    function signfn(params, secretKey) {
        let preSign = [];
        for (let key of Object.keys(params).sort()) {
            if (key == 'sign') {
                console.log(params[key]);
            }
            if (key === 'sign' || params[key] === '') {
                continue;
            }
            preSign.push(key+'='+params[key]);
        }
        return CryptoJS.HmacMD5(preSign.join('&'), secretKey).toString();
    }

    let now = Math.floor(Date.now());
    pm.globals.set("reqTime",  now);
    let query = {};
    pm.request.url.query.all().forEach((param) => { query[param.key] = param.value});
    query.reqTime = now;
    pm.globals.set("sign",  signfn(query, '8d06dae1-72ef-4d9c-82ca-5210b1a1dc48'));
```
----

### **Ws获取全部市场行情**
*Request*
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |event	|string|	Y	|addChannel|
> |channel|	string|	Y	|all_ticker|
>
*Response*

```html
        {
             "channel": "all_ticker",
             "date": "1472800466093",
             "data":
             {
                 "ceo_qc": { //  市场名
                 "buy": "91.00000000", //  买一价
                 "sell": "91.50000000", //  卖一价
                 "last": "90.00000000", //  最新成交价
                 "vol": "0.00000000", //  成交量(最近的24小时)
                 "high": "0.00000000", //  最高价
                 "low": "0.00000000" //  最低价
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
         }
```
----
### **Ws获取市场行情**
*Request*
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |event	|string|	Y	|addChannel|
> |channel|	string|	Y	|ceo_qc_ticker|
>
*Response*

```html
      {
            "channel": "ceo_qc_ticker",
            "date": "1472800466093",
            "ticker":
            {
                "buy": "91.00000000", //  市场名
                "sell": "91.50000000", //  买一价
                "last": "90.00000000", //  卖一价
                "vol": "0.00000000", //  最新成交价
                "high": "0.00000000", //  成交量(最近的24小时)
                "low": "0.00000000" //  最高价
            }
        }
```
----
### **Ws获取市场深度**
*Request*
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |event	|string|	Y	|addChannel|
> |channel|	string|	Y	|ceo_qc_order|
>
*Response*

```html
      {
           "date" : 1567582150426 ,
           "b": [ // 买
               [
                   "11.37", //  价格
                   "877.627331" //  数量
               ],
               [
                   "11.37"
                   "877.627331"
               ],
               ......
           ],
           "s":[ // 卖
               [
                   "11.37"
                   "877.627331"
               ],
               [
                   "11.37",
                   "877.627331"
               ],
               ......
           ],
           "channel": "ceo_qc_order"
       }
```
----
### **Ws获取历史成交**
*Request*
> | 参数        | 类型   |  必填   |  描述   |
> | :--------:  | :-----:  |  :-----:  |  :-----:  |
> |event	|string|	Y	|addChannel|
> |channel|	string|	Y	|ceo_qc_trade|
>
*Response*

```html
       {
            "date" : 1567582150426 ,
            "data": [
                {
                    "amount": "5000.000000", //  交易数量
                    "price": "0.400000", //  交易价格
                    "type": 2, //  交易类型，1(买)/2(卖)
                    "time": 1530144000 //  交易时间(时间戳)
                },
                ......
            ],
            "channel": "ceo_qc_trade"
        }
```
----
### **访问限制**

>单个IP限制每分钟3000次访问
>
>交易API单个用户限制每秒钟50次访问


 #### 接口示例

* 公共

```python
import requests

ROOT_URL = 'https://www.mxc.com'

headers = {
    'Content-Type': 'application/json',
    'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.71 Safari/537.36',
    "Accept": "application/json",
}
```

> ###### 获取市场列表信息 python demo

```python
url = ROOT_URL + '/open/api/v1/data/markets'
response = requests.request('GET', url, headers=headers)
print(response.json())
```

> ###### 获取交易对信息 python demo

```python
url = ROOT_URL + '/open/api/v1/data/markets_info'
response = requests.request('GET', url, headers=headers)
print(response.json())
```

> ###### 获取深度信息 python demo

```python
symbol = 'BTC_USDT'
depth = 30
params = {'market': symbol,
          'depth': depth}
url = ROOT_URL + '/open/api/v1/data/depth'
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

> ###### 获取单个币种成交记录信息 python demo

```python
symbol = 'BTC_USDT'
params = {'market': symbol}
url = ROOT_URL + '/open/api/v1/data/history'
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

> ###### 获取市场行情信息 python demo

```python
symbol = 'BTC_USDT'
params = {'market': symbol}
url = ROOT_URL + '/open/api/v1/data/ticker'
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

> ###### 获取市场K线信息 python demo

```python
import time
symbol = 'BTC_USDT'
params = {'market': symbol,
          'interval': '1m',
          'startTime': int(time.time() / 60) * 60 - 60 * 5,
          'limit': 5}
url = ROOT_URL + '/open/api/v1/data/kline'
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

* 私有

```python
import time
import hashlib

API_KEY = 'your api key'
SECRET_KEY = 'your secret key'

def sign(params):
    sign = ''
    for key in sorted(params.keys()):
        sign += key + '=' + str(params[key]) + '&'
    response_data = sign + 'api_secret=' + SECRET_KEY
    return hashlib.md5(response_data.encode("utf8")).hexdigest()
```

> ###### 获取账户资产信息 python demo

```python
url = ROOT_URL + '/open/api/v1/private/account/info'
params = {'api_key': API_KEY,
          'req_time': time.time()}
params.update({'sign': sign(params)})
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

> ###### 获取当前委托信息 python demo

```python
symbol = 'BTC_USDT'
trade_type = 0
params = {'api_key': API_KEY,
          'req_time': time.time(),
          'market': symbol,
          'trade_type': trade_type,  # 交易类型，0/1/2 (所有/买/卖)
          'page_num': 1,
          'page_size': 50}
params.update({'sign': sign(params)})
url = ROOT_URL + '/open/api/v1/private/current/orders'
response = requests.request('GET', url, params=params, headers=headers)
print(response.json())
```

> ###### 下单 python demo

```python
symbol = 'BTC_USDT'
price = 9999
quantity = 66
trade_type = 1  # 1/2 (买/卖)
params = {'api_key': API_KEY,
          'req_time': time.time(),
          'market': symbol,
          'price': price,
          'quantity': quantity,
          'trade_type': trade_type}
params.update({'sign': sign(params)})
url = ROOT_URL + '/open/api/v1/private/order'
response = requests.request('POST', url, params=params, headers=headers)
print(response.json())
```

> ###### 取消订单 python demo

```python
symbol = 'BTC_USDT'
order_id = '3cd4bd41-****-****-****-d593f8eea202'
params = {'api_key': API_KEY,
          'req_time': time.time(),
          'market': symbol,
          'trade_no': order_id}
params.update({'sign': sign(params)})
url = ROOT_URL + '/open/api/v1/private/order'
response = requests.request('DELETE', url, params=params, headers=headers)
print(response.json())
```

> ###### 查询账号历史委托记录 python demo

```python
symbol = 'EOS_ETH'
deal_type = 1
params = {'api_key': API_KEY,
          'req_time': time.time(),
          'market': symbol,
          'trade_type': deal_type,
          'page_num': 1,
          'page_size': 70}
params.update({'sign': sign(params)})
url = ROOT_URL + '/open/api/v1/private/orders'
response = requests.request('GET', url, params=params)
print(response.json())
```

> ###### 查询订单状态 python demo

```python
symbol = 'EOS_ETH'
trade_no = 'f5718b8a-8f93-4880-8e95-281fe28efb91'
params = {'api_key': API_KEY,
          'req_time': time.time(),
          'market': symbol,
          'trade_no': trade_no}
params.update({'sign': sign(params)})
url = ROOT_URL + '/open/api/v1/private/order'
response = requests.request('GET', url, params=params)
print(response.json())
```
