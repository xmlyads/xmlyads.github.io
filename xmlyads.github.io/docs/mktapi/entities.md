# Entities

## 接口设计：

<br/>

### 1. 刷新Access_token

<br/>

Access_Token是调用Marketing-API接口的调用凭证，由于Access_Token具有时效性（默认1天）,当Access_Token超时后，可以使用Refresh_Token进行刷新，每次刷新都会同时重置二者的有效期。Refresh_Token拥有较长的有效期。

<br/>

**请求地址 ：** /ads-catyph/v1/token

<br/>

**请求方式 ：** GET

<br/>

**请求参数 ：**

<br/>

**传参形式 ：** Url Param

<br/>


|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| refresh_token  | string | 是 | 刷新用token |

<br/>

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

<br/>

**返回字段 :**
|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - developer_info  | object[] | 开发者应用账户授权列表 |
| -- app_id  | int | 应用id |
| -- ad_account_info_list  | object[] | 应用下授权账户列表 |
| --- ad_account_id  | int | 广告账户bcid |
| --- approval_status  | string | 授权状态 |

<br/>

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "text": "success",
    "data": {
        "developer_info": [
            {
                "app_id": 1,
                "ad_account_info_list": [
                    {
                        "ad_account_id": 201196,
                        "approval_status": "审核通过"
                    },
                    {
                        "ad_account_id": 751048,
                        "approval_status": "审核中"
                    },
                    {
                        "ad_account_id": 1265661,
                        "approval_status": "审核中"
                    }
                ]
            }
        ]
    },
    "cost": 0
}

```

<br/>

### 2. 获取当前开发者所有广告账户信息

获取当前接口拥有哪些账户的惭怍权限，以及账户的审核状态

**请求地址 ：** /ads-catyph/v1/developer/info

**请求方式 ：** GET

**请求参数 ：** 无

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |





