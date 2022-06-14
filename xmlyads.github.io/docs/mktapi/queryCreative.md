# 广告创意列表

**请求地址 ：** https://catyph.ximalaya.com/ads-catyph/v1/creative/get

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
| fields  | array | 是 | 需要的返回字段，允许值：***id,ad_id,ad_account_id,<br/>name,style,status,create_time,<br/>update_time,app_position_type,content***|
| filter  | object | 是 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标,不支出传入多个参数，<br/>详情请见枚举接口 [promotion_goal](queryEnum.md) |
| - status  | array | 否 | 状态，支持传入多个参数，详情请见枚举接口 [creative_status](queryEnum.md) |
| - keyword  | array | 否 | 查询关键字，不支持传入多个参数 |
| - media  | array | 否 | 目标app，不支持传入多个参数，详情请见枚举值 [media](queryEnum.md) |
| - positions  | array | 否 | 投放位置，支持传入多个参数，详情请见枚举值 [position_type](queryEnum.md) |
| - styles  | array | 否 | 样式选项，支持传入多个参数，详情见枚举 [style_info](queryEnum.md) |
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
| -- style  | string | 样式 详情请见枚举接口 [style_info](queryEnum.md) |
| -- status  | string | 状态 详情请见枚举接口 [creative_status](queryEnum.md)  |
| -- create_time  | string | 创建时间 |
| -- update_time  | string | 更新时间 |
| -- position  | string | 位置样式 详情请见枚举接口 [position_type](queryEnum.md) |
| -- content  | string | 创意内容 |
| --- creative_id  | int | 创意id |
| --- description  | string | 创意描述 |
| --- ad_account_id  | int | 广告账户id |
| --- app_desc  | string | app描述 |
| --- video_duration  | int | 视频长度 |
| --- album_id  | int | 专辑id |
| --- track_id  | int | 声音id |
| --- sound_content  | string | 音频文字版 |
| --- urls  | string | 上传素材元素id和地址 |
| --- click_button  | string | 行为号召 详情请见枚举接口 [click_button](queryEnum.md) |
| --- title  | string | 标题 |
| --- third_click_stat_url  | string | 三方点击链接 |
| --- show_monitor_url  | string | 展示监控链接 |
| --- promotion_app_name  | string | app名 |
| --- upload_id  | string | 上传id |
| --- pic_upload_id  | string | 图片上传id |
| --- storage_id  | string | 上传模块id |


**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "id": 1008108,
                "ad_id": 1002970,
                "ad_account_id": 201196,
                "name": "非拉活 极速版创意标题",
                "style": "HORIZONTAL_SCREEN_BIGIMAGE",
                "status": "PAUSED",
                "create_time": 0,
                "update_time": 0,
                "position": "NATIVE_HOMEPAGE_BIGIMAGE",
                "content": {
                    "creative_id": 1008108,
                    "description": "非拉活 极速版创意描述",
                    "app_desc": "非拉活 极速版应用描述",
                    "video_duration": 0,
                    "album_id": 0,
                    "track_id": 0,
                    "sound_content": "",
                    "urls": {
                        "35": "http://audiotest.cos.tx.xmcdn.com/storages/1df7-audiotest/D0/2D/GKwaPd0GDgwnAAD7qwAAY-w5.jpg",
                        "20": "http://audiotest.cos.tx.xmcdn.com/storages/e4f8-audiotest/D7/2B/GKwaPd0GDgwXAAHHaQAAY-w1.jpg",
                        "14": "http://audiotest.cos.tx.xmcdn.com/storages/0aa4-audiotest/E4/6E/GKwaPd0GDgwaAAGLCwAAY-w2.jpg"
                    },
                    "click_button": "VIEW_NOW",
                    "title": "非拉活 极速版 首页大图图片物料",
                    "third_click_stat_url": null,
                    "show_monitor_url": "https://skclick.jd.com/feedback/monitor?idfa=_IDFA_&imei=_IMEI_MD5_&oaid=_OAID_&ua=_UA_&clktime=_TS_&ip=_IP_&planid=1002970&os=_MODEL_&unitid=972266&creativeid=1008108&bd_vid=_RESPONSE_ID_&media=xmly&utmsource=xmly-feed&converttype=0&callbackurl=_CALLBACK_URL_",
                    "promotion_app_name": "非拉活 极速版应用名",
                    "upload_id": "0",
                    "pic_upload_id": "0",
                    "storage_id": null
                }
            }
        ],
        "page_no": 1,
        "page_size": 20
    }
}

```

<br/>