切换 [简体中文](README_zh_CN.md)

# PidKeyTool CN/EN Version
Web version: [https://pidkey.vip](https://pidkey.vip/)     

Telegram bot: [@laomms](https://t.me/laomms)  
Telegram group: [GETCID Group1](https://t.me/get_cid)   
WhatsApp Bot: [tcbkk](https://wa.me/message/ETQAZKDFCSZCF1)  
Discord Channel: [GetCID](https://discord.gg/JDygTcRhhZ)  
Slack Channel: [#get-cid](https://join.slack.com/t/getcid/shared_invite/zt-3fxhdkmc7-pnAkb9D52eYFjVwOWq_sMw)  
LineBot/Group: [@bti0006p](https://line.me/R/ti/g/pBM6qdZhXA)  
QQ bot: [3390735069](http://wpa.qq.com/msgrd?v=3&uin=3390735069&site=qq&menu=yes)   
Wechat bot: tc_90222    

## Microsoft Key Detection Tool

## Content guide
| Chapter | Description |
|-|-|
| [Introduction](#Introduction) | Software Introduction |
| [UpdateRecord](#UpdateRecord) | Version update record |
| [question](#question) | Some FAQs |
| [ScreenShot](#ScreenShot) | Running interface |
| [ScreenCapture](#ScreenCapture) | Capture package to see if there is a third-party link |
| [ErrorCode](#ErrorCode) | Explanation of common error codes |
| [KeyRelatedSite](#KeyRelatedSite) | Some key websites are recommended |


## Introduction
Windows/Office Key Detection Tool
Can be used to detect the validity state of retail keys and the remaining number of times for MAK keys.
No need for system certificate environment support. Direct connection to Microsoft server detection.
The detection results are stored in the KeyList.db database in the software catalog.

## UpdateRecord
v3.0 supports offline detecting Office redemption key.    
v2.5 Added webact detection.    
v2.0 added redeem key detection.    
v1.5 Added random hardware emulation.    

## question
    1. Q: Will this tool reveal the key?
       A: This tool work process is: after decoding the key, it generates a user license by simulating hardware data combined with key data, and post to the Microsoft server to obtain the returned result, so it only connects to the Microsoft server. Or you can use captures tool to analyzes whether there is a third-party link address.
    2. Q: Will it affect the machine?
       A: The traditional key detection tool obtains the retail key result by installing the key to the system and get return error code. The tool directly bypasses this step, so it has nothing to do with the system certificate.
    3. Q: I would like to know if a key with a test result of 020 can still obtain a confirmation ID online through Microsoft's Self Service for Mobile site?
       A: Yes. There is a setting in menu to choose whether to get the result of webact. If you do not know the Token value of webact, the software is already built-in, so you do not need to set it. Note that this setting will affect the detection speed.
    4. Q: Can determine whether the redeemable key of Office is valid?
       A: Yes. Support to detect the redemption key type without logging in to the account.but if you want to check whether it is valid, you need to login your "setup.office.com" Microsoft account for detection, and the account information will be recorded in the registry (OutlookUsername and OutlookPassword under HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers).
    5. Q: Will the original test results database be lost after every software update?
       A: The detection result of the key is stored in KeyList.db in the directory. The database is not encrypted. You can use DB Browser for SQLite (https://sqlitebrowser.org/ ) to open and browse directly. The database in the same directory will not be overwritten. , you can also move the old database to the directory of the upgraded software.
    6. Q: How to detect the resurrection of the key?
       A: Right-click in the key management menu, there is a re-detection menu, you can select all the key lists that need to be re-detected for re-detection. If the main program interface is the batch detection interface, all selected keys will be detected. If it is a separate detection interface, only one key is detected.
    7. Q: Will the detection consume the remaining times of the key??
       A: For the retail online key, it will be consumed once, because it must be verified by the Microsoft server and return a user license. The 008 and 020 keys will not be consumed because there is no activation process.
    8. Q: Why does the anti-virus tool report a virus?
       A: In order to prevent the code being decompiled, the tool is packed, so the anti-virus software will report the virus. The software itself has no virus, so use it with confidence.
    9. Q: Is there any relevant library for calling in my program ?
       A: At present, the relevant controls have not been exposed, but the program has made silent parameters for calling, see the description in detail.    

## ScreenShot
![image](https://github.com/laomms/PidKeyBatch/blob/master/checks.gif)

## ScreenCapture
![image](https://github.com/laomms/PidKeyBatch/blob/master/record.gif)

## ErrorCode
    Note: Most keys do not contain the letters A, E, I, L, O, S, U, unless they are bound redemption keys.  
    * Error code: 0XC004C003
    Constant: SL_E_CHPA_PRODUCT_KEY_BLOCKED
    Description: The activation server determined the specified product key has been blocked.
    * Error code: 0XC004C060
    Constant: SL_E_CHPA_DYNAMICALLY_BLOCKED_PRODUCT_KEY
    Description: The activation server determined the specified product key has been blocked.
    * Error code: 0XC004C020
    Constant: SL_E_CHPA_DMAK_LIMIT_EXCEEDED
    Description: The activation server reported that the Multiple Activation Key has exceeded its limit.
    * Error code: 0XC004C008
    Constant: SL_E_CHPA_MAXIMUM_UNLOCK_EXCEEDED
    Description: The activation server reported that the product key has exceeded its unlock limit.
    * Error code: 0XC004C004
    Constant: SL_E_CHPA_INVALID_PRODUCT_KEY
    Description: The activation server determined the specified product key is invalid.
    * Error code: 0XC004C00D
    Constant: SL_E_CHPA_INVALID_ACTCONFIG_ID
    Description: The activation server determined the product key is not valid.
    * Error code: 0XC004F069
    Constant: SL_E_MISMATCHED_PRODUCT_SKU
    Description: The Software Licensing Service reported that the product SKU is not found.
    * Error code: 0XC004E016
    Constant: SL_E_PKEY_INVALID_CONFIG
    Description: The Software Licensing Service reported that the product key is invalid.
    * Error code: 0XC004F050
    Constant: SL_E_INVALID_PRODUCT_KEY
    Description: The Software Licensing Service reported that the product key is invalid.
     
 

