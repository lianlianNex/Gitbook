# Aggregate Payment Asynchronous Notification

Once a payment request is processed, LianLian will send the results to the notification URL ```notify_url``` via server-side HTTP requests, which is wrote into *HttpInputStream*. 

> Your servers are informed of the successful result only. No notification will be sent for unsuccessful or abnormal transactions. 

***

## Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|oid_paybill|Required|String(18)|Unique transaction No. in LianLian system. E.g. 2011030900001098|
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|result_pay|Required|String| Payment result. E.g. SUCCESS|
|settle_date|Optional|String(8)| Format YYYYMMDD. Returns when payment is successful|
|info_order|Optional|String(255)| Returns when ```info_order``` is sent in API requests|
|pay_type|Optional|String| The payment method used in this transaction. <br> 0, balance payment <br> 1, online banking payment (debit card) <br> 8, online banking payment (credit card) <br> 9, business online banking payment <br> 2, express payment (debit card) <br> 3, express payment (credit card)<br> D, verified payment <br> I, WeChat Payment <br> L, Alipay Payment| 
|bank_code|Optional|String| Short codes of banks |
|no_agree|Optional|String| Permanent token. Returns for express payment and verified payment. |

###### Sample asynchronous notification

```json
{
    "oid_partner":"201103171000000000",
    "dt_order":"20130515094013",
    "no_order":"2013051500001",
    "oid_paybill":"2013051613121201",
    "money_order":"210.97",
    "result_pay":"SUCCESS",
    "settle_date":"20130516",
    "info_order":"用户13958069593购买了3桶羽毛球",
    "pay_type":"2",
    "bank_code":"01020000",
    "sign_type":"RSA", 
    "sign":"ZPZULntRpJwFmGNIVKwjLEF2Tze7bqs60rxQ22CqT5J1UlvGo575QK9z/+p+7E9cOoRoWzqR6xHZ6WVv3dloyGKDR0btvrdqPgUAoeaX/YOWzTh00vwcQ+HBtXE+vPTfAqjCTxiiSJEOY7ATCF1q7iP3sfQxhS0nDUug1LP3OLk="
}
```

***

## Specification

###### Obtain request message

You can choose one way to obtain parameters depending on your programming language:

* PHP: ```file_get_contents("php://input");```
* Java: ```request.getInputStream();```
* C#: ```Request.inputStream;```

###### Requirement for ```notify_url```

```notify_url``` must be an online url which is accessible for our server ip addresses of asynchronous notification:

```html
218.4.207.154–218.4.207.158
112.80.55.210–112.80.55.214
223.112.79.242–223.112.79.246
115.238.110.126, 115.236.98.22, 211.140.27.205
```

> It is recommended to load your ```notify_url``` via HTTPS.

###### Successful payment

A successful payment always has below attributes:

* Signature verified successfully. The signature in asynchronous notification are encrypted by the ```private key``` from LianLianPay, Inc., you need to use the corresponding ```public key``` to proceed with signature verification.

* ```result_pay=SUCCESS```.

###### Handle asynchronous notification

LianLian expects you to respond asynchronous notification with below json object which means you have received our notification and proceeded with delivery logic:

```json
{
    "ret_code":"0000",
    "ret_msg":"ok"
}
```

###### Asynchronous notification repeat

Assuming there is no issues from internet layer, if we haven't received your response within 5 seconds or the response does NOT match our expectation, asynchronous notification mechanism would mark the result as FAILURE and send it again. 

Resending logic: 30 times in total with an interval of 2 minutes, until your server has correctly handled the notification. But if we never got the expected response after 30 times, the resending action would be stopped. In this case,  you will have to query [paymnet status query API](/docs/paymentStatusQuery.html) by yourself. 

However, there are few cases like internet traffic jam, network delay, packet loss or other causes which results in an unexpected phenomenon, that your server has received 2 same asynchronous notification for a same transaction. In case of it, you **MUST** have the capability to handle duplicated asynchronous notifications, respond them with the expected response of LianLian but proceed your successful logic only **ONCE**. The financial risks which caused by repeated asynchronous notification borne by yourselves.


          