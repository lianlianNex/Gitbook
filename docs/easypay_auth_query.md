# Authorization Query API

## Request

###### Endpoint

```html
https://queryapi.lianlianpay.com/preauthquery.htm
```

###### Request Parameter

|Name|Required|Type|Description|
|---|---|---|---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|platform|Optional|String(32)| ```platform``` is used for sharing user info between multiple ```oid_partner```, this requires additional settings from LianLian side|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|pay_type|Required|String| F, authorization payment for credit card <br> G, authorization payment for debit card |
|api_version|Required|String|Fixed value, ```1.0```|
|no_order|Required|String(32)|Merchant order No. Optional if ```oid_paybill``` is present |
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Required|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098. Optional if ```no_order``` is present |

###### Sample Request

```curl
curl https://queryapi.lianlianpay.com/preauthquery.htm \
-H "Content-type:application/json;charset=utf-8" \
-d '{
    	"user_id":"20130515094013",
    	"oid_partner":"201103171000000000",
    	"pay_type":"F",
    	"api_verion":"2.1",
    	"no_order":"2013051500001",
    	"dt_order":"2013051500001",
    	"sign_type ":"RSA",
    	"sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
    }'
```

***

## Response

###### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|ret_code|Required|String(4)|2003, transaction created <br> 2006, transaction expired <br> PR07, apply authorization successfully <br> PR08, applying authorization needs verification <br> PR09, apply authorization is processing <br> PR10, apply authorization failed <br> PR11, capture authorization successfully <br> PR12, capture authorization is processing <br> PR13, capture authorization failed <br> PR14, void authorization successfully  <br> PR15, void authorization is processing <br> PR16, void authorization failed <br> For others, refer to [return codes](return_code.md)|
|ret_msg|Required|String(255)|Return message, description of ```ret_code```, in Chinese|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|no_order|Optional|String(32)|Merchant order No.|
|dt_order|Optional|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Optional|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098|
|money_order|Optional|String(12)|The authorized amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|

###### Sample Response

```json
{
  "ret_code": "0000",
  "ret_msg": "交易成功",
  "oid_partner": "201103171000000000",
  "oid_paybill": "2013051416009982",
  "no_order": "2013051500001",
  "dt_order": "20141231010101",
  "money_order": "210.97",
  "user_id": "20130515094013",
  "sign_type": "RSA",
  "sign": "ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```
