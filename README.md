# LianLianPay Documentation

Welcome to LianLian.

Get started with following APIs:

* [Easy Payment](docs/easypay.md). Unified bank card payment solution including:
    * Debit card payments.
    * Credit card payments, authorization and capture functions are supported.

* [Aggregate Payment](docs/aggregate_pay.md). Redirect your users to pages hosted by LianLian and proceed payments with multiple methods.

***

## Terminologies

|Terminology|Interpretation |
|:---|:---|
|Binding card|Binding card is an operation to generate a special parameter ```no_agree``` which is used to take place of card information, thus you can use ```no_agree``` for further charge requests without card information  |
|Request and Response| The request and response in this documentation refer to HTTP terminologies [request](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_message) and [response](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Response_message) |
|Notification| A request sent from LianLianPay, Inc to merchants which represents the results of corresponding operation, it can be either synchronous or asynchronous|
|Query| A request sent from merchants' server which queries the results of payment or refund|
|Signature| A digital signature which used for authentic between merchants and LianLianPay, Inc. |

## Technical Support

If you have any questions about development or use of LianlianPay payment API, please contact the relevant technical staff of LianlianPay by e-mail or mobile phone.

|Name|Mobile Phone|Email|
|:---|:---|:---|
|Su Liang|+86 15057168900|suliang@yintong.com.cn|
|Peng LiJuan|+86 18867518002|penglj@yintong.com.cn|
|Tech Supports Group| N/A| tech_support@yintong.com.cn|

