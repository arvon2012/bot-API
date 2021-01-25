# Light Bot API
## 产品介绍
[闪电官网链接](http://www.ljlightning.com)  
闪电机器人云系统是一款已经稳定运行3年，服务过数百家项目方，支持上百个交易所的机器人云系统。  
我们为大家提供了极其简单易懂的API，接入后就可以轻松的开启和管理机器人。  
云系统目前支持的交易所超过100家，覆盖绝大多数一二三线交易所。  
支持的`机器人`包括：
  * 高抛低吸机器人
  * 冰山挂单机器人
  * 搬砖机器人
  * 网格机器人
  * 对敲机器人
  * 深度维护（摆盘）机器人
  * 大单护盘机器人
  * 画线机器人
  * 跟盘机器人
  * 主流币做市机器人
  * Dex跟盘机器人（Uniswap）
  
商务合作 ^_^ （微信Wechat）：  
琪琪 q1751365540  
娜娜 nana-99909  

## 接口概述
接口访问方式：GET
参数说明： 接口中出现的currency参数格式统一用小写字母，并用下划线'_'连接，如 btc_usdt  

接口前缀：http://api.lightbot.world/index.php/r/  
  
接口：  
  1. [创建账号，存储apikey和私钥](#创建账号存储apikey和私钥)  
  
  2. [获取账号信息](#获取账号信息)  

  3. [修改账号，包括账号名，apikey和私钥](#修改账号包括账号名apikey和私钥)

  4. [机器人参数设置（创建/编辑/启动/停止）](#机器人参数设置创建编辑启动停止)

  5. [机器人批量参数设置（创建/编辑/启动/停止）](#机器人批量参数设置创建编辑启动停止)

  6. [清仓卖出](#清仓卖出)

  7. [获取机器人列表](#获取机器人列表)

  8. [单个机器人工作状态接口](#单个机器人工作状态接口)

  9. [获取运行日志](#获取运行日志)

  10. [历史成交订单](#历史成交订单)

  11. [账号资产](#账号资产)

  12. [获取账户盈利列表](#获取账户盈利列表)

## 创建账号，存储apikey和私钥
请求方式： `GET`  
路径：create_account 

参数：  
  * access_token 系统提供，创建账号必传  
  * web 交易所（可选：huobi 火币 | ok OK | bian 币安）  
  * api_key apikey  
  * api_secret 私钥  
  * other_key 其他必要信息（如ok中的passphrase）  
  
返回：（json）  
  * code  200成功  
  * data  
    * account_id 账号id  
    * msg 消息  

实例：  
请求：http://api.lightbot.world/index.php/r/create_account?access_token=test&web=huobi&api_key=333&api_secret=222&other_key=  
返回：  
```Java
{
    "code": 200,
    "data": {
        "msg": "创建成功",
        "account_id": "3t54HV1609139461"
    }
}
```



## 获取账号信息
请求方式： `GET`  
路径：get_account 

参数：  
  * account_id 账号id    
  
返回：（json）  
  * code  200成功  
  * data  
    * web 交易所（可选：huobi 火币 | ok OK | bian 币安）  
    * api_key apikey  
    * api_secret 私钥   
    * other_key 其他必要信息（如ok中的passphrase） 
    
实例：  
请求：http://api.lightbot.world/index.php/r/get_account?account_id=3t54HV1609139461  
返回：  
```Java
{
    "code": 200,
    "data": {
        "api_key": "333",
        "api_secret": "222",
        "other_key": "0",
        "web": "huobi"
    }
}
```

## 修改账号，包括账号名，apikey和私钥
请求方式： `GET`  
路径：edit_account 

参数：  
  * account_id 账号id    
  * web 交易所（可选：huobi 火币 | ok OK | bian 币安）  
  * api_key apikey  
  * api_secret 私钥  
  * other_key 其他必要信息（如ok中的passphrase）  
  
返回：（json）  
  * code  200成功  
  * data  
    * msg 消息  

实例：  
请求：http://api.lightbot.world/index.php/r/edit_account?account_id=3t54HV1609139461&web=huobi&api_key=33334&api_secret=22223&other_key=11  
返回：  
```Java
{
    "code": 200,
    "data": {
        "msg": "编辑成功"
    }
}
```
    
## 机器人参数设置（创建/编辑/启动/停止）
请求方式： `GET`  
路径：set_bot   

参数：  
  * account_id 账号id    
  * currency 交易对（小写并用下滑线连接，如 btc_usdt）  
  * type 机器人类型（可选值：wangge 网格机器人）  
  * param 机器人参数列表，空格隔开， 如 8 0.01 0.003 0.01 0.003    
  * state 状态 如 1 启动 0 停止  
  * times 循环次数  
  
返回：（json）  
  * code  200成功  
  * data  
    * bot_id 机器人id
    * msg 消息  

实例：  
请求：http://api.lightbot.world/index.php/r/set_bot?account_id=9DXJY71609141556&currency=btc_usdt&type=wangge&param=1 2 3 1&state=1&times=10  
返回：  
```Java
{
    "code": 200,
    "data": {
        "msg": "机器人设置成功"
    }
}
```
    
    
## 机器人批量参数设置（创建/编辑/启动/停止）
请求方式： `GET`  
路径：set_bot_multi   

参数：  
  * account_id 账号id    
  * currency 交易对（小写并用下滑线连接，如 btc_usdt， 多个交易对用空格隔开）  
  * type 机器人类型（可选值：wangge 网格机器人）  
  * param 机器人参数列表，空格隔开， 如 8 0.01 0.003 0.01 0.003    
  * state 状态 如 1 启动 0 停止  
  * times 循环次数  
  
返回：（json）  
  * code  200成功  
  * data  
    * bot_id_list 机器人id列表，用空格连接
    * msg 消息  

实例：  
请求：http://api.lightbot.world/index.php/r/set_bot_multi?account_id=9DXJY71609141556&currency=btc_usdt eth_usdt eos_usdt&type=wangge&param=1 2 3 1&state=1&times=10  
返回：  
```Java
{
    "code": 200,
    "data": {
        "msg": "机器人批量设置成功",
        "bot_id": [
            "1842",
            "1846",
            "1847"
        ]
    }
}
```

## 清仓卖出 
说明：清除指定的交易对里所有的持仓  
请求方式： `GET`  
路径：clean_position   

参数：  
  * account_id 账号id   
  * bot_id 要清仓的机器人ID    
  
返回：（json）  
  * code  200成功  
  * data  
    * msg 消息

实例：  
请求：http://api.lightbot.world/index.php/R/clean_position?account_id=9DXJY71609141556&bot_id=123  
返回：  
```Java
{
    "code": 200,
    "data": {
        "msg": "完成清仓,机器人已彻底停止"
    }
}
```
    
## 获取机器人列表
说明：通过account_id获取这个账号下所有运行中的机器人  
请求方式： `GET`  
路径：get_bot_list   

参数：  
  * account_id 账号id   
  * state 机器人状态 0是已停止 1是运行中 不传则全部返回(可选参数)   
  
返回：（json）  
  * code  200成功  
  * data  
    * list  
      * bot_id 机器人id
      * type 机器人类型
      * param 参数 空格隔开
      * currency 交易对
      * sub_type 循环次数（机器人启动后工作几轮 10000代表无限次）
      * state 当前运行状态0代表停止 1代表正在运行
      * num 持仓数量
      * num_ 持仓金额
      * avg_price 持仓均价
      * times 补仓次数
      * win_rate 浮盈比例
      * last 盘口最新价格
      * rate 当日涨跌比例
      

实例：  
请求：http://api.lightbot.world/index.php/r/get_bot_list?account_id=9DXJY71609141556  
返回：  
```Java
{
    "code": 200,
    "data": {
        "list": [
            {
                "bot_id": "1934",
                "type": "wangge",
                "param": "10 1hour 0.01 3 0.01 0.002 0.02 0.003",
                "currency": "eth_usdt",
                "sub_type": "2",
                "state": "0",
                "num": "0.0373",
                "num_": "40",
                "avg_price": 1072.3860589812,
                "times": "1",
                "win_rate": -0.0056939,
                "last": 1066.28,
                "rate": -0.04886
            },
            {
                "bot_id": "1847",
                "type": "wangge",
                "param": "10 3 0.02 0.002 0.01 0.002 1",
                "currency": "eos_usdt",
                "sub_type": "2",
                "state": "1",
                "num": "2.5872",
                "num_": "7",
                "avg_price": 2.7056277056277,
                "times": "2",
                "win_rate": -0.0029300799999998,
                "last": 2.6977,
                "rate": -0.00955
            }
        ],
        "msg": "完成"
    }
}
```

## 获取单个机器人状态详情
说明：通过account_id获取这个账号下所有运行中的机器人  
请求方式： `GET`  
路径：get_bot   

参数：  
  * account_id 账号id  
  * bot_id 机器人id  
  
返回：（json）  
  * code  200成功  
  * data  
    * param 参数 空格隔开
    * type 机器人类型
    * currency 交易对
    * sub_type 循环次数（机器人启动后工作几轮 10000代表无限次）
    * state 当前运行状态0代表停止 1代表正在运行
    * num 持仓数量
    * num_ 持仓金额
    * avg_price 持仓均价
    * times 补仓次数
    * win_rate 浮盈比例
    * last 当前价格
    * rate 当日涨跌比例
    
实例：  
请求：http://api.lightbot.world/index.php/r/get_bot?account_id=9DXJY71609141556&bot_id=1847  
返回：  
```Java
{
    "code": 200,
    "data": {
        "list": [
            {
                "bot_id": "1847",
                "type": "wangge",
                "param": "10 3 0.02 0.002 0.01 0.002 1",
                "currency": "eos_usdt",
                "sub_type": "2",
                "state": "1",
                "num": "2.5872",
                "num_": "7",
                "avg_price": 2.7056277056277,
                "times": "2",
                "win_rate": -0.0034475199999999,
                "last": 2.6963,
                "rate": -0.00681
            }
        ],
        "msg": "完成"
    }
}
```

## 获取运行日志
请求方式： `GET`  
路径：get_logs   

参数：  
  * account_id 账号id  
  * currency 交易对(可选，不传返回所有机器人日志)  
  * page 翻页参数，从1开始，排序默认从新到旧
  * id （可选）从某个id开始取日志，填写该参数后，返回的数据排序将从旧到新
  
返回：（json）  
  * code  200成功  
  * data  
    * list
      * id ID序号
      * currency 交易对
      * content 日志内容
      * time 日志时间

实例：  
请求：http://api.lightbot.world/index.php/r/get_logs?account_id=9DXJY71609141556&page=1&currency=btc_usdt  
返回：  
```Java
{
    "code": 200,
    "data": {
        "list": [
            {
                "id": "10535544",
                "content": "[网格机器人5] 最新价格 34579.38 上次交易价格 34716.85 目前持仓均价 34730.538922156",
                "time": "2021-01-13 16:24:13",
                "currency": "btc_usdt"
            },
            {
                "id": "10535543",
                "content": "[机器人启动] 抱歉, 您的权限不足, 无法开启该机器人",
                "time": "2020-12-28 16:03:59",
                "currency": "btc_usdt"
            }
        ]
    }
}
```

## 历史成交订单
请求方式： `GET`  
路径：get_history_orders   

参数：  
  * account_id 账号id  
  * page 翻页参数，从1开始
  * currency 交易对
  * limit 每次返回的数量(可选参数)
  * type 订单类型 1买入 0卖出(可选参数)
  * start 开始时间如: 2020-12-31 00:00:00(可选参数)
  * end 结束时间如: 2021-01-01 00:00:00(可选参数)
  
返回：（json）  
  * code  200成功  
  * data  
    * list
      * web 交易所
      * currency 交易对
      * order_id 订单id
      * price 委托价格
      * num 委托数量
      * num_traded 成交数量
      * avg_price 交易均价
      * fee 手续费
      * profit 盈利
      * state 状态（0 未成交 1 已成交 2 已撤单）
      * type 订单类型 0 卖出 1买入
      * order_time 委托时间


实例：  
请求：http://api.lightbot.world/index.php/r/get_history_orders?account_id=9DXJY71609141556&page=1&currency=btc_usdt  
返回：  
```Java
{
    "code": 200,
    "data": {
        "list": [
            {
                "web": "huobi",
                "currency": "btm_usdt",
                "order_id": "5506170490",
                "price": "0.7",
                "num": "1",
                "num_traded": "1",
                "avg_price": "0.7",
                "fee": "0",
                "profit": "0",
                "state": "1",
                "type": "0",
                "order_time": "2018-06-08 18:09:36"
            },
            {
                "web": "huobi",
                "currency": "btm_usdt",
                "order_id": "4620017607",
                "price": "0.6267",
                "num": "202",
                "num_traded": "202",
                "avg_price": "0.6267",
                "fee": "0",
                "profit": "0",
                "state": "1",
                "type": "1",
                "order_time": "2018-05-18 16:54:32"
            }
        ]
    }
}
```

## 账号资产
请求方式： `GET`  
路径：get_web_balance   

参数：  
  * account_id 账号id  
  
返回：（json）  
  * code  200成功  
  * data  
      * 数组下标 币种大写字母如 USDT
        * balance 可用金额
        * freeze 冻结金额

实例：  
请求：http://api.lightbot.world/index.php/r/get_web_balance?account_id=9DXJY71609141556  
返回：  
```Java
{
    "code": 200,
    "data": {
        "BTC": {
            "balance": 0.01285876,
            "freeze": 0
        },
        "ETH": {
            "balance": 7.78328528,
            "freeze": 0
        }
    }
}
```

## 获取账户盈利列表
请求方式： `GET`  
路径：get_daily_profit   

参数：  
  * access_token   
  * time 可选，日期（格式如：2021-01-01） 
  
返回：（json）  
  * code  200成功  
  * data  
      * time 日期  
      * list 盈利列表  
        * account_id 账号ID
        * profit 当日盈利

实例：  
请求：http://api.lightbot.world/index.php/R/get_daily_profit?access_token=apitest&time=2021-01-15  
返回：  
```Java
{
    "code": 200,
    "data": {
        "time": "2021-01-15",
        "list": [
            {
                "account_id": "9DXJY71609141556",
                "profit": "0"
            },
            {
                "account_id": "3k6kkU1610676695",
                "profit": "0"
            }
        ]
    }
}
```
