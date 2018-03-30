# Easy Payment Mobile 

Integrate Easy Payment on mobile application is similar to other redirect APIs. The only difference is that payment information is sent to LianLian mobile SDKs instead of HTML ```<form>``` tag.

* [Android SDK](https://github.com/LianLianPay/LianLian-Android-SDK)

* [iOS SDK](https://github.com/LianLianPay/LianLian-iOS-SDK)

***

## Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|platform|Optional|String(32)| ```platform``` is used for sharing user info between multiple ```oid_partner```, this requires additional settings from LianLian side|
|user_id|Required|String(32)|The unique identification assigned to the user in the merchant’s system|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|busi_partner|Required|String(6)|Fixed value. Virtual products, ```101001```; Physical products, ```109001```|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|name_goods|Required|String(40)|Product name. E.g. Pen|
|info_order|Optional|String(255)|```info_order``` will be sent back in synchronous or asynchronous notification for parameters transmission|
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|notify_url|Required|String(128)|Online url where asynchronous notification should be sent, E.g. http://www.lianlianpay.com/help/notify|
|valid_order|Optional|Int|The valid period of ```no_order```, in minute. The status of corresponding transaction will be set to "Closed" once its ```valid_order``` run out. Default: 10080 (7 days). |
|pay_type|Required|String| M, regular payments <br> F, authorization, used for credit card only. An error throws out if the used card is not a credit card|
|risk_item|Required|String| This parameter is used for payment risk control, all required parameters should be included in the value of ```risk_item``` in json format, refer to [Payment Risk](payment_risk_item.md)| 
|no_agree|Optional|String(32)| A token which represents the key payment information, refer to [Binding Card](easypay.md) for more details|
|id_type|Required|String(1)| 0, ID card <br> 2, Passport <br> 3, Military Officer Certificate <br> 4, Hong Kong-Macau laissez-passer <br> 6, Mainland travel permit for Taiwan residents <br> 9, Police Officer card <br> X, other certificates |
|id_no|Required|String| The length need to be either 15 or 18|
|acct_name|Required|String|The name of payer, in Chinese. Required for Verified Payment |
|card_no|Optional|String|User's card number|

###### Sample

```json
{
	"oid_partner":"201103171000000000",
	"dt_order":"20130515094013",
	"no_order":"2013051500001",
	"busi_partner":"101001",
	"name_goods":"羽毛球",
	"info_order":"用户13958069593购买羽毛球3桶",
	"money_order":"210.97",
	"notify_url":"http://.../notify_url.shtml",
	"pay_type":"2",
	"bank_code":"01020000",
	"force_bank":"1",
	"sign_type":"RSA",
	"valid_order":"30",
	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```

***

## Flow


![](../textures/Easypay_mobile_flow.svg)
