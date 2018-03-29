# Authorization Capture API

## Request

###### Endpoint

```html
https://traderapi.lianlianpay.com/preauthComplete.htm
```

###### Request Parameter

|Name|Required|Type|Description|
|---|---|---|---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|user_id|Required|String(32)|The unique identification assigned to the user in the merchant’s system|
|platform|Optional|String(32)| ```platform``` is used for sharing user info between multiple ```oid_partner```, this requires additional settings from LianLian side|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|pay_type|Required|String| F, authorization payment for credit card <br> G, authorization payment for debit card |
|api_version|Required|String|Fixed value, ```1.0```|
|risk_item|Optional|String| This parameter is used for payment risk control, all required parameters should be included in the value of ```risk_item``` in json format, refer to [Payment Risk](payment_risk_item.md)| 
|no_order|Required|String(32)|Merchant order No. Optional if ```oid_paybill``` is present |
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Optional|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098. Optional if ```no_order``` is present |
|money_order|Optional|String(12)|The authorization amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|

###### Sample Request

```curl
curl https://traderapi.lianlianpay.com/preauthComplete.htm \
-H "Content-type:application/json;charset=utf-8" \
-d '{
    	"user_id":"20130515094013",
    	"oid_partner":"201103171000000000",
    	"pay_type":"F",
    	"api_verion":"2.1",
    	"oid_paybill":"2013051416009982",
    	"no_order ":"2013051500001",
    	"dt_order ":"20141231010101",
    	"money_order":"1000",
    	"sign_type ":"RSA",
    	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
    }'
```

***

## Response

###### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|ret_code|Required|String(4)|Return code, whether the request is handled successfully or not. Refer to [return codes](return_code.md)|
|ret_msg|Required|String(255)|Return message, description of ```ret_code```, in Chinese|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|user_id|Required|String(32)|The unique identification assigned to the user in the merchant’s system|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|no_order|Optional|String(32)|Merchant order No.|
|dt_order|Optional|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Optional|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098|
|money_order|Optional|String(12)|The authorized amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|settle_date|Optional|String(8)| Format YYYYMMDD. Returns when payment is successful|
|info_order|Optional|String(255)| Returns when ```info_order``` is sent in API requests|

###### Sample Response

```json
{
	"ret_code":"0000",
	"ret_msg":"交易成功",
	"oid_partner":"201103171000000000",
	"oid_paybill":"2013051416009982",
	"no_order ":"2013051500001",
	"dt_order ":"20141231010101",
	"settle_date ":"20141231",
	"user_id":"20130515094013",
	"info_order ":"some info",
	"sign_type":"RSA", 
	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```
