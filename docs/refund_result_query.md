# Refund Status API

## Request

###### Endpoint

```html
https://queryapi.lianlianpay.com/refundquery.htm
```

###### Request Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_refund|Optional|String(32)|Refund No. in your system. Either ```no_refund``` or ```oid_refundno``` is required|
|dt_refund|Required|String(14)|Refund date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_refundno|Optional|String(16)| Unique refund transaction No. in LianLian system. Either ```no_refund``` or ```oid_refundno``` is required|

###### Sample Request

```html
curl https://queryapi.lianlianpay.com/refundquery.htm \
-H "Content-type:application/json;charset=utf-8" \
-d '{
        "oid_partner":"201103171000000000",
        "dt_refund":"20130515094018",
        "no_refund":"2013051500005",
        "oid_refundno":"2013051613121201",
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
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|no_refund|Optional|String(32)|Refund No. in your system. It is recommended to set a different value from ```no_order```|
|dt_refund|Optional|String(14)|Refund date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|money_refund|Optional|String(12)|Refund amount. Refund amount should be less than or equal to the amount of original ```no_order```, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|oid_refundno|Optional|String(16)| Unique refund transaction No. in LianLian system |
|sta_refund|Optional|String(1) | 0, refund initialized <br> 1, refund processing <br> 2, refund success <br> 3, refund failed |
|settle_date|Optional|String(8) | Format YYYYMMDD. Returns when refund is successful |

###### Sample Response

```json
{
    "ret_code":"0000",
    "ret_msg":"交易成功",
    "oid_partner":"201103171000000000",
    "no_refund":"2013051500001",
    "dt_refund":"20130515094018",
    "oid_refundno":"2013051613121201",
    "money_refund":"200.01",
    "sta_refund":"2",
    "settle_date":"20130627",
    "sign_type":"RSA", 
    "sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```