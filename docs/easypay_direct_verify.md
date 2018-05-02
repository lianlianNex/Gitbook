# Easy Payment Direct Verify API

###### Endpoint

```html
https://traderapi.lianlianpay.com/easypayverify.htm
```

> Direct APIs have an additional requirement which involves our payment risk team and due diligence team. You need to contact your business development to obtain the access.

###### Request Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|token|Required|String|The token which is returned in [Easy Payment Direct Apply API](easypay_direct_apply.md)|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_order|Required|String(32)|Merchant order No.|
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|verify_code|Required|String| The SMS code sent to end user|
 
###### Sample Request

```curl
curl https://traderapi.lianlianpay.com/easypayverify.htm \
-H "Content-type:application/json;charset=utf-8" \
-d '{
    	"oid_partner":"201103171000000000",
    	"token":"D096DBA0E3E0CC8F1D504C06E71D292D",
    	"no_order":"2013051500001",
    	"oid_paybill":"2013051613121201",
    	"money_order":"210.97",
    	"verify_code":"666666",
    	"sign_type ":"RSA",
    	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
    }'
```

***

## Response

###### Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|ret_code|Required|String(4)|Return code, whether the request is handled successfully or not. Refer to [return codes](return_code.md)|
|ret_msg|Required|String(100)|Return message, description of ```ret_code```, in Chinese |
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Optional|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098 <br> Return when ```ret_code=8888``` or ```ret_code=0000``` |
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|result_pay|Optional|String| Payment result. <br> SUCCESS - Payment proceed successfully <br> PROCESSING -  Payment is processing <br> APPLY_SUCCESS - Authorization applied successfully|
|settle_date|Optional|String(8)| Format YYYYMMDD. Return when ```result_pay=SUCCESS```|
|info_order|Optional|String(255)| Returns when ```info_order``` is sent in API requests|
|bank_code|Optional|String| Short codes of banks. Return when ```ret_code=0000``` |
|no_agree|Optional|String(16)| Return when ```result_pay=SUCCESS```|
|pay_type|Required|String| The payment method used in this transaction. <br> M, Easy payment - Debit card <br> N, Easy payment - Credit card <br> F, Authorization | 
|bank_code|Optional|String| Short codes of banks |

###### Sample Response

```json
{
	"ret_code":"0000",
	"ret_msg":"交易成功",
	"oid_partner":"201103171000000000",
	"dt_order":"20130515094013",
	"no_order":"2013051500001",
	"oid_paybill":"2013051613121201",
	"money_order":"210.97",
	"result_pay":"SUCCESS",
	"settle_date":"20150805",
	"info_order":"用户13958069593购买了3桶羽毛球",
	"no_agree":"2014101516553011",
	"pay_type":"M",
	"sign_type":"RSA", 
	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```