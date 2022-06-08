# 广告单元列表

获取广告单元列表信息

**请求地址 ：** /ads-catyph/v1/ad/get

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
| query  | string | 是 | 请求参数结构，json格式，具体字段如下 |

**query参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| fields  | array | 否 | 需要的返回字段，允许值：***id ,ad_account_id,campaign_id,<br/>name,app_postion_type,delivery_goal,download_mode,<br/>show_status,quick_delivery,template_id,template_name,<br/>create_time,update_time,start_time,end_time,schedule_time,<br/>target_url ,download_url,deep_link_url,<br/>application_pack_name,js_track_id,api_track_id,<br/>refund_status,ad_bidding,ad_target*** |
| filter  | object | 否 | 查询条件 |
| - promotion_goal  | array | 否 | 推广目标，不支持传入多个参数，<br/>详情请见枚举接口 [promotion_goal](queryEnum.md) |
| - status  | array | 否 | 状态，支持传入多个参数，<br/>详情请见枚举接口 [ad_status](queryEnum.md) |
| - keyword  | array | 否 | 查询关键字，不支持传入多个参数 |
| - budget_type  | array | 否 | 预算类型，不支持传入多个参数，<br/>详情请见枚举接口 [budget_type](queryEnum.md) |
| - charge_method  | array | 否 | 计费方式，不支持传入多个参数，<br/>详情见枚举接口 [charge_method](queryEnum.md) |
| - media  | array | 否 | 目标app，不支持传入多个参数，<br/>详情请见枚举值 [media](queryEnum.md) |
| - positions  | array | 否 | 投放位置，支持传入多个参数，<br/>详情请见枚举值 [position_type](queryEnum.md) |
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
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
| data  | object | 返回数据 |
| - page_no  | int | 分页数 |
| - page_size  | int | 页数大小 |
| - records  | array | 计划组数据列表 |
| -- id  | string | 主键id |
| -- ad_account_id  | string | 广告账户id |
| -- campaign_id  | string | 广告组id |
| -- name  | string | 计划名 |
| -- position | string | 样式组合 详情请见枚举接口 [position_type](queryEnum.md) |
| -- delivery_goal   | string | 投放目标 详情请见枚举接口 [delivery_goal](queryEnum.md) |
| -- download_mode  | string | 下载方式 详情请见枚举接口 [download_mode](queryEnum.md) |
| -- status  | string | 展示状态 详情请见枚举接口 [ad_status](queryEnum.md) |
| -- quick_delivery  | boolean | 是否快速投放 |
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
| -- refund_status  | string | 赔付状态 详情请见枚举接口 [refund_status](queryEnum.md) |
| -- ad_bidding  | string | 广告出价 |
| --- ad_id  | int | 计划id |
| --- budget_type  | string | 预算类型 详情请见枚举接口 [budget_type](queryEnum.md) |
| --- budget  | int | 预算 |
| --- charge_method  | string | 计费方式 详情请见枚举接口 [charge_method](queryEnum.md) |
| --- price  | int | 价格 |
| --- price_second  | int | 二阶段出价 |
| --- ocpc_study_phase  | string | ocpc学习阶段 |
| --- _ocpc  | boolean | 是否是ocpc |
| -- ad_target  | string | 广告定向 |
| --- ad_id  | int | 计划id |
| --- target_audience  | array | 定向人群包 |
| --- exclude_target_audience  | array | 排除定向人群包 |
| --- age  | array | 年龄区间 详情请见定向信息查询接口 [age](queryTarget.md) |
| --- apk  | string | app安装情况 详情请见定向接口 [app](queryTarget.md) |
| --- child_age  | array | 儿童年龄区间 详情请见定向信息查询接口 [child_age](queryTarget.md) |
| --- province | array | 城市信息 [详情请见城市信息接口](queryProvince.md) |
| --- interest  | array | 行为兴趣 详情请见定向信息查询接口 [interest](queryTarget.md) |
| --- short_term_interest  | array | 收听兴趣 详情请见定向信息查询接口 [short_term_interest](queryTarget.md) |
| --- target_content_interests  | array | 内容定向 详情请见定向信息查询接口 [target_content_interests](queryTarget.md) |
| --- network  | array | 网络 内容定向 详情请见定向信息查询接口 [network](queryTarget.md) |
| --- operator  | array | 运营商 内容定向 详情请见定向信息查询接口 [operator](queryTarget.md) |
| --- platform  | array | 平台 内容定向 详情请见定向信息查询接口 [platform](queryTarget.md) |
| --- phone_brand  | array | 手机品牌 内容定向 详情请见定向信息查询接口 [phone_brand](queryTarget.md) |
| --- sex  | array | 性别 内容定向 详情请见定向信息查询接口 [sex](queryTarget.md) |



**返回示例 :**
```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": {
        "records": [
            {
                "id": 1003290,
                "ad_account_id": 201196,
                "campaign_id": 972418,
                "name": "oCPC_05_11_21:41",
                "position": "OPEN_SCREEN",
                "delivery_goal": "APPLICATION_DOWNLOAD",
                "download_mode": "DOWNLOAD_URL",
                "status": "ENABLED",
                "quick_delivery": false,
                "template_id": 0,
                "template_name": "",
                "create_time": -1285904960,
                "update_time": 0,
                "start_time": -1364008960,
                "end_time": 1889994776,
                "schedule_time": "Schedules[useSchedule=true,scheduleArray={16777215,16777215,16777215,16777215,16777215,16777215,16777215}]",
                "target_url": null,
                "download_url": null,
                "deep_link_url": null,
                "application_pack_name": null,
                "js_track_id": 0,
                "api_track_id": 527,
                "refund_status": null,
                "ad_bidding": {
                    "ad_id": 1003290,
                    "budget_type": null,
                    "budget": 0,
                    "charge_method": 0,
                    "price": 0,
                    "price_second": 1,
                    "ocpc_study_phase": "0",
                    "_ocpc": true
                },
                "ad_target": {
                    "ad_id": 1003290,
                    "target_audience": [],
                    "exclude_target_audience": [],
                    "age": [],
                    "apk": null,
                    "child_age": [],
                    "interest": [],
                    "short_term_interest": [],
                    "target_content_interests": [],
                    "network": [],
                    "operator": [],
                    "platform": [
                        "ANDROID"
                    ],
                    "phone_brand": [],
                    "province": null,
                    "sex": []
                }
            }
        ],
        "page_no": 1,
        "page_size": 20
    }
}

```

<br/>