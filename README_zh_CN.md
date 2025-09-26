# PidKeyTool  CN/EN Version
网页版: [https://pidkey.top](https://pidkey.top/?lang=cn)
## 微软密钥检测工具  
检测机器人:  
QQ: [3390735069](http://wpa.qq.com/msgrd?v=3&uin=3390735069&site=qq&menu=yes)   
微信: tc_90222

## 内容导引
| 章节 | 描述 |
|-|-|
| [简介](#简介) | 软件简介 |
| [更新记录](#更新记录) | 版本更新记录 |
| [问题](#问题) | 一些常见问题解答 |
| [软件截图](#软件截图) | 运行界面 |
| [抓包截图](#抓包截图) | 抓包查看是否有第三方链接 |
| [错误代码](#错误代码) | 常见错误代码解释 |
| [密钥相关网站](#密钥相关网站) | 一些密钥网站推荐 |


## 简介
Windows/Office密钥检测工具  
可用于检测零售密钥的有效状态和批量密钥的剩余次数.  
无需系统证书环境支持.直连微软服务器检测.  
检测结果存储于软件目录的KeyList.db数据库中.   

## 更新记录
v3.0 支持离线检测Office兑换密钥类型.   
v2.5 加入webact检测.   
v2.0 加入绑定密钥检测.   
v1.5 加入随机硬件模拟.   

## 问题
    1. 问：用该工具会不会泄露密钥? 
       答：该检测工具的原理是:解码密钥后，通过模拟硬件数据结合密钥数据生成用户证书，发包给微软服务器获取返回结果，所以至始至终只连接微软服务器，如果不放心可以用相关工具抓包分析是否有第三方链接地址。 
    2. 问：会不会对本机造成影响?
       答：传统的密钥检测工具通过安装密钥到系统获取系统返回的错误代码，该工具直接绕过了这一步，所以跟系统证书没有任何关系。
    3. 问：我想知道检测结果为020的密钥是否还能通过微软的电话自助网页(Microsoft Self Service for Mobile site)在线获取确认ID？
       答：菜单中有设置是否要获取该项结果的设置，如果你不知道webact的Token值，软件已经内置了，可以不用设置。注意该项设置会影响检测速度。
    4. 问：能不能检测Office绑定密钥还是否有效?
       答：可以。支持不登录账号检测兑换密钥类型,但是如果你要检测是否有效需要登陆自己的微软账户(https://account.microsoft.com/billing/redeem)检测，该账户信息会记录在注册表中(HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers下的OutlookUsername和OutlookPassword)，以便下次不用再次登陆。纯本地操作，完全不用担心泄露账号。  
    5. 问：每次更新软件后原来的检测结果会不会丢失?  
       答：密钥的检测结果存储于目录的KeyList.db，该数据库没有加密，你可以用DB Browser for SQLite（https://sqlitebrowser.org/ )直接打开浏览，同一目录下该数据库不会被覆盖，你也可以移动旧的数据库到升级后软件的目录。
    6. 问：密钥复活了怎么检测?  
       答：在密钥管理菜单右键，有重新检测菜单，可以选中所有需要重新检测的密钥列表进行重新检测。如果主程序界面是批量检测界面，将会检测所有选中的密钥。如果是单独检测界面，只有检测一个密钥。  
    7. 问：检测会消耗密钥次数吗?    
       答：对于零售的在线密钥,会消耗一次,因为必须通过微软服务器验证是否有效,008、020密钥因为没有激活过程所以不会消耗.     
    8. 问：工具为什么会报毒?    
       答：为了防止代码被反编译，所以对工具进行了加壳处理，所以杀毒软件就会报毒。软件本身没有病毒，放心使用。   
    9. 问：有相关控件可以供我的程序调用吗?   
       答：目前还没有公开相关控件，但是程序做了静默参数供调用，详细看说明.   

## 软件截图
![image](https://github.com/laomms/PidKeyBatch/blob/master/checks.gif)

## 抓包截图
![image](https://github.com/laomms/PidKeyBatch/blob/master/record.gif)

## 错误代码
    注意：一般密钥密钥不包含：A,E,I,L,O,S,U这些字母，除非是一些绑定型的兑换密钥。  
    * 错误代码：0XC004C003
    常数名称：SL_E_CHPA_PRODUCT_KEY_BLOCKED
    描述：激活服务器确定指定的产品密钥已被阻止。
    * 错误代码：0XC004C060
    常数名称：SL_E_CHPA_DYNAMICALLY_BLOCKED_PRODUCT_KEY
    描述：激活服务器确定指定的产品密钥已被阻止。
    * 错误代码：0XC004C020
    常数名称：SL_E_CHPA_DMAK_LIMIT_EXCEEDED
    描述：激活服务器报告该密钥已超出其在线激活次数限制。
    * 错误代码：0XC004C008
    常数名称：SL_E_CHPA_MAXIMUM_UNLOCK_EXCEEDED
    描述：激活服务器报告产品密钥已超出其在线激活次数限制。
    * 错误代码：0XC004C004
    常数名称：SL_E_CHPA_INVALID_PRODUCT_KEY
    描述：激活服务器确定指定的产品密钥无效。
    * 错误代码：0XC004C00D
    常数名称：SL_E_CHPA_INVALID_ACTCONFIG_ID
    描述：激活服务器确定产品密钥无效。
    * 错误代码：0XC004F069
    常数名称：SL_E_MISMATCHED_PRODUCT_SKU
    描述：软件授权服务报告找不到产品sku，系统未发现该密钥证书。
    * 错误代码：0XC004E016
    常数名称：SL_E_PKEY_INVALID_CONFIG
    描述：软件授权服务报告产品密钥与系统SKU不一致。
    * 错误代码：0XC004F050
    常数名称：SL_E_INVALID_PRODUCT_KEY
    描述：软件授权服务报告产品密钥与版本不符。
     

 <!---
 [![](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.sandbox.paypal.com/donate?hosted_button_id=WTE9HCGSXGTAN)
 -->
 






