# 数据报表域查询

**请求地址 ：** /ads-catyph/v1/statement/field/get

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
| statement_field  | string | 是 | 查询域枚举，详情请见枚举接口[statement_field](queryEnum.md) |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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