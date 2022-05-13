# 广告计划列表

获取广告计划列表信息

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
| fields  | array | 否 | 需要的返回字段，允许值：***id,ad_account_id,name,<br/>promotion_goal,budget_type,budget,status,<br/>create_time,update_time***|
| filter  | object | 否 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标，不支出传入多个参数，详情请见枚举<br/>[promotion_goal](queryEnum.md) |
| - status  | array | 否 | 状态，支持传入多个参数，详情请见枚举接口 [campaign_status](queryEnum.md) |
| - keyword  | array | 否 | 查询关键字，不支持传入多个参数 |
| page_no | int | 否 | 默认值为1 |
| page_size | int | 否 | 默认值为20 |

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
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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