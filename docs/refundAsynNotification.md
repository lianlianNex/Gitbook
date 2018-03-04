# Refund Asynchronous Notification

Once a refund request is processed, LianLian will send the results to the notification URL ```notify_url``` via server-side HTTP requests, which is wrote into *HttpInputStream*. You can choose one way to obtain parameters depending on your programming language:

* PHP: ```file_get_contents("php://input");```
* Java: ```request.getInputStream();```
* C#: ```Request.inputStream;```

Refund Asynchronous Notification is sent out whenever the status of refund is confirmed as SUCCESS or FAILURE.

###### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. E.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_refund|Optional|String(32)|Refund No. in your system. It is recommended to set a different value from ```no_order```|
|dt_refund|Optional|String(14)|Refund date. Format: YYYYMMDDHHMMSS, E.g. 20170801225714|
|money_refund|Optional|String(12)|Refund amount. Refund amount should be less than or equal to the amount of original ```no_order```, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|oid_refundno|Optional|String(16)| Unique refund transaction No. in LianLian system |
|sta_refund|Optional|String(1) | 0, refund initialized <br> 1, refund processing <br> 2, refund success <br> 3, refund failed |
|settle_date|Optional|String(8) | Format YYYYMMDD. Returns when refund is successful |

###### Sample refund asynchronous notification

```json
{
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


***

## Handle asynchronous notification

LianLian expects you to respond asynchronous notification with below json object which means you have received our notification and proceeded with delivery logic:

```json
{
    "ret_code":"0000",
    "ret_msg":"ok"
}
```

If we haven't received your response within 5 seconds or the response does NOT match our expectation, asynchronous notification mechanism would mark the result as FAILURE and send it again. 
 
Resending logic: 30 times in total with an interval of 2 minutes, until your server has correctly handled the notification. 

But if we never got the expected response after 30 times, the resending action would be stopped. In this case,  you will have to query [refund status query API](//refundStatusQuery.html) by yourself. 