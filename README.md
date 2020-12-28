# bot-API
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

## 清仓卖出 
说明：清除指定的交易对里所有的持仓  
请求方式： `GET`  
路径：clean_position   

参数：  
  * account_id 账号id   
  * currency 交易对    
  
返回：（json）  
  * code  200成功  
  * data  
    * msg 消息
    
## 获取机器人列表
说明：通过account_id获取这个账号下所有运行中的机器人  
请求方式： `GET`  
路径：get_bot_list   

参数：  
  * account_id 账号id   
  
返回：（json）  
  * code  200成功  
  * data  
    * list  
      * bot_id 机器人id
      * currency 交易对
      * param 参数 空格隔开
      * num 持仓数量
      * num_ 持仓金额
      * win_rate 浮盈比例
      * rate 当日涨跌比例

## 获取单个机器人状态详情
说明：通过account_id获取这个账号下所有运行中的机器人  
请求方式： `GET`  
路径：get_bot_list   

参数：  
  * account_id 账号id  
  * bot_id 机器人id  
  
返回：（json）  
  * code  200成功  
  * data  
    * param 参数 空格隔开
    * currency 交易对
    * num 持仓数量
    * num_ 持仓金额
    * win_rate 浮盈比例
    * rate 当日涨跌比例
    * last 当前价格
    * avg_price 持仓均价
    * times 补仓次数

## 获取运行日志
请求方式： `GET`  
路径：get_logs   

参数：  
  * account_id 账号id  
  * bot_id 机器人id(可选，不传返回所有机器人日志)  
  * page 翻页参数，从1开始
  
返回：（json）  
  * code  200成功  
  * data  
    * list
      * currency 交易对
      * content 日志内容
      * time 日志时间

## 历史成交订单
请求方式： `GET`  
路径：get_history_orders   

参数：  
  * account_id 账号id  
  * currency 交易对(可选参数)
  * page 翻页参数，从1开始
  
返回：（json）  
  * code  200成功  
  * data  
    * list
      * currency 交易对
      * order_id 订单id
      * price 委托价格
      * num 委托数量
      * num_traded 成交数量
      * state 状态（0 未成交 1 已成交 2 已撤单）
      * order_time 委托时间

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
