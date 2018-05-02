# Easy Payment Direct Apply API

###### Endpoint

```html
https://traderapi.lianlianpay.com/easypay.htm
```

> Direct APIs have an additional requirement which involves our payment risk team and due diligence team. You need to contact your business development to obtain the access.

###### Request Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|api_version|Required|String(6)|Fixed value, ```1.0```|
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
|pay_type|Required|String| M, Easy payment - Debit card <br> N, Easy payment - Credit card <br> F, authorization, used for credit card only. An error throws out if the used card is not a credit card|
|risk_item|Required|String| This parameter is used for payment risk control, all required parameters should be included in the value of ```risk_item``` in json format, refer to [Payment Risk](payment_risk_item.md)| 
|bank_code|Optional|String| The code of bank. E.g. ```01040000```|
|client_chnl|Optional|String|```10``` - APP <br> ```13``` - PC <br> ```16``` - H5 <br> ```18``` - IVR <br> ```NA``` - N/A| 
|no_agree|Optional|String(32)| A token which represents the key payment information, refer to [Binding Card](easypay.md) for more details|
|id_type|Optional|String(1)| 0, ID card <br> 2, Passport <br> 3, Military Officer Certificate <br> 4, Hong Kong-Macau laissez-passer <br> 6, Mainland travel permit for Taiwan residents <br> 9, Police Officer card <br> X, other certificates |
|id_no|Optional|String| The number of User's ID card. The length need to be either 15 or 18|
|acct_name|Required|String|The name of payer, in Chinese|
|card_no|Required|String|User's card number|
|bind_mob|Required|String| User's phone number |
|vali_date|Optional|String| The expire date of credit card. Required for credit card|
|cvv2|Optional|String|The CVV/CVC2 of credit card. Required for credit card|

> ```id_no```, ```acct_name```, ```id_type```, ```card_no``` are ignored if ```no_agree``` is present.

###### Sample Request

```curl
curl https://traderapi.lianlianpay.com/easypay.htm \
-H "Content-type:application/json;charset=utf-8" \
-d '{
      "api_version": "1.0",
      "acct_name": "测试用户",
      "bank_code": "01020000",
      "bind_mob": "18667140528",
      "busi_partner": "101001",
      "card_no": "6222081202008631100",
      "client_chnl": "18",
      "cvv2": "211",
      "dt_order": "20150805172633",
      "id_no": "339005198901194918",
      "id_type": "0",
      "info_order": "商品名称",
      "money_order": "10",
      "name_goods": "表",
      "no_order": "20150805172633650",
      "notify_url": "http://payhttp.xiaofubao.com/***/back.shtml",
      "oid_partner": "201310102000003524",
      "pay_type": "M",
      "risk_item": "{\"frms_client_chnl\":\"13\",\"frms_is_real_name\":\"1\",\"type_pay\":\"2\"}",
      "sign": "eeWrsPdqpy8nmCmUgnwbJ9y7XB+Z9HkCsBJMOz6Y+5Lh9ydA+CEswYY3mkit3xZ1Y8qk+xJlJ0dQqziojNK7rUqC9MbTdO0fvO8NKhpW1/9GwrkxOPrFd+b1WBVIwyPYBcL+R7FA87xZPWuPjCpeRpQH0voLv0EMDKmzVKCpNzk=",
      "sign_type": "RSA",
      "user_id": "201310102000003524",
      "vali_date": "2016",
      "valid_order": "10080"
    }'
```

***

## Response

###### Parameters

|Name|Required|Type|Description|
|:---|:---|:---|:---|
|ret_code|Required|String(4)|Return code, whether the request is handled successfully or not. Refer to [return codes](return_code.md)|
|ret_msg|Required|String(100)|Return message, description of ```ret_code```, in Chinese |
|token|Optional|String| Return when ```ret_code=0000```|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Optional|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098 <br> Return when ```ret_code=8888``` or ```ret_code=0000``` |
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|sms_flag|Required|String(1)| If the SMS is sent. ```1``` - send SMS code <br> ```0``` - Do NOT send SMS code|
|result_pay|Optional|String| Payment result. <br> SUCCESS - Payment proceed successfully <br> PROCESSING -  Payment is processing <br> APPLY_SUCCESS - Authorization applied successfully|
|settle_date|Optional|String(8)| Format YYYYMMDD. Return when ```result_pay=SUCCESS```|
|info_order|Optional|String(255)| Returns when ```info_order``` is sent in API requests|
|bank_code|Optional|String| Short codes of banks. Return when ```ret_code=0000``` |
|no_agree|Optional|String(16)| Return when ```result_pay=SUCCESS```|

###### Sample Response

```json
{
    "ret_code":"0000",
    "ret_msg":"交易成功",
    "token":"D096DBA0E3E0CC8F1D504C06E71D292D",
    "oid_partner":"201103171000000000",
    "dt_order":"20130515094013",
    "no_order":"2013051500001",
    "oid_paybill":"2013051613121201",
    "sms_flag":"1",
    "result_pay":"PROCESSING",
    "money_order":"210.97",
    "sign_type":"RSA", 
    "sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```