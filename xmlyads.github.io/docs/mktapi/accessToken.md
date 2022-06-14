# 刷新Access_Token

Access_Token是调用Marketing-API接口的调用凭证，由于Access_Token具有时效性（默认30天）,当Access_Token超时后，可以使用Refresh_Token进行刷新，每次刷新都会同时重置二者的有效期。Refresh_Token拥有较长的有效期。


**请求地址 ：** https://catyph.ximalaya.com/ads-catyph/v1/token


**请求方式 ：** GET

**请求参数 ：**

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| refresh_token  | string | 是 | 刷新用token |


**请求示例 :**

```java
		OkHttpClient okHttpClient = new OkHttpClient();
		final Request request = new Request.Builder()
				.url(http://172.26.53.45:10787/ads-catyph/v1/token?refresh_token=222333)
                .method("GET", null)
				.build();
		final Call call = okHttpClient.newCall(request);
		new Thread(new Runnable() {
			@Override
			public void run() {
				try {
					Response response = call.execute();
				} catch (IOException e) {
					e.printStackTrace();
				}
			}
		}).start();
```


**返回字段释义 :**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
| data  | object | 返回数据 |
| - access_token  | string | access_token |
| - expires_in  | int | 超时时间 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "access_token": "c707da227e5032d2ea893918ac8dcaf8",
        "expires_in": 1652323236307
    }
}

```