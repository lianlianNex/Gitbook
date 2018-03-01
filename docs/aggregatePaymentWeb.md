# Aggregate Payment API

This document is targeted to people who are capable of web development and understand server development, as well as relevant project management personnel.

***

## Specification 

* **Unique order number**: the merchant orders system uses the unique order number identification in the payment platform of LianlianPay. In principle, merchant order number is the unique identification for the appropriate order, which is independent of the date. 
* **Duplicate order protection**: each order shall be assigned a unique order number during a merchant’s business day. In the platform system of LianlianPay, elements such as merchant number, merchant order date, and merchant order number and transaction amount constitute a unique order.
* **Payment result query**: if an order is identified with the unique order number in the merchant orders system, then merchant could inquire about the status of this order only with merchant number + unique order number. If an order is identified with date + order number in the merchant order system (the same order number may be assigned in different date), then the merchant could inquire about the status of this order with merchant number + merchant order time+ merchant order number.
* **Payment retry**: Lianlian payment platform accepts repeated orders placed by the merchant (i.e. merchant order date and order number remain unchanged). If payment for the merchant order is unsuccessful in the platform of LianlianPay, then the merchant can make payment for the order again, provided that the merchant number, merchant order date and order number provided by the merchant to the platform shall remain unchanged; if the payment for this order has been successful, then payment retry for this order will be refused.
* **Date**: In consideration of minor time difference between the merchant order system server and the LianlianPay payment platform server, as well as the timezone differences, difference of one (1) day between the merchant order date and LianlianPay payment platform date is acceptable. However, all clearing and reconciliation data given to the merchant shall be subject to the clearing date of the platform.


***

## API Description

###### Endpoint

```html
https://wallet.lianlianpay.com/aggregateweb/gateway.htm
```

The way to call this API is limited to HTML ```<form/>``` post request from client-side. Below ```<meta>```  is needed in the head of your HTML.
 
```html
<meta http-equiv="content-type" content="text/html;charset=UTF-8">
```

###### Request Parameters

|Name|Required|Type|Description|
|---|---|---|---|
|version|Required|String|Fixed value, ```1.1```|
|oid_partner|Required|String(18)|The unique identification assigned to the merchant. e.g. 201304121000001004|
|user_id|Required|String(32)|The unique identification assigned to the user in the merchant’s system|
|timestamp|Required|String(14)|The time when request is initialized. Format: YYYYMMDDHHMMSS, e.g. 20170801225714|
|sign_type|Required|String(3)|RSA |
|sign|Required|String|Signature value|
|busi_partner|Required|String(6)|Fixed value. Virtual products, ```101001```; Physical products, ```109001```|
|no_order|Required|String(32)|Merchant order No.|
|dt_order|Required|String(14)|Merchant order date. Format: YYYYMMDDHHMMSS, e.g. 20170801225714|
|name_goods|Required|String(40)|Product name. e.g. Pen|
|info_order|Optional|String(255)|```info_order``` will be sent back in synchronous or asynchronous notification for parameters transmission|
|money_order|Required|String(12)|Merchant order amount, range: 0.01 ~ 100,000,000.00, 2 decimal places are expected, in CNY|
|notify_url|Required|String(128)|Online url where asynchronous notification should be sent, e.g. http://www.lianlianpay.com/help/notify|
|url_return|Optional|String(128)|Online url, your customer will be redirected to ```url_return``` once they finished their payment|
|userreq_ip|Required|String(32)|The IP address of your customer, used for anti-fraud purpose. Replace "." with "_", e.g. 122_11_37_211|
|url_order|Optional|String(255)|Online url of products|
|valid_order|Optional|Int|The valid period of ```no_order```, in minute. The status of corresponding transaction will be set to "Closed" once its ```valid_order``` run out. Default: 10080 (7 days). |
|risk_item|Required|String| This parameter is used for payment risk control, all required parameters should be included in the value of ```risk_item``` in json format| 
|col_oidpartner|Optional|String(18)| ```oid_partner``` of recipient, which is mainly used in LianLian E-wallet. The value is set as ```oid_partner``` to which ```user_id``` belongs by default. |
|col_userid|Optional|String(32)| ```user_id``` of recipient, which is mainly used in LianLian E-wallet. Note there is only one recipient, ```col_userid``` and ```col_oidparnter``` can not be used in a same request |
|shareing_data|Optional|String(1024)| Refer to [Sharing data instruction](#sharing-data-instruction) |
|secured_partner|Optional|String(18)|```oid_partner``` of guarantor, which is mainly used in guaranteed transactions. Refer to LianLian E-wallet documentation for more details|
|buyer_confirm_valid|Optional|Int| |
|seller_send_valid|Optional|Int| |
|id_no|Optional|String| Only ID card is supported, the length need to be either 15 or 18. Required for Verified Payment|
|acct_name|Optional|String|The name of payer, in Chinese. Required for Verified Payment |
|bank_code|Optional|String|Specify which online banking should be used instead of displaying online banking selection page. ```bank_code``` to be used with ```pay_type```. |
|pay_type|Optional|String| 1, online banking payment(debit card) <br> 8, online banking payment(credit card) <br> 9, business online banking payment <br> ```pay_type``` to be used with ```bank_code```.|

###### Sample Request

```html
<form action="ENDPOINT" method="post"> 
    <input type="text" name="version" value="1.0">
    <input type="text" name="oid_partner" value="201304121000001004">
    <input type="text" name="user_id" value="111111">
    <input type="text" name="busi_partner" value="101001">
    <input type="text" name="no_order" value="2013099129111111">
    <input type="text" name="dt_order" value="20130224120224">
    <input type="text" name="name_goods" value="test item">
    <input type="text" name="info_order" value="some info">
    <input type="text" name="money_order" value="49.95">
    <input type="text" name="notify_url" value="http://domain:port/notify">
    <input type="text" name="url_return" value="http://domain:port/return">
    <input type="text" name="userreq_ip" value="*_*_*_*">
    <input type="text" name="risk_item" value='{"user_info_bind_phone":"13958069593","user_info_dt_register":"20131030122130","frms_ware_category":"1009","request_imei":211,"request_imsi":121121,"request_ip":"192.168.20.110"}'>
    <input type="text" name="url_order" value="http://domain:port/orderUrl">
    <input type="text" name="sign_type" value="RSA">
    <input type="text" name="sign" value="YOUR-RSA-SIGN-RESULT">
    <input type="submit" value="checkout">
</form>
```

###### Sharing Data Introduction

Parameter ```shareing_data``` is mainly used for revenue sharing. Max recipients: 3. 

```html
Sharing_account^Sharing_account_type^Sharing_amount^Sharing_description|Sharing_account^Sharing_account_type^Sharing_amount^Sharing_description|Sharing_account^Sharing_account_type^Sharing_amount^Sharing_description
```
* ```Sharing_account```, can either be ```user_id``` or ```oid_partner``` .
* ```Sharing_account_type```, fixed value. 0 for LianLian E-wallet merchant, 1 for regular merchant.
* ```Sharing_amount```, revenue sharing amount, 2 decimal places are expected, in CNY.
* ```Sharing_description```, a short description for revenue sharing, no "^" nor "|", length: 85.