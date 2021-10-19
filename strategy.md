# Light Bot Param
## 现货策略
### 智能马丁  
type类型： wangge
times循环方式： 1单次循环(止盈一次就彻底停止) 10000连续循环  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|不含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|止盈回调|float|是|达到止盈幅度后的回调比例，如0.001|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓回调|float|是|达到补仓跌幅后的反弹幅度，如0.001|
|是否平推|int|是|开仓后出现小幅下跌并反弹，再次买入一单开仓单，0关闭，1打开|
|补仓倍数|float|是|每次补仓相对前一次买入金额的倍数，默认2|
|止损价格|float|否|到达价格触发清仓操作，默认传0|


### 底部套利  
type类型： wangge2  
times循环方式： 1 10000  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|周期|string|是|被检测的周期，可选：15m，1h，4h，1d| 
|连续下跌|float|是|周期中连续下跌幅度，如0.1 代表下跌10%|
|补仓次数|int|是|不含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|止盈回调|float|是|达到止盈幅度后的回调比例，如0.001|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓回调|float|是|达到补仓跌幅后的反弹幅度，如0.001|
|止损价格|float|否|到达价格触发清仓操作，默认传0|


### 海浪网格  
type类型： wave  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓宽度缩放|float|是|补仓幅度缩放比例，如2代表每次补仓幅度加倍|
|补仓金额缩放|float|是|补仓金额缩放比例，如2代表每次补仓金额加倍|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
  

## 合约策略
### 智能马丁  
type类型： wangge_f
times循环方式： 1单次循环(止盈一次就彻底停止) 10000连续循环  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|不含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|止盈回调|float|是|达到止盈幅度后的回调比例，如0.001|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓回调|float|是|达到补仓跌幅后的反弹幅度，如0.001|
|是否平推|int|是|开仓后出现小幅下跌并反弹，再次买入一单开仓单，0关闭，1打开|
|补仓倍数|float|是|每次补仓相对前一次买入金额的倍数，默认2|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|多空方向|int|是|1 做多 2 做空|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
  

### 海浪网格  
type类型： wave_f  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓宽度缩放|float|是|补仓幅度缩放比例，如2代表每次补仓幅度加倍|
|补仓金额缩放|float|是|补仓金额缩放比例，如2代表每次补仓金额加倍|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|多空方向|int|是|1 做多 2 做空|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
  

### 海浪对冲多  
type类型： wave_f_long  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓宽度缩放|float|是|补仓幅度缩放比例，如2代表每次补仓幅度加倍|
|补仓金额缩放|float|是|补仓金额缩放比例，如2代表每次补仓金额加倍|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
  

### 海浪对冲空  
type类型： wave_f_long  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额| 
|补仓次数|int|是|含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓宽度缩放|float|是|补仓幅度缩放比例，如2代表每次补仓幅度加倍|
|补仓金额缩放|float|是|补仓金额缩放比例，如2代表每次补仓金额加倍|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|止损价格|float|否|到达价格触发清仓操作，默认传0|

### 手动策略多  
type类型： manual_f_long  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
|止盈价格|float|否|到达价格触发清仓操作，默认传0|
  

### 手动策略空  
type类型： manual_f_short  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
|止盈价格|float|否|到达价格触发清仓操作，默认传0|
  

### 增币策略（币本位永续合约策略）  
type类型： wave_f_coin  
times循环方式： 1  
param:  

|参数|类型|是否必填|备注|
|:-|:-|:-|:-|
|开仓金额|float|是|第一单开仓金额，单位是对应的币数量| 
|补仓次数|int|是|含开仓，总补仓次数|
|止盈幅度|float|是|止盈涨幅（基于整体持仓均价），如0.01|
|补仓幅度|float|是|补仓所需跌幅（基于上次买入价格），如0.01|
|补仓宽度缩放|float|是|补仓幅度缩放比例，如2代表每次补仓幅度加倍|
|补仓金额缩放|float|是|补仓金额缩放比例，如2代表每次补仓金额加倍|
|杠杆倍数|int|是|如1 就是1倍杠杆|
|多空方向|int|是|1 做多 2 做空|
|止损价格|float|否|到达价格触发清仓操作，默认传0|
  