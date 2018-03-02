# Return Codes

<table>
   <tr>
      <td>ret_code</td>
      <td>ret_msg</td>
      <td>description </td>
   </tr>
   <tr>
      <td>0000</td>
      <td>交易成功</td>
      <td>Trade successfully</td>
   </tr>
   <tr>
      <td>0106</td>
      <td>签约银行卡信息查询失败</td>
      <td>Failed to query the signed bank card info</td>
   </tr>
   <tr>
      <td>1000</td>
      <td>支付授权令牌失效或错误</td>
      <td>It means that the token is invalid or wrong. The token will be invalid after half an hour. Preprocessed the payment to re-obtain the new token.</td>
   </tr>
   <tr>
      <td>1001</td>
      <td>商户请求签名错误</td>
      <td>Illegal signature</td>
   </tr>
   <tr>
      <td>1002</td>
      <td>第三方单号重复</td>
      <td>repeated order no</td>
   </tr>
   <tr>
      <td>1003</td>
      <td>正在支付中,请稍后</td>
      <td>Contact Customer Service</td>
   </tr>
   <tr>
      <td>1004</td>
      <td>商户请求参数校验错误（具体参数名）</td>
      <td>Incorrect parameter</td>
   </tr>
   <tr>
      <td>1005</td>
      <td>支付处理失败</td>
      <td>For a variety of reasons, the payment failed, including the failure of the user signing , the lack of the balance, the restrictions of the banks </td>
   </tr>
   <tr>
      <td>1006</td>
      <td>支付单创建失败</td>
      <td>Payment order creation failed </td>
   </tr>
   <tr>
      <td>1007</td>
      <td>网络链接繁忙</td>
      <td>busy network link</td>
   </tr>
   <tr>
      <td>1008</td>
      <td>商户请求IP错误</td>
      <td>Please whitelist your IP address.</td>
   </tr>
   <tr>
      <td>[1012]</td>
      <td>请求报文解析失败</td>
      <td>Failed to resolve the request message.</td>
   </tr>
   <tr>
      <td>1009</td>
      <td>暂停商户支付服务，请联系连连银通客服</td>
      <td>The merchant payment service was suspended for a variety of reasons </td>
   </tr>
   <tr>
      <td>1014</td>
      <td>日累计金额或笔数超限</td>
      <td>Exceed the cumulative amount or number of transactions limits</td>
   </tr>
   <tr>
      <td>1016</td>
      <td>交易金额超限</td>
      <td>The amount of the transaction is beyond the limit.</td>
   </tr>
   <tr>
      <td>1019</td>
      <td>单笔金额超限</td>
      <td>The amount of a single transaction is beyond the limit.</td>
   </tr>
   <tr>
      <td>1100</td>
      <td>无效卡号</td>
        <td>Invalid or unsupported card.</td>
   </tr>
   <tr>
      <td>1101</td>
      <td>卡已挂失</td>
      <td>A lost bank card.</td>
   </tr>
   <tr>
      <td>1102</td>
      <td>无此发卡方</td>
      <td>There's not this card issuer</td>
   </tr>
   <tr>
      <td>1103</td>
      <td>银行卡有效期或CVV2错误</td>
      <td>Bank card validity or CVV2 is wrong. </td>
   </tr>
   <tr>
      <td>1104</td>
      <td>卡密码错误</td>
      <td>Incorrect card password.</td>
   </tr>
   <tr>
      <td>1105</td>
      <td>卡号在黑名单中</td>
      <td>The card no is in the blacklist or the card has been restricted</td>
   </tr>
   <tr>
      <td>1106</td>
      <td>允许的输入PIN次数超限</td>
      <td>Too much times to input the incorrect password.</td>
   </tr>
   <tr>
      <td>1107</td>
      <td>您的银行卡暂不支持在线支付业务</td>
      <td>Your bank card does not support online payment services. </td>
   </tr>
   <tr>
      <td>1108</td>
      <td>您输入的证件号、姓名或手机号有误</td>
      <td>Incorrect ID no,name or phone no.</td>
   </tr>
   <tr>
      <td>1109</td>
      <td>卡号和证件号不符</td>
      <td>The card number is inconsistent with the ID no.</td>
   </tr>
   <tr>
      <td>1110</td>
      <td>卡状态异常</td>
      <td>Card status is abnormal </td>
   </tr>
   <tr>
      <td>1111</td>
      <td>交易异常，支付失败</td>
      <td>The transaction is abnormal and failed.</td>
   </tr>
   <tr>
      <td>1112</td>
      <td>证件号有误</td>
      <td>Incorrect ID no.</td>
   </tr>
   <tr>
      <td>1113</td>
      <td>持卡人姓名有误</td>
      <td>Card holder name is incorrect.</td>
   </tr>
   <tr>
      <td>1114</td>
      <td>手机号有误</td>
      <td>Incorrect phone no.</td>
   </tr>
   <tr>
      <td>1115</td>
      <td>该卡未预留手机号</td>
      <td>The user's card is not bound to any phone number. </td>
   </tr>
   <tr>
      <td>1200</td>
      <td>用户选择的银行暂不支持，请重新选择其他银行进行支付/签约</td>
      <td>unsupported bank</td>
   </tr>
   <tr>
      <td>1201</td>
      <td>银行卡变更失败</td>
      <td>Failed to change the bank.</td>
   </tr>
   <tr>
      <td>1202</td>
      <td>银行卡查询失败</td>
      <td>Faile to query the bank card.</td>
   </tr>
   <tr>
      <td>1805</td>
      <td>暂不支持该银行</td>
      <td>unsupported bank</td>
   </tr>
   <tr>
      <td>1900</td>
      <td>短信码校验错误</td>
      <td>Faild to verify the SMS identifying code </td>
   </tr>
   <tr>
      <td>1901</td>
      <td>短信码已失效</td>
      <td>Invalid SMS identifying code</td>
   </tr>
   <tr>
      <td>1902</td>
      <td>该卡交易金额超出免密限额</td>
      <td>Exceed the trade amount which require no password.</td>
   </tr>
   <tr>
      <td>2003</td>
      <td>支付单创建</td>
      <td>Payment order created.</td>
   </tr>
   <tr>
      <td>2004</td>
      <td>签约处理中</td>
      <td>The bank processing timeout or could not return final result synchronously.</td>
   </tr>
   <tr>
      <td>2005</td>
      <td>原交易已在进行处理，请勿重复提交</td>
      <td>Repeated request for a transaction.</td>
   </tr>
   <tr>
      <td>2006</td>
      <td>交易已过期</td>
      <td>exceed the order valid time</td>
   </tr>
   <tr>
      <td>2007</td>
      <td>交易已支付成功</td>
      <td>The original transaction has been paid successfully. </td>
   </tr>
   <tr>
      <td>2008</td>
      <td>交易处理中</td>
      <td>payment processing</td>
   </tr>
   <tr>
      <td>3001</td>
      <td>非法商户</td>
      <td>Invalid merchant account</td>
   </tr>
   <tr>
      <td>3002</td>
      <td>用户生成错误</td>
      <td>Failed to generate the user account. </td>
   </tr>
   <tr>
      <td>3003</td>
      <td>签约信息不存在</td>
      <td>Signing information does not exist </td>
   </tr>
   <tr>
      <td>3004</td>
      <td>用户解约失败</td>
      <td>Failed to cancel the user account</td>
   </tr>
   <tr>
      <td>3005</td>
      <td>查询跨度不得高于3个月</td>
      <td>Please query records within three months.</td>
   </tr>
   <tr>
      <td>3006</td>
      <td>用户不存在</td>
      <td>This user account does not exist.</td>
   </tr>
   <tr>
      <td>3007</td>
      <td>[user_id]查询不存在</td>
      <td>This userid does not exist.</td>
   </tr>
   <tr>
      <td>3008</td>
      <td>查询截止日期错误</td>
      <td>Incorrect expiration date.</td>
   </tr>
   <tr>
      <td>3009</td>
      <td>重复签约</td>
      <td>Repeated signing</td>
   </tr>
   <tr>
      <td>3010</td>
      <td>商户支付权限不足</td>
      <td>Service is not activated for this account</td>
   </tr>
   <tr>
      <td>3011</td>
      <td>用户签约信息不存在</td>
      <td>The user signing info does not exist.</td>
   </tr>
   <tr>
      <td>4000</td>
      <td>解约失败，请联系发卡行</td>
      <td>Failed to cancel agreement.Please contact the issuing bank.</td>
   </tr>
   <tr>
      <td>5001</td>
      <td>卡bin校验失败</td>
      <td>Failed to identify the BIN.</td>
   </tr>
   <tr>
      <td>5002</td>
      <td>原始交易不存在</td>
      <td>Trade does NOT exist.</td>
   </tr>
   <tr>
      <td>5003</td>
      <td>退款金额错误</td>
      <td>Refund amount is inconsistent with the original trade amount.</td>
   </tr>
   <tr>
      <td>5004</td>
      <td>商户状态异常，无法退款</td>
      <td>Merchant account status is abnormal so that refund cannnot be processed.</td>
   </tr>
   <tr>
      <td>5005</td>
      <td>退款失败，请重试</td>
      <td>Failed to refund.</td>
   </tr>
   <tr>
      <td>5006</td>
      <td>商户账户余额不足</td>
      <td>Insufficient account balance</td>
   </tr>
   <tr>
      <td>5007</td>
      <td>累计退款金额大于原交易金额</td>
      <td>Accumulated refund amount exceeds the original trade amount.</td>
   </tr>
   <tr>
      <td>5008</td>
      <td>原交易未成功</td>
      <td>The original trade was failed.</td>
   </tr>
   <tr>
      <td>5501</td>
      <td>大额行号查询失败</td>
      <td>Failed to query the prcptcd.</td>
   </tr>
   <tr>
      <td>5502</td>
      <td>信用卡不支持提现</td>
      <td>Credit card is unsupported to withdraw. </td>
   </tr>
   <tr>
      <td>5503</td>
      <td>商户提现权限不足</td>
      <td>This merchant account hasn't enough right to withdraw.</td>
   </tr>
   <tr>
      <td>5504</td>
      <td>商户操作权限不足</td>
      <td>Insufficient operating right.</td>
   </tr>
   <tr>
      <td>5505</td>
      <td>该银行未进行配置，请联系客服</td>
      <td>This bank hasn't been configured.Please contact the service.</td>
   </tr>
   <tr>
      <td>5506</td>
      <td>商户备注解析失败</td>
      <td>Failed to reslove the memo.</td>
   </tr>
   <tr>
      <td>5601</td>
      <td>支付方式和卡类型不匹配</td>
       <td>Card type and the payment method do not match .</td>
   </tr>
   <tr>
      <td>6001</td>
      <td>卡余额不足</td>
      <td>Insufficient fund in bank card.</td>
   </tr>
   <tr>
      <td>6002</td>
      <td>该卡号未成功进行首次验证</td>
      <td>First validation of this card no failed.</td>
   </tr>
   <tr>
      <td>6601</td>
      <td>获取银行请求地址失败，请稍后重试</td>
      <td>Obtain bank request url failed .Please try again.</td>
   </tr>
   <tr>
      <td>7001</td>
      <td>用户已存在</td>
      <td>This user is already exsited.</td>
   </tr>
   <tr>
      <td>7017</td>
      <td>金额不正确</td>
      <td>Invalid amount of money</td>
   </tr>
   <tr>
      <td>7018</td>
      <td>新增银行卡用户信息不一致</td>
      <td>The user info of the new added bank card is inconsistent. </td>
   </tr>
   <tr>
      <td>7119</td>
      <td>分账信息有误（分期付定期扣款）</td>
      <td>Incorrect shareing data.</td>
   </tr>
   <tr>
      <td>7777</td>
      <td>需要补全签约信息</td>
      <td>Need to complete contract information.</td>
   </tr>
   <tr>
      <td>8000</td>
      <td>用户信息不存在</td>
      <td>The user info doed not exist.</td>
   </tr>
   <tr>
      <td>8001</td>
      <td>文件异常</td>
      <td>Abnormal file</td>
   </tr>
   <tr>
      <td>8002</td>
      <td>生成文件异常</td>
      <td>Generate the file abnormally.</td>
   </tr>
   <tr>
      <td>8003</td>
      <td>解析文件异常</td>
      <td>An exception is thrown when parsing the file.  </td>
   </tr>
   <tr>
      <td>8006</td>
      <td>汇兑异常</td>
      <td>Exchange abnormally.</td>
   </tr>
   <tr>
      <td>8010</td>
      <td>付款人信息不存在</td>
      <td>The payer information does not exist. </td>
   </tr>
   <tr>
      <td>8099</td>
      <td>实名认证失败</td>
      <td>Authentication failed </td>
   </tr>
   <tr>
      <td>8101</td>
      <td>无此扣款计划信息</td>
      <td>No such repayment schedul existed.</td>
   </tr>
   <tr>
      <td>8102</td>
      <td>当前扣款计划已执行，请勿重复执行</td>
      <td>The deduction plan has been executed. Do not repeat it.</td>
   </tr>
   <tr>
      <td>8103</td>
      <td>还款计划通知短信发送失败</td>
      <td>Send notification of the repayment schedul message failed.</td>
   </tr>
   <tr>
      <td>8104</td>
      <td>扣款失败</td>
      <td>Failed to deduct money.</td>
   </tr>
   <tr>
      <td>8105</td>
      <td>变更还款次数超过限制</td>
      <td>The number to change repayment plan exceeds the limit. </td>
   </tr>
   <tr>
      <td>8106</td>
      <td>该签约协议号未授权该扣款协议号进行扣款</td>
      <td>The repayment plan has not been authorized by the agreement no. </td>
   </tr>
   <tr>
      <td>8107</td>
      <td>扣款计划校验失败</td>
      <td>Deduction plan verification failed.</td>
   </tr>
   <tr>
      <td>8108</td>
      <td>变更计划失败</td>
      <td>Failed to change the plan.</td>
   </tr>
   <tr>
      <td>8109</td>
      <td>计划保存失败</td>
      <td>Failed to save the plan.</td>
   </tr>
   <tr>
      <td>8110</td>
      <td>验证码错误</td>
      <td>Incorrect verification code.</td>
   </tr>
   <tr>
      <td>8111</td>
      <td>用户查询失败</td>
      <td>Failed to query the user account.</td>
   </tr>
   <tr>
      <td>8112</td>
      <td>变更计划状态失败</td>
      <td>Failed to change the repayment state. </td>
   </tr>
   <tr>
      <td>8113</td>
      <td>分期计划不存在</td>
      <td>Installment plan does NOT exsited.  </td>
   </tr>
   <tr>
      <td>8114</td>
      <td>扣款方式不符</td>
      <td>Incorrect pay type.</td>
   </tr>
   <tr>
      <td>8115</td>
      <td>还款卡授权失败</td>
      <td>The repayment card failed to authorize the repayment plan.</td>
   </tr>
   <tr>
      <td>8116</td>
      <td>定时任务执行失败</td>
      <td>The timing task execution failed.</td>
   </tr>
   <tr>
      <td>8117</td>
      <td>幂等检查异常</td>
      <td>Idempotent check abnormaly</td>
   </tr>
   <tr>
      <td>8888</td>
      <td>短信已下发，需要再次验证</td>
      <td>Need to do SMS validation again.</td>
   </tr>
   <tr>
      <td>8901</td>
      <td>没有记录</td>
      <td>None record is obtained according to the provided query conditions </td>
   </tr>
   <tr>
      <td>8911</td>
      <td>没有风控记录</td>
      <td>No record in risk contorl system.</td>
   </tr>
   <tr>
      <td>9000</td>
      <td>银行维护中，请稍后再试</td>
      <td>Bank is in maintenance, please try again later. </td>
   </tr>
   <tr>
      <td>9002</td>
      <td>报文解析异常</td>
      <td>An exception is thrown when parsing the message. </td>
   </tr>
   <tr>
      <td>9091</td>
      <td>创建支付失败</td>
        <td>Failed to create payment order.</td>
   </tr>
   <tr>
      <td>9092</td>
      <td>支付单号与订单号不一致</td>
      <td>oid_paybill is inconsistent with the no_order.</td>
   </tr>
   <tr>
      <td>9093</td>
      <td>无对应的支付单信息</td>
      <td>No corresponding payment information.</td>
   </tr>
   <tr>
      <td>9094</td>
      <td>请求银行扣款失败</td>
      <td>Failed to request the bank to deduct money. </td>
   </tr>
   <tr>
      <td>9104</td>
      <td>对公账户余额不足</td>
      <td>When calling the payment interface, the merchant account balance to pay the company account is insufficient.</td>
   </tr>
   <tr>
      <td>9700</td>
      <td>短信验证码错误</td>
      <td>Incorrect SMS verification code.</td>
   </tr>
   <tr>
      <td>9701</td>
      <td>短信验证码和手机不匹配</td>
      <td>SMS verification code and mobile phone numbers do not match.</td>
   </tr>
   <tr>
      <td>9702</td>
      <td>验证码错误次数超过最大次数,请重新获取进行验证</td>
      <td>Input incorrect verify code too much times.</td>
   </tr>
   <tr>
      <td>9703</td>
      <td>短信验证码失效,请重新获取</td>
      <td>Invalid SMS verify code.Please obtain it again.</td>
   </tr>
   <tr>
      <td>9704</td>
      <td>短信发送异常,请稍后重试</td>
      <td>Failed to send the SMS normally.Please try later.</td>
   </tr>
   <tr>
      <td>9990</td>
      <td>银行交易出错</td>
      <td>Please contact our customer service  to check this error.</td>
   </tr>
   <tr>
      <td>9901</td>
      <td>请求报文非法</td>
      <td>Invalid request message.</td>
   </tr>
   <tr>
      <td>9902</td>
      <td>接口调用异常</td>
      <td>An exception is thrown when the interface is invoked.</td>
   </tr>
   <tr>
      <td>9903</td>
      <td>ret_msg":"请求无效，请稍后重试</td>
      <td>Please contact our customer service  to check this error.</td>
   </tr>
   <tr>
      <td>9907</td>
      <td>银行编码与卡不一致</td>
      <td>The bank code is inconsistent with the card.</td>
   </tr>
   <tr>
      <td>9904</td>
      <td></td>
      <td></td>
   </tr>
   <tr>
      <td>9910</td>
      <td>风险等级过高</td>
      <td>High risk level.</td>
   </tr>
   <tr>
      <td>9911</td>
      <td>金额超过指定额度</td>
      <td>The amount over a specified amount </td>
   </tr>
   <tr>
      <td>9912</td>
      <td>暂不支持</td>
      <td>Unsupported card.</td>
   </tr>
   <tr>
      <td>9913</td>
      <td>该卡已签约成功 </td>
      <td>This card has alrealy signed up.</td>
   </tr>
   <tr>
      <td>9920</td>
      <td>退款失败</td>
      <td>Failed to refund.</td>
   </tr>
   <tr>
      <td>9921</td>
      <td>退款查询失败</td>
      <td>Failded to query the refund.</td>
   </tr>
   <tr>
      <td>9970</td>
      <td>银行系统日切处理中</td>
      <td>The bank system is changing the time of the system to keep account.Please try later.</td>
   </tr>
   <tr>
      <td>9983</td>
      <td>商户订单号重复</td>
      <td>The order number is repeated </td>
   </tr>
   <tr>
      <td>9990</td>
      <td>银行交易出错，{银行返回的错误信息}，请稍后重试</td>
      <td>Please contact our customer service to check this issue.</td>
   </tr>
   <tr>
      <td>9991</td>
      <td>银行交易出错，请联系客服，客服热线客服热线：4000188888</td>
      <td>Trade failed .Please contact service hotline :4000188888</td>
   </tr>
   <tr>
      <td>9999</td>
      <td>系统错误</td>
      <td>system error</td>
   </tr>
   <tr>
      <td></td>
   </tr>
</table>