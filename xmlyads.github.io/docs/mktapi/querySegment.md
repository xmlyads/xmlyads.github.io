# 广告素材列表

获取广告素材列表信息

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
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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
                    "file_url": "http://fdfs.xmcdn.com/group90/M05/B7/11/wKg5PV9pun-AkVrQAAGQ7AD-evE442.jpg",
                    "width": 1280,
                    "height": 720,
                    "duration": 0,
                    "file_name": "wKg5PV9pun-AkVrQAAGQ7AD-evE442.jpg"
                }
            ]
        }
    ]
}

```

<br/>