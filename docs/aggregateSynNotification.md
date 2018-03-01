# Aggregate Payment Synchronous Notification

Payment synchronous notification, a HTTP POST request, will be sent to ```url_return``` whenever the payment is confirmed as successful. 

> Synchronous notification sends only once, we recommend you to use [asynchronous notification](/docs/aggregateAsynNotification.html) or [order status query API](/docs/orderStatusQuery.html) to obtain payment result.

###### Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. e.g. 201304121000001004|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, e.g. 20170801225714|
|oid_paybill|Required|String(18)|Unique transaction No. in LianLian system. e.g. 2011030900001098|
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|result_pay|Required|String| Payment result. e.g. SUCCESS|
|settle_date|Optional|String(8)| Format YYYYMMDD. Returns when payment is successful|
|info_order|Optional|String(255)| Returns when ```info_order``` is sent in API requests|
|pay_type|Optional|String| The payment method used in this transaction. <br> 0, balance payment <br> 1, online banking payment (debit card) <br> 8, online banking payment (credit card) <br> 9, business online banking payment <br> 2, express payment (debit card) <br> 3, express payment (credit card)<br> D, verified payment <br> I, WeChat Payment <br> L, Alipay Payment| 
|bank_code|Optional|String| Returns only for express payments and verified payment.|

There is no need to send response for synchronous notification.