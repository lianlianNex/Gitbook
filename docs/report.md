# Report

Transaction reports are generated automatically by ```settle_date``` which is returned in [payment asynchronous notification](asyn_notification.md) for successful payments.

LianLian provides 2 ways for you to obtain reports:

* Download it from [merchant dashboard](https://b.lianlianpay.com/trader/login.htm).

* Download it from Sftp servers. In order to obtain Sftp access, you need to contact [tech_support@yintong.com.cn](mailto:tech_support@yintong.com.cn).

***

## Sftp Reports

###### Daily report file format

Daily report is generated and uploaded to Sftp servers at 9:00 am (UTC +8) every day. 

**File name format**: Its name consists of prefix, your ```oid_parnter``` and ```settle_date``` of the payment. E.g. JYMX_201301221000001001_20130313.txt.

**File content format**: Only successful or refunded payment are shown in daily reports, failed payments won't be reflected in it. Besides, all transaction details including merchant's settlement and withdraw are recorded in daily reports.

```html
{no_order||no_refund}, {oid_partner}, {dt_order||dt_refund(Format: yyyymmdd hh:mm:ss)}, {busi_partner}, {oid_paybill(Returns no_order when refund)}, {settle_date}, {money_order(2 decimal places)}, {flag_receive_money(0 means receive money, 1 means send money)}, {payment_status(0 means success, 5 means refunded)}, {dt_update(Format: yyyymmdd hh:mm:ss)}, {fee(2 decimal places, in CNY)},{payment_products(WEB支付网关(WEB payment)|手机应用支付网关(mobile payment gateway)|API渠道(API gateway)|WAP支付网关(WAP payment)|IVR支付网关(IVR payment))}, {payment_method(余额支付(Balance payment)|储蓄卡网银支付(Online banking debit card payment)|信用卡网银支付(Online banking credit card payment)|储蓄卡快捷支付(Express debit card payment)|信用卡快捷支付(Express credit card payment)|线下网点支付(Offline payment)|充值卡支付(Prepaid card payment)|企业网银支付(Online banking B2B)}, {info_order}
```

E.g.

```html
201405287094797,201403251000001147,20140528 16:35:56,101001,2014052846671792,20140528,100,0,0, 20140528 16:35:56,0.5,手机应用支付网关,储蓄卡快捷支付,彩票连连支付充值
201405287094244,201403251000001147,20140528 16:32:53,101001,2014052846671022,20140528,15,0,0, ,20140528 16:32:53,0.1,手机应用支付网关,信用卡快捷支付,彩票连连支付充值
201405287094894,201403251000001147,20140528 16:36:35,101001,2014052846671934,20140528,100,0,0, 20140528 16:36:35,0.5,手机应用支付网关,储蓄卡快捷支付,彩票连连支付充值
```

Daily reports contain all of your business transaction records, you can use ```busi_partner``` as a filter if needed. 

An order which is refunded has 2 records in reports, one with positive ```money_order``` + ```fee``` and another one with negative ```money_order``` + ```fee```. The ```oid_paybill``` of the refund records is the original ```no_order```, and its ```payment_status``` is set to 5.

***

###### Monthly report file format

Monthly report will be available by 9:00 am (UTC +8) on the 1st of next month.

**File name format**: Its name consists of prefix, your ```oid_parnter``` and current month. E.g. JYMX_201301221000001001_201304.txt.

**File content format**: The content format is same with [daily report file format](#daily-report-file-format) but with longer time range.

***

###### Daily summary report file format

Summary report is generated everyday which records an overview of your daily revenue.

**File name format**: Its name consists of prefix, your ```oid_parnter``` and ```settle_date``` of the payment. E.g. JYMXSUM_201301221000001001_20130313.txt.

**File content format**:

```html
{total_transaction_count}, {successful_transaction_count}, {successful_transaction_amount_summary(2 decimal places, in CNY)}, {refunded_transaction_count}, {refunded_transaction_amount_summary(2 decimal places, in CNY, negative value), {canceled_transaction_count}, {canceled_transaction_amount_summary(2 decimal places, in CNY, negative value)}
```

E.g.

```html
8|8|551.23|0||0|
```