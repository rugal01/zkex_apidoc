# 基础介绍

API使用HTTPS。

针对终端用户的API域名是`http://18.181.46.207:28080`。

API调用方式：

- 请求方式：总是GET或POST；
- 请求路径：总是以`/v1/`开头，例如`/v1/market/trades`；

## 请求参数

- GET请求以URL参数传入，例如：[http://18.181.46.207:28080/v1/market/bars/BTC_USDT/SEC?start=0&end=1](http://18.181.46.207:28080/v1/market/bars/BTC_USDT/SEC?start=0&end=1)。
- POST请求以JSON作为HTTP BODY传入，且必须设置Content-Type: application/json

## 返回参数

如果API调用成功，返回200，内容总是JSON，且具有`Content-Type: application/json`。

如果API调用失败，返回code非200，内容总是JSON，且具有`Content-Type: application/json`，

格式为固定的Error，请参考[https://18.181.46.207:28080/v1/market/error](https://18.181.46.207:28080/v1/market/error)。

如果API超过了业务频率限制，返回429，无内容，可根据返回头`X-RateLimit-Biz-Limit`、"`X-RateLimit-Biz-Burst`和`X-RateLimit-Biz-Remaining`获取限频次数。

## 字符编码

全部使用UTF-8且只能使用UTF-8。

示例：一个完整的GET请求：

```
https://uniapi.876ex.com/v1/market/ticks
```
