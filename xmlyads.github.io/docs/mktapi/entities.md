# Entities

## 接口设计：

### 1. 刷新Access_token

Access_Token是调用Marketing-API接口的调用凭证，由于Access_Token具有时效性（默认1天）,当Access_Token超时后，可以使用Refresh_Token进行刷新，每次刷新都会同时重置二者的有效期。Refresh_Token拥有较长的有效期。


**请求地址 ：** /ads-catyph/v1/token


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
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - access_token_info  | object | 登录鉴权返回实体 |
| -- app_id  | string | 应用id |
| -- ad_account_info_list  | object[] | 应用下授权账户列表 |
| --- ad_account_id  | int | 广告账户bcid |
| --- approval_status  | string | 授权状态 |


**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "text": "success",
    "data": {
        "access_token_info": {
            "access_token": "786fa8903bd8f0f409ba83c36c896df5",
            "expires_in": 1652273817845
        }
    },
    "cost": 0
}

```

<br/>

### 2. 获取当前开发者所有广告账户信息

获取当前开发者拥有哪些账户的惭怍权限，以及账户的审核状态

**请求地址 ：** /ads-catyph/v1/developer/info

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

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
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - developer_info  | object[] | 开发者应用账户授权列表 |
| -- app_id  | int | 应用id |
| -- ad_account_info_list  | object[] | 应用下授权账户列表 |
| --- ad_account_id  | int | 广告账户bcid |
| --- approval_status  | string | 授权状态 |

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

### 3. 计划组查询

查询广告账户下有哪些计划组

**请求地址 ：** /ads-catyph/v1/campaign/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：** 

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| ad_account_id  | int | 是 | 操作广告账户id |
| query  | string | 是 | 请求参数结构，json格式，具体字段如下 |

**query参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| fields  | array | 否 | 需要的返回字段，允许值：<br/>id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //id<br/>ad_account_id&nbsp; &nbsp; &nbsp; &nbsp; //广告账户id<br/>name&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //广告组名<br/>promotion_goal &nbsp; &nbsp; &nbsp;//推广目标<br/>budget_type&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //预算类型<br/>budget&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //预算值<br/>status&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //状态<br/>create_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //创建时间<br/>update_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //更新时间 |
| filter  | object | 否 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标 详情请见枚举接口 |
| - status  | array | 否 | 状态     详情请见枚举接口 |
| - keyword  | array | 否 | 查询关键字 |
| - query_start_date  | array | 否 | 查询起始时间 |
| - query_end_date  | array | 否 | 查询结束时间 |

**query示例：**

```json
{
    "filter":{
        "promotion_goal":[
            "CONTENT_PROMOTION"
        ]
    },
    "fields":[
        "id",
        "ad_account_id",
        "name",
        "promotion_goal"
    ]
}
```

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - campaign_list  | object[] | 计划组查询返回实体 |
| -- page_no  | int | 分页数 |
| -- page_size  | int | 页数大小 |
| -- records  | array | 计划组数据列表 |
| --- id  | string | 主键id |
| --- name  | string | 名字 |
| --- promotion_goal  | string | 推广目标 |
| --- ad_account_id  | int | 广告账户id |
| --- budget_type  | string | 预算类型 |
| --- budget  | string | 预算值 |
| --- status  | string | 状态 |
| --- create_time   | string | 创建时间 |
| --- update_time  | string | 更新时间 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "text": "success",
    "data": {
        "campaign_list": {
            "records": [
                {
                    "update_time": "0",
                    "create_time": "0",
                    "name": "内容推广_2022_02_14_15_22",
                    "id": "972047",
                    "promotion_goal": "CONTENT_PROMOTION",
                    "budget_type": "NO_LIMIT",
                    "ad_account_id": "201196",
                    "budget": "0",
                    "status": "ENABLED"
                }
            ],
            "page_no": 1,
            "page_size": 20
        }
    },
    "cost": 0
}

```

<br/>

### 4. 计划查询

查询计划

**请求地址 ：** /ads-catyph/v1/ad/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：** 

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| ad_account_id  | int | 是 | 操作广告账户id |
| query  | string | 是 | 请求参数结构，json格式，具体字段如下 |

**query参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| fields  | array | 否 | 需要的返回字段，允许值：<br/>id &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //id<br/>ad_account_id&nbsp; &nbsp; &nbsp; &nbsp; //广告账户id<br/>campaign_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //广告组id<br/>name&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //计划名<br/>app_postion_typenbsp; &nbsp; &nbsp; //样式组合<br/>delivery_goal&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //投放目标<br/>download_mode&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //下载方式<br/>show_status&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //展示状态<br/>quick_delivery&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //是否快速投放<br/>template_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //建站id<br/>template_name&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //建站名称<br/>create_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //创建时间<br/>update_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //更新时间<br/>start_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //开始时间<br/>end_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //结束时间<br/>schedule_time&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //时段定向<br/>target_url &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //落地页地址<br/>download_urlnbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //下载链接地址<br/>deep_link_url &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //deeplink地址<br/>application_pack_name &nbsp; &nbsp; &nbsp; &nbsp; //应用包名称<br/>js_track_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //js追踪id<br/>api_track_id&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//api追踪id<br/>refund_status&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //赔付状态<br/>ad_bidding&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //广告出价<br/>ad_target&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //人群定向|
| filter  | object | 否 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标 详情请见枚举接口 |
| - status  | array | 否 | 状态     详情请见枚举接口 |
| - keyword  | array | 否 | 查询关键字 |
| - query_start_date  | array | 否 | 查询起始时间 |
| - query_end_date  | array | 否 | 查询结束时间 |
| - budget_type  | array | 否 | 预算类型  详情请见枚举接口 |
| - charge_method  | array | 否 | 计费方式 详情见枚举接口 |
| - media  | array | 否 | 目标app  详情请见枚举值media |
| - positions  | array | 否 | 投放位置 详情请见枚举值 |
| page  | int | 否 | 默认值为1 |
| page_size  | int | 否 | 默认值为20 |

**query示例：**

```json
{
    "filter":{
        "promotion_goal":[
            "APPLICATION_DOWNLOAD"
        ]
    },
    "fields":[
        "id",
        "ad_account_id",
        "campaign_id",
        "name",
        "app_position_type",
        "delivery_goal",
        "download_mode"
    ]
}
```

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - ad_list  | object[] | 计划查询返回实体 |
| -- page_no  | int | 分页数 |
| -- page_size  | int | 页数大小 |
| -- records  | array | 计划组数据列表 |
| --- id  | string | 主键id |
| --- ad_account_id  | string | 广告账户id |
| --- campaign_id  | string | 广告组id |
| --- name  | string | 计划名 |
| --- app_postion_type  | string | 样式组合 |
| --- delivery_goal   | string | 投放目标  |
| --- download_mode  | string | 下载方式 |
| --- show_status  | string | 展示状态 |
| --- quick_delivery  | string | 是否快速投放 |
| --- template_id  | string | 建站id |
| --- template_name  | string | 建站名称 |
| --- create_time  | string | 创建时间 |
| --- update_time  | string | 更新时间 |
| --- start_time  | string | 开始时间 |
| --- end_time  | string | 结束时间 |
| --- schedule_time  | string | 时段定向 |
| --- target_url  | string | 落地页地址 |
| --- download_url  | string | 下载链接地址 |
| --- deep_link_url  | string | deeplink地址 |
| --- application_pack_name | string | 应用包名称 |
| --- js_track_id   | string | js追踪id |
| --- api_track_id   | string | api追踪id |
| --- refund_status  | string | 赔付状态 |
| --- ad_bidding  | string | 广告出价 |
| --- ad_target  | string | 广告定向 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "text": "success",
    "data": {
        "ad_list": {
            "records": [
                {
                    "ad_bidding": "{\"adId\":1003071,\"priceSecond\":0,\"ocpc\":false,\"ocpcStudyPhase\":\"0\",\"price\":0,\"chargeMethod\":0,\"budget\":0}",
                    "quick_delivery": "false",
                    "target_url": null,
                    "api_track_id": "0",
                    "js_track_id": "0",
                    "ad_account_id": "201196",
                    "update_time": "0",
                    "delivery_goal": "APPLICATION_DOWNLOAD",
                    "download_url": null,
                    "download_mode": "DOWNLOAD_URL",
                    "id": "1003071",
                    "show_status": "ENABLED",
                    "campaign_id": "972333",
                    "refund_status": null,
                    "create_time": "-383894664",
                    "deep_link_url": null,
                    "end_time": "-1479605224",
                    "application_pack_name": null,
                    "start_time": "-438641664",
                    "template_name": "",
                    "schedule_time": "Schedules[useSchedule=true,scheduleArray={16777215,16777215,16777215,16777215,16777215,16777215,16777215}]",
                    "app_position_type": "SYSTEM_PREFERENCES",
                    "name": "应用-内容推广",
                    "template_id": "0",
                    "ad_target": "{\"targetAudienceIds\":[],\"sex\":[],\"childAge\":[],\"operator\":[],\"platform\":[],\"network\":[],\"adId\":1003071,\"interest\":[],\"phoneBrand\":[],\"targetContentInterests\":[],\"age\":[],\"shortTermInterest\":[]}"
                }
            ],
            "page_no": 1,
            "page_size": 20
        }
    },
    "cost": 0
}

```

<br/>

### 5. 创意查询

创意查询

**请求地址 ：** /ads-catyph/v1/creative/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：** 

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| ad_account_id  | int | 是 | 操作广告账户id |
| query  | string | 是 | 请求参数结构，json格式，具体字段如下 |

**query参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| fields  | array | 否 | 需要的返回字段，允许值：***id,ad_id,ad_account_id,<br/>name,style,status,create_time,<br/>update_time,app_position_type,content***|
| filter  | object | 否 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标 详情请见枚举接口 |
| - status  | array | 否 | 状态     详情请见枚举接口 |
| - keyword  | array | 否 | 查询关键字 |
| - query_start_date  | array | 否 | 查询起始时间 |
| - query_end_date  | array | 否 | 查询结束时间 |
| - media  | array | 否 | 目标app  详情请见枚举值media |
| - positions  | array | 否 | 投放位置 详情请见枚举值 |
| - styles  | array | 否 | 样式选项 详情见枚举 |
| page  | int | 否 | 默认值为1 |
| page_size  | int | 否 | 默认值为20 |

**query示例：**

```json
{
    "filter":{
        "promotion_goal":[
            "APPLICATION_DOWNLOAD"
        ]
    },
    "fields":[
        "id",
        "ad_id",
        "ad_account_id",
        "name",
        "style",
        "status",
        "create_time",
        "update_time",
        "app_position_Type",
        "content"
    ]
}
```

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - creative_list  | object[] | 创意查询返回实体 |
| -- page_no  | int | 分页数 |
| -- page_size  | int | 页数大小 |
| -- records  | array | 创意数据列表 |
| --- id  | string | 主键id |
| --- ad_id  | string | 计划id |
| --- ad_account_id  | string | 广告账户id |
| --- name  | string | 创意名 |
| --- style  | string | 样式 |
| --- status  | string | 状态 |
| --- create_time  | string | 创建时间 |
| --- update_time  | string | 更新时间 |
| --- app_position_type  | string | 位置样式 |
| --- content  | string | 创意内容 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "text": "success",
    "data": {
        "creativeList": {
            "records": [
                {
                    "ad_id": "1002926",
                    "update_time": "0",
                    "create_time": "0",
                    "app_position_type": "SYSTEM_PREFERENCES",
                    "name": "梁浅-小喜马测试1",
                    "style": null,
                    "id": "1007810",
                    "content": "{\"adId\":1002926,\"createTime\":0,\"adAccountId\":201196,\"name\":\"梁浅-小喜马测试1\",\"updateTime\":0,\"id\":1007810,\"status\":\"ENABLED\"}",
                    "ad_account_id": "201196",
                    "status": "ENABLED"
                }
            ],
            "page_no": 1,
            "page_size": 20
        }
    },
    "cost": 0
}

```

<br/>

### 6. 素材查询

**请求地址 ：** /ads-catyph/v1/creative/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：** 

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| ad_account_id  | int | 是 | 操作广告账户id |
| creative_id_list  | array | 是 | 创意id列表 |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| data  | object | 返回数据 |
| - creative_list  | object[] | 创意查询返回实体 |
| -- page_no  | int | 分页数 |
| -- page_size  | int | 页数大小 |
| -- records  | array | 创意数据列表 |
| --- id  | string | 主键id |
| --- ad_id  | string | 计划id |
| --- ad_account_id  | string | 广告账户id |
| --- name  | string | 创意名 |
| --- style  | string | 样式 |
| --- status  | string | 状态 |
| --- create_time  | string | 创建时间 |
| --- update_time  | string | 更新时间 |
| --- app_position_type  | string | 位置样式 |
| --- content  | string | 创意内容 |