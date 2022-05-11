# Entities

## 接口设计：

### 1. 刷新Access_Token

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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回数据 |
| - app_id  | int | 应用id |
| - ad_account_info_list  | object[] | 应用下授权账户列表 |
| -- ad_account_id  | int | 广告账户bcid |
| -- approval_status  | string | 授权状态 |

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
| page_no | int | 否 | 查询结束时间 |
| page_size | int | 否 | 查询结束时间 |

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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回数据 |
| - page_no  | int | 分页数 |
| - page_size  | int | 页数大小 |
| - records  | array | 计划组数据列表 |
| -- id  | string | 主键id |
| -- name  | string | 名字 |
| -- promotion_goal  | string | 推广目标 |
| -- ad_account_id  | int | 广告账户id |
| -- budget_type  | string | 预算类型 |
| -- budget  | string | 预算值 |
| -- status  | string | 状态 |
| -- create_time   | string | 创建时间 |
| -- update_time  | string | 更新时间 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "update_time": "0",
                "create_time": "0",
                "name": "测试：内容推广_2022_05_10_15_33",
                "id": "972417",
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
| page_no | int | 否 | 默认值为1 |
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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回数据 |
| - page_no  | int | 分页数 |
| - page_size  | int | 页数大小 |
| - records  | array | 计划组数据列表 |
| -- id  | string | 主键id |
| -- ad_account_id  | string | 广告账户id |
| -- campaign_id  | string | 广告组id |
| -- name  | string | 计划名 |
| -- app_postion_type  | string | 样式组合 |
| -- delivery_goal   | string | 投放目标  |
| -- download_mode  | string | 下载方式 |
| -- show_status  | string | 展示状态 |
| -- quick_delivery  | string | 是否快速投放 |
| -- template_id  | string | 建站id |
| -- template_name  | string | 建站名称 |
| -- create_time  | string | 创建时间 |
| -- update_time  | string | 更新时间 |
| -- start_time  | string | 开始时间 |
| -- end_time  | string | 结束时间 |
| -- schedule_time  | string | 时段定向 |
| -- target_url  | string | 落地页地址 |
| -- download_url  | string | 下载链接地址 |
| -- deep_link_url  | string | deeplink地址 |
| -- application_pack_name | string | 应用包名称 |
| -- js_track_id   | string | js追踪id |
| -- api_track_id   | string | api追踪id |
| -- refund_status  | string | 赔付状态 |
| -- ad_bidding  | string | 广告出价 |
| -- ad_target  | string | 广告定向 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "ad_bidding": "{\"adId\":1003278,\"priceSecond\":1,\"ocpc\":false,\"ocpcStudyPhase\":\"0\",\"price\":0,\"chargeMethod\":0,\"budget\":0}",
                "quick_delivery": "false",
                "target_url": null,
                "api_track_id": "527",
                "js_track_id": "0",
                "ad_account_id": "201196",
                "update_time": "0",
                "delivery_goal": "APPLICATION_DOWNLOAD",
                "download_url": null,
                "download_mode": "DOWNLOAD_URL",
                "id": "1003278",
                "show_status": "ENABLED",
                "campaign_id": "972418",
                "refund_status": null,
                "create_time": "-1369496960",
                "deep_link_url": null,
                "end_time": "1803594776",
                "application_pack_name": null,
                "start_time": "-1450408960",
                "template_name": "",
                "schedule_time": "Schedules[useSchedule=true,scheduleArray={16777215,16777215,16777215,16777215,16777215,16777215,16777215}]",
                "app_position_type": "NATIVE_FEEDS_RECOMMEND",
                "name": "oCPC_05_10_22:28",
                "template_id": "0",
                "ad_target": "{\"targetAudienceIds\":[],\"sex\":[],\"childAge\":[],\"operator\":[],\"platform\":[\"ANDROID\"],\"network\":[],\"adId\":1003278,\"interest\":[],\"phoneBrand\":[],\"targetContentInterests\":[],\"age\":[],\"shortTermInterest\":[]}"
            }
        ],
        "page_no": 1,
        "page_size": 20
    }
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
| page_no  | int | 否 | 默认值为1 |
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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回数据 |
| - page_no  | int | 分页数 |
| - page_size  | int | 页数大小 |
| - records  | array | 创意数据列表 |
| -- id  | string | 主键id |
| -- ad_id  | string | 计划id |
| -- ad_account_id  | string | 广告账户id |
| -- name  | string | 创意名 |
| -- style  | string | 样式 |
| -- status  | string | 状态 |
| -- create_time  | string | 创建时间 |
| -- update_time  | string | 更新时间 |
| -- app_position_type  | string | 位置样式 |
| -- content  | string | 创意内容 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "ad_id": "1003259",
                "update_time": "0",
                "create_time": "0",
                "app_position_type": "NATIVE_FEEDS_RECOMMEND",
                "name": "2222",
                "style": "HORIZONTAL_SCREEN_VIDEO",
                "id": "1010655",
                "content": "{\"adId\":1003259,\"createTime\":0,\"adAccountId\":201196,\"name\":\"2222\",\"updateTime\":0,\"id\":1010655,\"status\":\"ENABLED\"}",
                "ad_account_id": "201196",
                "status": "ENABLED"
            }
        ],
        "page_no": 1,
        "page_size": 20
    }
}

```

<br/>

### 6. 素材查询

**请求地址 ：** /ads-catyph/v1/segment/get

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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | array | 返回数据 |
| - creative_id  | int | 创意id |
| - segment_list  | array | 素材列表 |
| -- file_ext_name  | string | 文件扩展名 |
| -- file_url  | string | 文件地址 |
| -- width  | int | 文件宽度 |
| -- height | int | 文件高度 |
| -- duration  | int | 时长 |
| -- file_name  | string | 文件名 |

**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": [
        {
            "creative_id": 225865,
            "segment_list": [
                {
                    "file_ext_name": ".jpg",
                    "file_url": null,
                    "width": 1280,
                    "height": 720,
                    "duration": 0,
                    "file_name": null
                },
                {
                    "file_ext_name": ".png",
                    "file_url": null,
                    "width": 108,
                    "height": 108,
                    "duration": 0,
                    "file_name": null
                }
            ]
        }
    ]
}

```

<br/>

### 7. 统计报表查询

**请求地址 ：** /ads-catyph/v1/statement/get

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
| fields  | array | 否 | 需要的返回字段，允许值：***date_time,name,user_id,<br/>show,click,conv_num,deep_conv_num,<br/>ctr,cvr,deep_cvr,consume,cpc_consume,cpa,cpm,deep_cpa***|
| filter  | object | 否 | 查询条件 |
| - query_type  | array | 否 | 查询类型 详情请见枚举 |
| - other_dimension  | array | 否 | 查询域  详情请见枚举 |
| - time_dimension  | array | 否 | 时间维度 DAY：天 ，HOUR：小时 |
| - filter_value  | array | 否 | 筛选值 ：详情请见报表搜索域接口返回值 |
| - query_end_date  | array | 否 | 结束时间 |
| - query_start_date  | array | 否 | 开始时间 |
| page_no  | int | 否 | 默认值为1 |
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
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | array | 返回数据 |
| - page_no  | int | 分页数 |
| - page_size  | int | 每页大小 |
| - records  | array | 文件扩展名 |
| -- date_time  | string | 日期 |
| -- name  | string | 名字 |
| -- userId  | string | 用户id |
| -- show  | string | 用户展示数 |
| -- click  | string | 点击数 |
| -- conv_num  | string | 转化数 |
| -- deep_conv_num  | string | 深度转化数 |
| -- ctr  | string | 点击率 |
| -- cvr  | string | 转化率 |
| -- deep_cvr  | string | 深度转化率 |
| -- consume  | string | 消耗 |
| -- cpc_consume  | string | cpc消耗 |
| -- cpa  | string | cpa |
| -- cpm  | string | cpm |
| -- deep_cpa  | string | 深度转化成本 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "deep_conv_num": "0",
                "ctr": "6.48%",
                "conv_num": "0",
                "date_time": "2022-04-27",
                "user_id": "0",
                "deep_cvr": "0.00%",
                "name": null,
                "show": "108",
                "consume": "0",
                "click": "7",
                "cvr": "null"
            }
        ],
        "page_no": 1,
        "page_size": 20
    }
}

```

<br/>

### 8. 报表查询域获取接口

**请求地址 ：** /ads-catyph/v1/statement/field/get

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
| statement_field  | string | 是 | 查询域枚举，详情请见枚举接口 |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | array | 返回数据 |
| - id  | int | 数据主键id |
| - name  | string | 数据名 |
| - statement_field  | string | 查询域名称 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": [
        {
            "id": 972187,
            "name": "自动化测试推广组2022-03-17 05:35:02",
            "statement_field": "CAMPAIGN"
        }
    ]
}

```

<br/>

### 9. 获取枚举信息

**请求地址 ：** /ads-catyph/v1/system-enum/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：**  无

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回数据 |
| - enum  | array | 枚举类数组 |
| -- name  | string | 枚举值名 |
| -- desc  | string | 枚举值含义描述 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "refund_status": [
            {
                "name": "FIRST_PERIOD_END",
                "desc": "第一周期赔付结束"
            },
            {
                "name": "SECOND_PERIOD_END",
                "desc": "第二周期赔付结束"
            },
            {
                "name": "INVALID",
                "desc": "第二周期赔付结束"
            }
        ],
        "deep_target": [
            {
                "name": "NONE",
                "desc": "无"
            },
            {
                "name": "REGISTER",
                "desc": "注册"
            },
            {
                "name": "LEAVE",
                "desc": "次留"
            },
            {
                "name": "PAY",
                "desc": "付费"
            }
        ],
        "style_info": [
            {
                "name": "FULL_SCREEN_GIF",
                "desc": "全屏GIF"
            },
            {
                "name": "FULL_SCREEN_VIDEO",
                "desc": "全屏视频"
            },
            {
                "name": "NON_FULL_SCREEN_BIGIMAGE",
                "desc": "非全屏大图"
            },
            {
                "name": "HORIZONTAL_SCREEN_BIGIMAGE",
                "desc": "横屏大图"
            },
            {
                "name": "HORIZONTAL_SCREEN_VIDEO",
                "desc": "横屏视频"
            },
            {
                "name": "HORIZONTAL_SCREEN_EXTRABIGIMAGE",
                "desc": "横屏特大图"
            },
            {
                "name": "SQUARE_SCREEN_BIGIMAGE",
                "desc": "方屏大图"
            },
            {
                "name": "SOUND_AND_SMALL_YELLOW_STRIP",
                "desc": "声音+小黄条"
            },
            {
                "name": "BANNER_SMALL_IMAGE",
                "desc": "横幅小图"
            },
            {
                "name": "SOUND_AND_PATCH",
                "desc": "声音+贴片"
            },
            {
                "name": "SCATTER_FLOWERS",
                "desc": "通栏撒花"
            },
            {
                "name": "VIDEO_PROGRAM",
                "desc": "视频节目"
            },
            {
                "name": "FULL_SCREEN_BIGIMAGE",
                "desc": "全屏大图"
            },
            {
                "name": "VERTICAL_SCREEN_BIGIMAGE",
                "desc": "竖屏大图"
            },
            {
                "name": "VERTICAL_SCREEN_VIDEO",
                "desc": "竖屏视频"
            },
            {
                "name": "ANCHOR_SOUND",
                "desc": "主播声音"
            },
            {
                "name": "HIGHLIGHT_BIGIMAGE",
                "desc": "高光大图"
            }
        ],
        "media": [
            {
                "name": "XMLY_MAIN_APP",
                "desc": "喜马拉雅主APP"
            },
            {
                "name": "XMLY_JISUBAN",
                "desc": "喜马拉雅极速版"
            }
        ],
        "charge_method": [
            {
                "name": "CPM",
                "desc": "按照展示计费"
            },
            {
                "name": "CPT",
                "desc": "按照时长来计费"
            },
            {
                "name": "OTHER",
                "desc": "其他"
            },
            {
                "name": "CPC",
                "desc": "按照点击计费"
            }
        ],
        "type": [
            {
                "name": "JS",
                "desc": "JS布码"
            },
            {
                "name": "TEMPLATE",
                "desc": "自建站组件"
            },
            {
                "name": "JS_API",
                "desc": "JS_API"
            }
        ],
        "ad_status": [
            {
                "name": "ENABLED",
                "desc": "投放中"
            },
            {
                "name": "PAUSED",
                "desc": "未开启"
            },
            {
                "name": "DELETED",
                "desc": "已删除"
            },
            {
                "name": "PLAN_OVER_BUDGET",
                "desc": "广告计划超出预算"
            },
            {
                "name": "NOT_YET_DATE",
                "desc": "计划未达投放时间"
            },
            {
                "name": "OVER_DATE",
                "desc": "计划超过投放时间"
            },
            {
                "name": "NOT_TIME_RANGE",
                "desc": "不在投放时段"
            },
            {
                "name": "PAUSED_BY_PLAN_TASK",
                "desc": "已被广告组暂停"
            },
            {
                "name": "NO_MATERIAL",
                "desc": "无在投创意"
            },
            {
                "name": "TRACK_INVALID",
                "desc": "转化事件无效"
            },
            {
                "name": "TEMPLATE_INVALID",
                "desc": "自建站点无效"
            },
            {
                "name": "CONTENT_INVALID",
                "desc": "内容节目审核未通过"
            }
        ],
        "target": [
            {
                "name": "ACTIVATION",
                "desc": "激活"
            },
            {
                "name": "REGISTRATION",
                "desc": "注册"
            },
            {
                "name": "RETENTION",
                "desc": "次留"
            },
            {
                "name": "PAY",
                "desc": "付费"
            },
            {
                "name": "ACTIVE",
                "desc": "首活"
            }
        ],
        "other_dimension": [
            {
                "name": "APP",
                "desc": "投放媒体"
            },
            {
                "name": "PROMOTION_GOAL",
                "desc": "推广目标"
            },
            {
                "name": "POSITION_TYPE",
                "desc": "投放形式"
            },
            {
                "name": "POSITION_STYLE",
                "desc": "创意样式"
            }
        ],
        "delivery_goal": [
            {
                "name": "CONVERSION",
                "desc": "转化量"
            },
            {
                "name": "CLICK",
                "desc": "点击量"
            },
            {
                "name": "SUBSCRIBE",
                "desc": "订阅量"
            },
            {
                "name": "PLAY",
                "desc": "播放量"
            },
            {
                "name": "SHOW",
                "desc": "曝光量"
            }
        ],
        "campaign_status": [
            {
                "name": "ENABLED",
                "desc": "投放中"
            },
            {
                "name": "PAUSED",
                "desc": "未开启"
            },
            {
                "name": "DELETED",
                "desc": "已删除"
            },
            {
                "name": "BALANCE_INSUFFICIENT",
                "desc": "账户余额不足"
            },
            {
                "name": "OVER_DAILY_BUDGET",
                "desc": "账户超出日预算"
            },
            {
                "name": "OVER_TASK_BUDGET",
                "desc": "广告组超出预算（含日&总）"
            },
            {
                "name": "NO_PLAN",
                "desc": "无在投计划"
            }
        ],
        "download_mode": [
            {
                "name": "DOWNLOAD_URL",
                "desc": "下载链接"
            },
            {
                "name": "TARGET_URL",
                "desc": "落地页"
            },
            {
                "name": "MINI_APP",
                "desc": "小程序"
            },
            {
                "name": "ALBUM",
                "desc": "专辑"
            },
            {
                "name": "TRACK",
                "desc": "声音"
            }
        ],
        "statement_field": [
            {
                "name": "USER",
                "desc": "账户"
            },
            {
                "name": "CAMPAIGN",
                "desc": "广告组"
            },
            {
                "name": "Ad",
                "desc": "广告计划"
            },
            {
                "name": "CREATIVE",
                "desc": "广告创意"
            }
        ],
        "network_type": [
            {
                "name": "MOBILE2G",
                "desc": "2g"
            },
            {
                "name": "MOBILE3G",
                "desc": "3g"
            },
            {
                "name": "MOBILE4G",
                "desc": "4g"
            },
            {
                "name": "WIFI",
                "desc": "wifi"
            },
            {
                "name": "MOBILE5G",
                "desc": "5g"
            },
            {
                "name": "MOBILE6G",
                "desc": "6g"
            },
            {
                "name": "OTHER",
                "desc": ""
            }
        ],
        "click_button": [
            {
                "name": "VIEW_DETAILS",
                "desc": "查看详情"
            },
            {
                "name": "VIEW_NOW",
                "desc": "立即查看"
            },
            {
                "name": "LEARN_MORE",
                "desc": "了解详情"
            },
            {
                "name": "DOWNLOAD_NOW",
                "desc": "立即下载"
            }
        ],
        "position_type": [
            {
                "name": "NATIVE_FEEDS_RECOMMEND",
                "desc": "原生-信息流推荐"
            },
            {
                "name": "NATIVE_OTHERS",
                "desc": "原生-其他"
            },
            {
                "name": "NATIVE_NO_SOUND_PATCH",
                "desc": "原生-无声贴片"
            },
            {
                "name": "NATIVE_SOUND_PATCH",
                "desc": "原生-有声贴片"
            },
            {
                "name": "NATIVE_FOCUS_IMAGE",
                "desc": "原生-焦点图"
            },
            {
                "name": "NATIVE_HOMEPAGE_BIGIMAGE",
                "desc": "原生-首页大图"
            },
            {
                "name": "SOUND_INTERACTION",
                "desc": "声音互动"
            },
            {
                "name": "OPEN_SCREEN",
                "desc": "开屏"
            },
            {
                "name": "SYSTEM_PREFERENCES",
                "desc": "系统优选"
            },
            {
                "name": "HOMEPAGE_HOVER_TOUCH",
                "desc": "首页悬浮touch"
            },
            {
                "name": "MOTIVATION_VIDEO",
                "desc": "激励视频"
            }
        ],
        "promotion_goal": [
            {
                "name": "APPLICATION_DOWNLOAD",
                "desc": "应用下载"
            },
            {
                "name": "CLUE_COLLECTION",
                "desc": "销售线索收集"
            },
            {
                "name": "CONTENT_PROMOTION",
                "desc": "内容推广"
            }
        ],
        "budget_type": [
            {
                "name": "NO",
                "desc": "未设置"
            },
            {
                "name": "ALL",
                "desc": "全部"
            },
            {
                "name": "TOTAL_BUDGET",
                "desc": "总预算"
            },
            {
                "name": "DAILY_BUDGET",
                "desc": "日预算"
            },
            {
                "name": "NO_LIMIT",
                "desc": "不限"
            }
        ]
    }
}

```

<br/>

### 10. 开发者申请账户权限

**请求地址 ：** /ads-catyph/v1/approval/launch

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
| app_id  | int | 是 | 开发者名下appid |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回添加授权状态 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": true
}

```

<br/>