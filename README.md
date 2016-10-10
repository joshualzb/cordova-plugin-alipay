# cordova-plugin-alipay
cordova 支付宝插件,alipay

1.移除现有的插件（如果你已经安装了的话）
cordova plugin remove cordova-plugin-alipay

2.安装这个插件

cordova plugin add https://github.com/joshualzb/cordova-plugin-alipay.git

3.重新添加IOS、ANDROID平台

cordova platform remove ios(android)
cordova platform add ios(android)

4.调用

param:格式参考支付宝官网API的格式(https://doc.open.alipay.com/docs/doc.htm?spm=a219a.7629140.0.0.Zeb8bN&treeId=193&articleId=105465&docType=1)

var param='app_id=2015052600090779&biz_content=%7B%22timeout_express%22%3A%2230m%22%2C%22seller_id%22%3A%22%22%2C%22product_code%22%3A%22QUICK_MSECURITY_PAY%22%2C%22total_amount%22%3A%220.01%22%2C%22subject%22%3A%221%22%2C%22body%22%3A%22%E6%88%91%E6%98%AF%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%22%2C%22out_trade_no%22%3A%22IQJZSRC1YMQB5HU%22%7D&charset=utf-8&format=json&method=alipay.trade.app.pay&notify_url=http%3A%2F%2Fdomain.merchant.com%2Fpayment_notify&sign_type=RSA&timestamp=2016-08-25%2020%3A26%3A31&version=1.0&sign=cYmuUnKi5QdBsoZEAbMXVMmRWjsuUj%2By48A2DvWAVVBuYkiBj13CFDHu2vZQvmOfkjE0YqCUQE04kqm9Xg3tIX8tPeIGIFtsIyp%2FM45w1ZsDOiduBbduGfRo1XRsvAyVAv2hCrBLLrDI5Vi7uZZ77Lo5J0PpUUWwyQGt0M4cj8g%3D';

window.alipay.pay({params: param}, function (successResults) {
              //支付成功
            }, function (errorResults) {
                console.log(errorResults);
                if (errorResults.resultStatus == 4000) {
                    $.toast('请确认支付宝正确安装后再试');
                } else {
                    $.toast('支付宝错误：' + errorResults.memo + '(' + errorResults.resultStatus + ')');
                }
            });
            
         
