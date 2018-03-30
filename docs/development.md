# Development 

This document is targeted to people who are capable of web development and understand server development, as well as relevant project management personnel.

***

## Specification 

* **Unique order number**: the merchant orders system uses the unique order number identification in the payment platform of LianlianPay. In principle, merchant order number is the unique identification for the appropriate order, which is independent of the date. 
* **Duplicate order protection**: each order shall be assigned a unique order number during a merchant’s business day. In the platform system of LianlianPay, elements such as merchant number, merchant order date, and merchant order number and transaction amount constitute a unique order.
* **Payment result query**: if an order is identified with the unique order number in the merchant orders system, then merchant could inquire about the status of this order only with merchant number + unique order number. If an order is identified with date + order number in the merchant order system (the same order number may be assigned in different date), then the merchant could inquire about the status of this order with merchant number + merchant order time+ merchant order number.
* **Payment retry**: Lianlian payment platform accepts repeated orders placed by the merchant (i.e. merchant order date and order number remain unchanged). If payment for the merchant order is unsuccessful in the platform of LianlianPay, then the merchant can make payment for the order again, provided that the merchant number, merchant order date and order number provided by the merchant to the platform shall remain unchanged; if the payment for this order has been successful, then payment retry for this order will be refused.
* **Date**: In consideration of minor time difference between the merchant order system server and the LianlianPay payment platform server, as well as the timezone differences, difference of one (1) day between the merchant order date and LianlianPay payment platform date is acceptable. However, all clearing and reconciliation data given to the merchant shall be subject to the clearing date of the platform.

###### Security requirements

|Requirements|Description|
|:---|:---|
|Protocol|HTTPS|
|Request submission|For front-end payment integration, ```<Form/>``` or mobile SDKs <br> For back-end payment integration, request method: POST |
|Format|[JSON](http://json.org/)|
|Charset|utf-8|


***

## Integration Type

###### Redirect API

The payment process are handled in pages hosted by LianLianPay, Inc. Implementation is limited to client-side by using redirect APIs.

Steps:

1. Prepare request information in your applications.
2. Submit the payment form and then redirect users to LianLian payment pages.
3. Your users complete payments externally of your application and can be redirected back.

###### Direct API

Payment information are collected by your servers and communicated to LianLian servers directly to proceed payments.

Steps:

1. Prepare request information in your application and send it to LianLian servers via provided APIs.
2. LianLian handle the payment requests internally.
3. LianLian respond the payment requests with the results.

###### File transmission

Mainly used in report services via Sftp.