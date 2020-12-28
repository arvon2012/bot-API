# bot-API
接口访问方式：GET

接口前缀：http://www.ljlightning.com/index.php/r/

接口：
  1. 创建账号，存储apikey和私钥（返回账号id）

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

创建账号，存储apikey和私钥（返回账号id）
--------
请求方式： `GET`  
路径：create_account 

参数：  
  * account_name 账号名  
  * api_key apikey  
  * api_secret 私钥  
  
返回：（json）  
  * code  200成功  
  * data  
    * account_id 账号id  
    * msg 消息  
      
      
    
