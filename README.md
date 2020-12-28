# bot-API
接口访问方式：GET
参数说明： 接口中出现的currency参数格式统一用小写字母，并用下划线'_'连接，如 btc_usdt  

接口前缀：http://www.ljlightning.com/index.php/r/

接口：  
  1. 创建账号，存储apikey和私钥  

  2. 机器人参数设置（新建/编辑）

  3. 启动机器人（需要指定循环方式）

  4. 停止机器人

  5. 批量设置参数

  6. 批量启动

  7. 批量停止

  8. 获取机器人列表（含 当前运行浮盈浮亏和持仓）

  9. 单个机器人工作状态接口（含补仓次数）

  10. 获取运行日志

  11. 历史成交订单

  12. 账户资产

  13. 获取机器人

  14. 清仓卖出

## 创建账号，存储apikey和私钥（返回账号id）
请求方式： `GET`  
路径：create_account 

参数：  
  * account_name 账号名  
  * web 交易所（可选：huobi 火币 | ok OK | bian 币安）  
  * api_key apikey  
  * api_secret 私钥  
  
返回：（json）  
  * code  200成功  
  * data  
    * account_id 账号id  
    * msg 消息  
      
## 修改账号，包括账号名，apikey和私钥
请求方式： `GET`  
路径：edit_account 

参数：  
  * account_id 账号id    
  * account_name 账号名  
  * web 交易所（可选：huobi 火币 | ok OK | bian 币安）  
  * api_key apikey  
  * api_secret 私钥  
  
返回：（json）  
  * code  200成功  
  * data  
    * msg 消息  
    
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
    
## 获取机器人列表（含 当前运行浮盈浮亏和持仓）
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
  * currency 交易对
  * bot_id 机器人id(可选，不传返回所有机器人日志)  
  * page 翻页参数，从1开始
  
返回：（json）  
  * code  200成功  
  * data  
    * list
      * currency 交易对
      * content 日志内容
      * time 日志时间
