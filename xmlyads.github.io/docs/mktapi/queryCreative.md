# 广告创意列表

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
| - promotion_goal  | array | 否 | 推广目标,不支出传入多个参数，<br/>详情请见枚举接口 ***promotion_goal*** |
| - status  | array | 否 | 状态，支持传入多个参数，详情请见枚举接口 ***creative_status*** |
| - keyword  | array | 否 | 查询关键字，不支持传入多个参数 |
| - query_start_date  | array | 否 | 查询起始时间，不支持传入多个参数 |
| - query_end_date  | array | 否 | 查询结束时间，不支持传入多个参数 |
| - media  | array | 否 | 目标app，不支持传入多个参数，详情请见枚举值 ***media*** |
| - positions  | array | 否 | 投放位置，支持传入多个参数，详情请见枚举值 ***position_type*** |
| - styles  | array | 否 | 样式选项，支持传入多个参数，详情见枚举 ***style_info*** |
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
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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