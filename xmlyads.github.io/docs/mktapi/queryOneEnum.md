# 枚举信息精确查询

根据枚举名查询枚举信息

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
| name  | string | 是 | 枚举名 |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | array | 返回枚举数组 |
| - name  | string | 枚举值名字 |
| - desc  | string | 枚举值描述 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": [
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
    ]
}

```

<br/>