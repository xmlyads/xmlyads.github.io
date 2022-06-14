# 授权信息查询

获取当前开发者拥有哪些账户的操作权限，以及账户的审核状态

**请求地址 ：** https://catyph.ximalaya.com/ads-catyph/v1/developer/info

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access-token  | string | 是 | 鉴权用access-token |

**请求参数 ：** 无

**请求示例 :**

```java
		OkHttpClient okHttpClient = new OkHttpClient();
		final Request request = new Request.Builder()
				.url("http://172.26.53.45:10787/ads-catyph/v1/developer/info")
				.method("GET", null)
				.header("access_token", "320e1807136bdcd1b099fda4b4ed66e1")
				.build();
		final Call call = okHttpClient.newCall(request);
		new Thread(new Runnable() {
			@Override
			public void run() {
				try {
					Response response = call.execute();
					System.out.println("run: " + response.body().string());
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
| - app_id  | int | 应用id |
| - ad_account_info_list  | array | 应用下授权账户列表 |
| -- ad_account_id  | int | 广告账户bcid |
| -- authorization_status  | string | 授权状态 详情请见枚举接口 [authorization_status]      (queryEnum.md) |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": [
        {
            "app_id": 1,
            "ad_account_info_list": [
                {
                    "ad_account_id": 201196,
                    "authorization_status": "AUTHORIZATION_PASS"
                },
                {
                    "ad_account_id": 751048,
                    "authorization_status": "AUTHORIZATIONING"
                },
                {
                    "ad_account_id": 1265661,
                    "authorization_status": "AUTHORIZATIONING"
                }
            ]
        }
    ]
}

```

<br/>