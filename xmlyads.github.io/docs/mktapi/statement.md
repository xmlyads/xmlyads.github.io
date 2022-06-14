# 数据报表列表

获取广告主数据报表信息

**请求地址 ：** https://catyph.ximalaya.com/ads-catyph/v1/statement/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access-token  | string | 是 | 鉴权用access-token |

**请求参数 ：** 

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| ad_account_id  | int | 是 | 操作广告账户id |
| query  | string | 是 | 请求参数结构，json格式，需要urlEncode，具体字段如下 |

**query参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| fields  | array | 是 | 需要的返回字段，允许值：***date_time,name,user_id,<br/>show,click,conv_num,deep_conv_num,<br/>ctr,cvr,deep_cvr,consume,cpc_consume,cpa,cpm,deep_cpa***|
| filter  | object | 是 | 查询条件 |
| - query_type  | array | 是 | 查询类型，不支持多个参数，详情请见枚举 [statement_field](queryEnum.md) |
| - other_dimension  | array | 否 | 查询域，不支持多个参数，详情请见枚举 [other_dimension](queryEnum.md) |
| - time_dimension  | array | 是 | 时间维度，不支持多个参数， DAY：天 ，HOUR：小时 |
| - filter_value  | array | 否 | 筛选值，支持传入多个参数，详情请见[报表搜索域接口](queryStatementField.md) |
| - query_end_date  | array | 是 | 结束时间，不支持多个参数 |
| - query_start_date  | array | 是 | 开始时间，不支持多个参数 |
| page_no  | int | 否 | 默认值为1 |
| page_size  | int | 否 | 默认值为20 |

**query示例：**

```json
{
    "filter":{
        "query_start_date":[
            "2022-06-07"
        ],
        "query_end_date":[
            "2022-06-09"
        ],
        "time_dimension":["DAY"],
       "query_type":["USER"]
    },
    "fields":[
        "date_time",
        "name",
        "user_id",
        "show",
        "click",
        "conv_num",
        "deep_conv_num",
        "ctr",
        "cvr",
        "deep_cvr",
        "consume",
        "cpc_consume",
        "cpa",
        "cpm",
        "deep_cpa"
    ],
    "page_no":1,
    "page_size":20
}
```

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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