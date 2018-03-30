# Aggregate Payment

Aggregate Payment allows you to accept payments with a single integration for below payment methods:

* **Card payment**. Users provide their key payment information such as card number, phone number, ID card number, real name etc to get verified and complete payments.
    > Note: No authorization nor capture function for credit card is supported, if you are looking for relevant functions, go to [Easy Payment](easypay.md) instead.
* **Online banking payment**. Users are redirected from your sites to pages hosted by selected banks, proceed payments and then return to your sites. 
* **Alipay**. Users scan QR code which is displayed in pages hosted by LianLian after being redirected from your sites.
* **WechatPay**. Similar to Alipay.
* **Balance payment**. This payment methods is for E-wallet merchants only. For the documents of E-wallet, please contact our support.

All above payment methods are available by redirecting your users to pages hosted by LianLian via [aggregate payment redirect API](aggregate_redirect.md). On the other hand, [aggregate payment direct API](aggregate_direct.md) is available for WechatPay and Alipay.
