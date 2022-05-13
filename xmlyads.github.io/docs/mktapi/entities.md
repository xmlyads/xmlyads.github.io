# Entities



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
| - query_type  | array | 否 | 查询类型，不支持多个参数，详情请见枚举 ***statement_field*** |
| - other_dimension  | array | 否 | 查询域，不支持多个参数，详情请见枚举 ***other_dimension*** |
| - time_dimension  | array | 否 | 时间维度，不支持多个参数， DAY：天 ，HOUR：小时 |
| - filter_value  | array | 否 | 筛选值，支持传入多个参数，详情请见报表搜索域接口返回值 |
| - query_end_date  | array | 否 | 结束时间，不支持多个参数 |
| - query_start_date  | array | 否 | 开始时间，不支持多个参数 |
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
        "creative_status": [
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
                "name": "ADD_WAITING",
                "desc": "新建审核中"
            },
            {
                "name": "EDIT_WAITING",
                "desc": "修改审核中"
            },
            {
                "name": "UNPASS",
                "desc": "审核未通过"
            },
            {
                "name": "PAUSED_BY_PLAN",
                "desc": "已被广告计划暂停"
            },
            {
                "name": "ALBUM_TRACK_INVALID",
                "desc": "节目无效"
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

### 11. 根据名字获取枚举类型

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


### 12. 获取定向信息

**请求地址 ：** /ads-catyph/v1/approval/launch

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：** 无

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | 状态码  0：正常 ， 其他：异常 |
| type  | string  | 返回类型 |
| msg  | string  | 返回信息 |
| data  | object | 返回枚举数组 |
| - targetName  | array | 定向枚举名 |
| -- code  | int | 定向枚举code |
| -- name  | string | 定向枚举名 |
| --- sub  | array | 定向枚举子节点数组 |
| ---- code  | int | 定向枚举子节点code |
| ---- name  | string | 定向枚举子节点名 |

**返回示例 :**

```json

{
    "status":0,
    "type":"SUCCESS",
    "msg":"success",
    "data":{
        "app":[
            {
                "code":1,
                "name":"便捷生活",
                "sub":[
                    {
                        "code":101,
                        "name":"本地生活"
                    },
                    {
                        "code":102,
                        "name":"家居装修"
                    },
                    {
                        "code":103,
                        "name":"租房买房"
                    },
                    {
                        "code":104,
                        "name":"天气日历"
                    },
                    {
                        "code":105,
                        "name":"家政"
                    },
                    {
                        "code":106,
                        "name":"电影票"
                    }
                ]
            },
            {
                "code":2,
                "name":"儿童",
                "sub":[
                    {
                        "code":201,
                        "name":"儿童教育"
                    },
                    {
                        "code":202,
                        "name":"母婴"
                    },
                    {
                        "code":203,
                        "name":"儿歌"
                    }
                ]
            },
            {
                "code":3,
                "name":"出行导航",
                "sub":[
                    {
                        "code":301,
                        "name":"用车"
                    },
                    {
                        "code":302,
                        "name":"公交地铁"
                    },
                    {
                        "code":303,
                        "name":"导航"
                    },
                    {
                        "code":304,
                        "name":"交通票务"
                    },
                    {
                        "code":305,
                        "name":"地图"
                    }
                ]
            },
            {
                "code":4,
                "name":"商务",
                "sub":[
                    {
                        "code":401,
                        "name":"效率"
                    },
                    {
                        "code":402,
                        "name":"办公软件"
                    },
                    {
                        "code":403,
                        "name":"招聘"
                    },
                    {
                        "code":404,
                        "name":"笔记"
                    },
                    {
                        "code":405,
                        "name":"邮箱"
                    }
                ]
            },
            {
                "code":5,
                "name":"实用工具",
                "sub":[
                    {
                        "code":501,
                        "name":"工具"
                    },
                    {
                        "code":502,
                        "name":"Wi-Fi"
                    },
                    {
                        "code":503,
                        "name":"安全性能"
                    },
                    {
                        "code":504,
                        "name":"浏览器"
                    },
                    {
                        "code":505,
                        "name":"输入法"
                    },
                    {
                        "code":506,
                        "name":"闹钟"
                    }
                ]
            },
            {
                "code":6,
                "name":"影音娱乐",
                "sub":[
                    {
                        "code":601,
                        "name":"视频"
                    },
                    {
                        "code":602,
                        "name":"直播"
                    },
                    {
                        "code":603,
                        "name":"音乐"
                    },
                    {
                        "code":604,
                        "name":"电台"
                    },
                    {
                        "code":605,
                        "name":"电视"
                    },
                    {
                        "code":606,
                        "name":"K歌"
                    }
                ]
            },
            {
                "code":7,
                "name":"拍摄美化",
                "sub":[
                    {
                        "code":701,
                        "name":"图像美化"
                    },
                    {
                        "code":702,
                        "name":"影音编辑"
                    },
                    {
                        "code":703,
                        "name":"拍照"
                    },
                    {
                        "code":704,
                        "name":"相册图库"
                    },
                    {
                        "code":705,
                        "name":"短视频"
                    }
                ]
            },
            {
                "code":8,
                "name":"教育",
                "sub":[
                    {
                        "code":801,
                        "name":"学习"
                    },
                    {
                        "code":802,
                        "name":"备考"
                    },
                    {
                        "code":803,
                        "name":"英文"
                    },
                    {
                        "code":804,
                        "name":"翻译"
                    }
                ]
            },
            {
                "code":9,
                "name":"新闻阅读",
                "sub":[
                    {
                        "code":901,
                        "name":"分类信息"
                    },
                    {
                        "code":902,
                        "name":"电子书"
                    },
                    {
                        "code":903,
                        "name":"新闻"
                    },
                    {
                        "code":904,
                        "name":"体育"
                    },
                    {
                        "code":905,
                        "name":"杂志"
                    },
                    {
                        "code":906,
                        "name":"有声读物"
                    },
                    {
                        "code":907,
                        "name":"动漫"
                    },
                    {
                        "code":908,
                        "name":"幽默"
                    }
                ]
            },
            {
                "code":10,
                "name":"旅游住宿",
                "sub":[
                    {
                        "code":1001,
                        "name":"旅游"
                    },
                    {
                        "code":1002,
                        "name":"住宿"
                    },
                    {
                        "code":1003,
                        "name":"行程助手"
                    }
                ]
            },
            {
                "code":11,
                "name":"汽车",
                "sub":[
                    {
                        "code":1101,
                        "name":"养车"
                    },
                    {
                        "code":1102,
                        "name":"汽车资讯"
                    },
                    {
                        "code":1103,
                        "name":"驾考"
                    },
                    {
                        "code":1104,
                        "name":"违章查询"
                    }
                ]
            },
            {
                "code":12,
                "name":"社交通讯",
                "sub":[
                    {
                        "code":1201,
                        "name":"社区"
                    },
                    {
                        "code":1202,
                        "name":"聊天"
                    },
                    {
                        "code":1203,
                        "name":"婚恋"
                    },
                    {
                        "code":1204,
                        "name":"通讯"
                    }
                ]
            },
            {
                "code":13,
                "name":"美食",
                "sub":[
                    {
                        "code":1301,
                        "name":"外卖"
                    },
                    {
                        "code":1302,
                        "name":"生鲜"
                    },
                    {
                        "code":1303,
                        "name":"餐饮"
                    },
                    {
                        "code":1304,
                        "name":"菜谱"
                    }
                ]
            },
            {
                "code":14,
                "name":"购物比价",
                "sub":[
                    {
                        "code":1401,
                        "name":"商城"
                    },
                    {
                        "code":1402,
                        "name":"优惠"
                    },
                    {
                        "code":1403,
                        "name":"导购"
                    },
                    {
                        "code":1404,
                        "name":"团购"
                    },
                    {
                        "code":1405,
                        "name":"海淘"
                    },
                    {
                        "code":1406,
                        "name":"快递"
                    }
                ]
            },
            {
                "code":15,
                "name":"运动健康",
                "sub":[
                    {
                        "code":1501,
                        "name":"健康"
                    },
                    {
                        "code":1502,
                        "name":"医疗"
                    },
                    {
                        "code":1503,
                        "name":"运动"
                    },
                    {
                        "code":1504,
                        "name":"养生"
                    }
                ]
            },
            {
                "code":16,
                "name":"金融理财",
                "sub":[
                    {
                        "code":1601,
                        "name":"银行"
                    },
                    {
                        "code":1602,
                        "name":"理财"
                    },
                    {
                        "code":1603,
                        "name":"股票基金"
                    },
                    {
                        "code":1604,
                        "name":"贷款"
                    },
                    {
                        "code":1605,
                        "name":"记账"
                    }
                ]
            },
            {
                "code":17,
                "name":"游戏-休闲益智",
                "sub":[
                    {
                        "code":1701,
                        "name":"休闲"
                    },
                    {
                        "code":1702,
                        "name":"益智"
                    },
                    {
                        "code":1703,
                        "name":"解谜"
                    },
                    {
                        "code":1704,
                        "name":"消除"
                    },
                    {
                        "code":1705,
                        "name":"IO"
                    },
                    {
                        "code":1706,
                        "name":"音乐节奏"
                    }
                ]
            },
            {
                "code":18,
                "name":"游戏-体育竞速",
                "sub":[
                    {
                        "code":1801,
                        "name":"赛车"
                    },
                    {
                        "code":1802,
                        "name":"足球"
                    },
                    {
                        "code":1803,
                        "name":"篮球"
                    },
                    {
                        "code":1804,
                        "name":"体育运动"
                    }
                ]
            },
            {
                "code":19,
                "name":"游戏-动作射击",
                "sub":[
                    {
                        "code":1901,
                        "name":"射击"
                    },
                    {
                        "code":1902,
                        "name":"格斗"
                    },
                    {
                        "code":1903,
                        "name":"跑酷"
                    },
                    {
                        "code":1904,
                        "name":"打飞机"
                    }
                ]
            },
            {
                "code":20,
                "name":"游戏-棋牌桌游",
                "sub":[
                    {
                        "code":2001,
                        "name":"捕鱼"
                    },
                    {
                        "code":2002,
                        "name":"纸牌"
                    },
                    {
                        "code":2003,
                        "name":"麻将"
                    },
                    {
                        "code":2004,
                        "name":"斗地主"
                    },
                    {
                        "code":2005,
                        "name":"桌游与棋类"
                    }
                ]
            },
            {
                "code":21,
                "name":"游戏-经营策略",
                "sub":[
                    {
                        "code":2101,
                        "name":"经营"
                    },
                    {
                        "code":2102,
                        "name":"养成"
                    },
                    {
                        "code":2103,
                        "name":"古代谋略"
                    },
                    {
                        "code":2104,
                        "name":"塔防"
                    },
                    {
                        "code":2105,
                        "name":"现代战略"
                    },
                    {
                        "code":2106,
                        "name":"MOBA"
                    }
                ]
            },
            {
                "code":22,
                "name":"游戏-角色扮演",
                "sub":[
                    {
                        "code":2201,
                        "name":"卡牌"
                    },
                    {
                        "code":2202,
                        "name":"仙侠"
                    },
                    {
                        "code":2203,
                        "name":"放置挂机"
                    },
                    {
                        "code":2204,
                        "name":"冒险"
                    },
                    {
                        "code":2205,
                        "name":"回合制"
                    },
                    {
                        "code":2206,
                        "name":"传奇"
                    },
                    {
                        "code":2207,
                        "name":"动作"
                    },
                    {
                        "code":2208,
                        "name":"多人在线"
                    },
                    {
                        "code":2209,
                        "name":"魔幻"
                    },
                    {
                        "code":2210,
                        "name":"武侠"
                    },
                    {
                        "code":2211,
                        "name":"生存"
                    }
                ]
            }
        ],
        "interest":[
            {
                "code":101,
                "name":"儿童",
                "sub":[
                    {
                        "code":10101,
                        "name":"儿童"
                    }
                ]
            },
            {
                "code":102,
                "name":"少儿教育",
                "sub":[
                    {
                        "code":10201,
                        "name":"少儿教育"
                    }
                ]
            },
            {
                "code":103,
                "name":"新闻资讯",
                "sub":[
                    {
                        "code":10301,
                        "name":"新闻资讯"
                    }
                ]
            },
            {
                "code":104,
                "name":"相声评书",
                "sub":[
                    {
                        "code":10401,
                        "name":"相声评书"
                    }
                ]
            },
            {
                "code":105,
                "name":"音乐",
                "sub":[
                    {
                        "code":10501,
                        "name":"音乐"
                    }
                ]
            },
            {
                "code":106,
                "name":"职业培训",
                "sub":[
                    {
                        "code":10601,
                        "name":"职业培训"
                    }
                ]
            },
            {
                "code":107,
                "name":"人文",
                "sub":[
                    {
                        "code":10701,
                        "name":"人文"
                    }
                ]
            },
            {
                "code":108,
                "name":"明星八卦",
                "sub":[
                    {
                        "code":10801,
                        "name":"明星八卦"
                    }
                ]
            },
            {
                "code":109,
                "name":"历史",
                "sub":[
                    {
                        "code":10901,
                        "name":"历史"
                    }
                ]
            },
            {
                "code":110,
                "name":"成人英语",
                "sub":[
                    {
                        "code":11001,
                        "name":"成人英语"
                    }
                ]
            },
            {
                "code":111,
                "name":"金融理财",
                "sub":[
                    {
                        "code":11101,
                        "name":"金融理财"
                    }
                ]
            },
            {
                "code":112,
                "name":"情感生活",
                "sub":[
                    {
                        "code":11201,
                        "name":"情感生活"
                    }
                ]
            },
            {
                "code":113,
                "name":"健康养生",
                "sub":[
                    {
                        "code":11301,
                        "name":"健康养生"
                    }
                ]
            },
            {
                "code":114,
                "name":"IT科技",
                "sub":[
                    {
                        "code":11401,
                        "name":"IT科技"
                    }
                ]
            },
            {
                "code":115,
                "name":"戏曲",
                "sub":[
                    {
                        "code":11501,
                        "name":"戏曲"
                    }
                ]
            },
            {
                "code":116,
                "name":"儿童英语",
                "sub":[
                    {
                        "code":11601,
                        "name":"儿童英语"
                    }
                ]
            },
            {
                "code":117,
                "name":"二次元",
                "sub":[
                    {
                        "code":11701,
                        "name":"二次元"
                    }
                ]
            },
            {
                "code":118,
                "name":"影视",
                "sub":[
                    {
                        "code":11801,
                        "name":"影视"
                    }
                ]
            },
            {
                "code":119,
                "name":"有声书",
                "sub":[
                    {
                        "code":11901,
                        "name":"悬疑"
                    },
                    {
                        "code":11902,
                        "name":"言情"
                    },
                    {
                        "code":11903,
                        "name":"都市"
                    },
                    {
                        "code":11904,
                        "name":"武侠"
                    },
                    {
                        "code":11905,
                        "name":"幻想"
                    },
                    {
                        "code":11906,
                        "name":"文学"
                    },
                    {
                        "code":11907,
                        "name":"历史"
                    },
                    {
                        "code":11908,
                        "name":"经典"
                    },
                    {
                        "code":11909,
                        "name":"社科"
                    },
                    {
                        "code":11910,
                        "name":"商业"
                    },
                    {
                        "code":11911,
                        "name":"童书"
                    },
                    {
                        "code":11912,
                        "name":"励志"
                    },
                    {
                        "code":11913,
                        "name":"官场商战"
                    },
                    {
                        "code":11914,
                        "name":"教材"
                    },
                    {
                        "code":11915,
                        "name":"生活"
                    }
                ]
            }
        ],
        "content":[
            {
                "code":1,
                "name":"资讯",
                "sub":[
                    {
                        "code":101,
                        "name":"体育资讯"
                    },
                    {
                        "code":102,
                        "name":"军事资讯"
                    },
                    {
                        "code":103,
                        "name":"国内资讯"
                    },
                    {
                        "code":104,
                        "name":"国际资讯"
                    },
                    {
                        "code":105,
                        "name":"娱乐资讯"
                    },
                    {
                        "code":106,
                        "name":"文化资讯"
                    },
                    {
                        "code":107,
                        "name":"时政要闻"
                    },
                    {
                        "code":108,
                        "name":"民生资讯"
                    },
                    {
                        "code":109,
                        "name":"科技资讯"
                    },
                    {
                        "code":110,
                        "name":"访谈"
                    },
                    {
                        "code":111,
                        "name":"财经资讯"
                    }
                ]
            },
            {
                "code":2,
                "name":"音乐",
                "sub":[
                    {
                        "code":201,
                        "name":"3D电音"
                    },
                    {
                        "code":202,
                        "name":"乡村"
                    },
                    {
                        "code":203,
                        "name":"佛乐"
                    },
                    {
                        "code":204,
                        "name":"催眠"
                    },
                    {
                        "code":205,
                        "name":"动感电音"
                    },
                    {
                        "code":206,
                        "name":"华语"
                    },
                    {
                        "code":207,
                        "name":"古典"
                    },
                    {
                        "code":208,
                        "name":"哈萨克语"
                    },
                    {
                        "code":209,
                        "name":"影视原声"
                    },
                    {
                        "code":210,
                        "name":"怀旧"
                    },
                    {
                        "code":211,
                        "name":"日韩"
                    },
                    {
                        "code":212,
                        "name":"欧美"
                    },
                    {
                        "code":213,
                        "name":"流行"
                    },
                    {
                        "code":214,
                        "name":"游戏动漫"
                    },
                    {
                        "code":215,
                        "name":"爵士"
                    },
                    {
                        "code":216,
                        "name":"电台"
                    },
                    {
                        "code":217,
                        "name":"粤语"
                    },
                    {
                        "code":218,
                        "name":"翻唱"
                    },
                    {
                        "code":219,
                        "name":"自然"
                    },
                    {
                        "code":220,
                        "name":"轻音乐"
                    },
                    {
                        "code":221,
                        "name":"铃声"
                    }
                ]
            },
            {
                "code":3,
                "name":"有声书",
                "sub":[
                    {
                        "code":301,
                        "name":"历史"
                    },
                    {
                        "code":302,
                        "name":"官场商战"
                    },
                    {
                        "code":303,
                        "name":"幻想"
                    },
                    {
                        "code":304,
                        "name":"悬疑"
                    },
                    {
                        "code":305,
                        "name":"文学"
                    },
                    {
                        "code":306,
                        "name":"武侠"
                    },
                    {
                        "code":307,
                        "name":"社科"
                    },
                    {
                        "code":308,
                        "name":"商业"
                    },
                    {
                        "code":309,
                        "name":"言情"
                    },
                    {
                        "code":310,
                        "name":"都市"
                    },
                    {
                        "code":312,
                        "name":"经典"
                    },
                    {
                        "code":313,
                        "name":"励志"
                    },
                    {
                        "code":314,
                        "name":"童书"
                    },
                    {
                        "code":315,
                        "name":"生活"
                    },
                    {
                        "code":316,
                        "name":"教材"
                    },
                    {
                        "code":317,
                        "name":"英文原版"
                    }
                ]
            },
            {
                "code":4,
                "name":"娱乐",
                "sub":[
                    {
                        "code":401,
                        "name":"八卦"
                    },
                    {
                        "code":402,
                        "name":"原声电视剧"
                    },
                    {
                        "code":403,
                        "name":"地方脱口秀"
                    },
                    {
                        "code":404,
                        "name":"星座"
                    },
                    {
                        "code":405,
                        "name":"段子"
                    },
                    {
                        "code":406,
                        "name":"经典动漫原声"
                    },
                    {
                        "code":407,
                        "name":"经典电影原声"
                    },
                    {
                        "code":408,
                        "name":"综艺"
                    },
                    {
                        "code":409,
                        "name":"脱口秀"
                    },
                    {
                        "code":410,
                        "name":"访谈"
                    },
                    {
                        "code":411,
                        "name":"鬼故事"
                    }
                ]
            },
            {
                "code":5,
                "name":"外语",
                "sub":[
                    {
                        "code":501,
                        "name":"俄语"
                    },
                    {
                        "code":502,
                        "name":"其他语言"
                    },
                    {
                        "code":503,
                        "name":"口语"
                    },
                    {
                        "code":504,
                        "name":"名校公开课"
                    },
                    {
                        "code":505,
                        "name":"商务英语"
                    },
                    {
                        "code":506,
                        "name":"实用英语"
                    },
                    {
                        "code":507,
                        "name":"少儿英语"
                    },
                    {
                        "code":508,
                        "name":"影视原声"
                    },
                    {
                        "code":509,
                        "name":"德语"
                    },
                    {
                        "code":510,
                        "name":"意大利语"
                    },
                    {
                        "code":511,
                        "name":"日语"
                    },
                    {
                        "code":512,
                        "name":"法语"
                    },
                    {
                        "code":513,
                        "name":"泰语"
                    },
                    {
                        "code":514,
                        "name":"英文名著"
                    },
                    {
                        "code":515,
                        "name":"英语初级"
                    },
                    {
                        "code":516,
                        "name":"英语发音"
                    },
                    {
                        "code":517,
                        "name":"英语新闻"
                    },
                    {
                        "code":518,
                        "name":"英语演讲"
                    },
                    {
                        "code":519,
                        "name":"英语考试"
                    },
                    {
                        "code":520,
                        "name":"英语脱口秀"
                    },
                    {
                        "code":521,
                        "name":"英语词汇"
                    },
                    {
                        "code":522,
                        "name":"英语读物"
                    },
                    {
                        "code":523,
                        "name":"葡萄牙语"
                    },
                    {
                        "code":524,
                        "name":"西班牙语"
                    },
                    {
                        "code":525,
                        "name":"韩语"
                    }
                ]
            },
            {
                "code":6,
                "name":"儿童",
                "sub":[
                    {
                        "code":601,
                        "name":"中小学必备"
                    },
                    {
                        "code":602,
                        "name":"亲子学堂"
                    },
                    {
                        "code":603,
                        "name":"儿歌大全"
                    },
                    {
                        "code":604,
                        "name":"卡通动画"
                    },
                    {
                        "code":605,
                        "name":"国学启蒙"
                    },
                    {
                        "code":606,
                        "name":"百科知识"
                    },
                    {
                        "code":607,
                        "name":"童话故事"
                    },
                    {
                        "code":608,
                        "name":"胎教"
                    },
                    {
                        "code":609,
                        "name":"英文儿歌"
                    }
                ]
            },
            {
                "code":39,
                "name":"人文",
                "sub":[
                    {
                        "code":3901,
                        "name":"佛学心灵"
                    },
                    {
                        "code":3902,
                        "name":"古诗词"
                    },
                    {
                        "code":3903,
                        "name":"启蒙"
                    },
                    {
                        "code":3904,
                        "name":"国学名著"
                    },
                    {
                        "code":3905,
                        "name":"国学经典"
                    },
                    {
                        "code":3906,
                        "name":"现代诗"
                    },
                    {
                        "code":3907,
                        "name":"纪实档案"
                    },
                    {
                        "code":3908,
                        "name":"艺术收藏"
                    }
                ]
            },
            {
                "code":7,
                "name":"健康养生",
                "sub":[
                    {
                        "code":701,
                        "name":"两性"
                    },
                    {
                        "code":702,
                        "name":"中医养生"
                    },
                    {
                        "code":703,
                        "name":"健康"
                    },
                    {
                        "code":704,
                        "name":"催眠"
                    },
                    {
                        "code":705,
                        "name":"心理"
                    },
                    {
                        "code":706,
                        "name":"生活家"
                    },
                    {
                        "code":707,
                        "name":"美容"
                    },
                    {
                        "code":708,
                        "name":"美食"
                    },
                    {
                        "code":709,
                        "name":"运动健身"
                    }
                ]
            },
            {
                "code":8,
                "name":"商业财经",
                "sub":[
                    {
                        "code":801,
                        "name":"创业"
                    },
                    {
                        "code":802,
                        "name":"商业评论"
                    },
                    {
                        "code":803,
                        "name":"房地产"
                    },
                    {
                        "code":804,
                        "name":"消费指南"
                    },
                    {
                        "code":805,
                        "name":"理财指南"
                    },
                    {
                        "code":806,
                        "name":"股指期货"
                    }
                ]
            },
            {
                "code":9,
                "name":"历史",
                "sub":[
                    {
                        "code":901,
                        "name":"一战二战"
                    },
                    {
                        "code":902,
                        "name":"三国"
                    },
                    {
                        "code":903,
                        "name":"世界史"
                    },
                    {
                        "code":904,
                        "name":"中国史"
                    },
                    {
                        "code":907,
                        "name":"名人传记"
                    },
                    {
                        "code":908,
                        "name":"国学启蒙"
                    },
                    {
                        "code":910,
                        "name":"宋元"
                    },
                    {
                        "code":911,
                        "name":"战争史"
                    },
                    {
                        "code":912,
                        "name":"明清"
                    },
                    {
                        "code":913,
                        "name":"春秋战国"
                    },
                    {
                        "code":914,
                        "name":"民国"
                    },
                    {
                        "code":916,
                        "name":"秦汉"
                    },
                    {
                        "code":917,
                        "name":"纪实档案"
                    },
                    {
                        "code":919,
                        "name":"读书会"
                    },
                    {
                        "code":920,
                        "name":"近代史"
                    },
                    {
                        "code":921,
                        "name":"隋唐"
                    },
                    {
                        "code":922,
                        "name":"魏晋"
                    }
                ]
            },
            {
                "code":10,
                "name":"情感生活",
                "sub":[
                    {
                        "code":1001,
                        "name":"两性心理"
                    },
                    {
                        "code":1002,
                        "name":"夜谈"
                    },
                    {
                        "code":1003,
                        "name":"女性心理"
                    },
                    {
                        "code":1004,
                        "name":"婚姻心理"
                    },
                    {
                        "code":1005,
                        "name":"情感励志"
                    },
                    {
                        "code":1006,
                        "name":"情感故事"
                    },
                    {
                        "code":1007,
                        "name":"文艺青年"
                    },
                    {
                        "code":1008,
                        "name":"星座爱情"
                    },
                    {
                        "code":1009,
                        "name":"治愈系"
                    },
                    {
                        "code":1010,
                        "name":"浪漫爱情"
                    },
                    {
                        "code":1011,
                        "name":"脱单技巧"
                    },
                    {
                        "code":1012,
                        "name":"青春怀旧"
                    }
                ]
            },
            {
                "code":12,
                "name":"相声评书",
                "sub":[
                    {
                        "code":1201,
                        "name":"其他评书"
                    },
                    {
                        "code":1202,
                        "name":"刘兰芳"
                    },
                    {
                        "code":1203,
                        "name":"单田芳"
                    },
                    {
                        "code":1204,
                        "name":"岳云鹏"
                    },
                    {
                        "code":1205,
                        "name":"张少佐"
                    },
                    {
                        "code":1206,
                        "name":"曹云金"
                    },
                    {
                        "code":1207,
                        "name":"王玥波"
                    },
                    {
                        "code":1208,
                        "name":"田连元"
                    },
                    {
                        "code":1209,
                        "name":"相声江湖"
                    },
                    {
                        "code":1210,
                        "name":"袁阔成"
                    },
                    {
                        "code":1211,
                        "name":"赵本山"
                    },
                    {
                        "code":1212,
                        "name":"连丽如"
                    },
                    {
                        "code":1213,
                        "name":"郭德纲"
                    },
                    {
                        "code":1214,
                        "name":"青曲茶馆"
                    },
                    {
                        "code":1215,
                        "name":"马三立"
                    },
                    {
                        "code":1216,
                        "name":"马季"
                    },
                    {
                        "code":1217,
                        "name":"鼎泰茶社"
                    },
                    {
                        "code":1218,
                        "name":"鼓曲大全"
                    }
                ]
            },
            {
                "code":13,
                "name":"教育培训",
                "sub":[
                    {
                        "code":1301,
                        "name":"互联网"
                    },
                    {
                        "code":1302,
                        "name":"会计金融"
                    },
                    {
                        "code":1303,
                        "name":"儿童教育"
                    },
                    {
                        "code":1304,
                        "name":"公务员"
                    },
                    {
                        "code":1305,
                        "name":"初中教育"
                    },
                    {
                        "code":1306,
                        "name":"励志成功学"
                    },
                    {
                        "code":1307,
                        "name":"名人"
                    },
                    {
                        "code":1308,
                        "name":"听党课"
                    },
                    {
                        "code":1309,
                        "name":"国学"
                    },
                    {
                        "code":1310,
                        "name":"宗教公开课"
                    },
                    {
                        "code":1311,
                        "name":"家庭教育"
                    },
                    {
                        "code":1312,
                        "name":"小学教育"
                    },
                    {
                        "code":1313,
                        "name":"心理"
                    },
                    {
                        "code":1314,
                        "name":"新媒体"
                    },
                    {
                        "code":1315,
                        "name":"法律"
                    },
                    {
                        "code":1316,
                        "name":"生活百科"
                    },
                    {
                        "code":1317,
                        "name":"留学"
                    },
                    {
                        "code":1318,
                        "name":"研习社"
                    },
                    {
                        "code":1319,
                        "name":"管理"
                    },
                    {
                        "code":1320,
                        "name":"职业技能"
                    },
                    {
                        "code":1321,
                        "name":"职场"
                    },
                    {
                        "code":1322,
                        "name":"营销"
                    },
                    {
                        "code":1323,
                        "name":"语言"
                    },
                    {
                        "code":1324,
                        "name":"高中教育"
                    },
                    {
                        "code":1325,
                        "name":"高考"
                    }
                ]
            },
            {
                "code":14,
                "name":"百家讲坛",
                "sub":[
                    {
                        "code":1401,
                        "name":"历史传奇"
                    },
                    {
                        "code":1402,
                        "name":"名师经典"
                    },
                    {
                        "code":1403,
                        "name":"国学经典"
                    },
                    {
                        "code":1404,
                        "name":"帝王将相"
                    },
                    {
                        "code":1405,
                        "name":"风云人物"
                    }
                ]
            },
            {
                "code":15,
                "name":"广播剧",
                "sub":[
                    {
                        "code":1501,
                        "name":"剧情歌"
                    },
                    {
                        "code":1502,
                        "name":"古风剧"
                    },
                    {
                        "code":1503,
                        "name":"现代剧"
                    },
                    {
                        "code":1504,
                        "name":"百合剧"
                    },
                    {
                        "code":1505,
                        "name":"耽美剧"
                    },
                    {
                        "code":1506,
                        "name":"言情剧"
                    }
                ]
            },
            {
                "code":16,
                "name":"戏曲",
                "sub":[
                    {
                        "code":1601,
                        "name":"其他地方戏"
                    },
                    {
                        "code":1602,
                        "name":"典雅昆曲"
                    },
                    {
                        "code":1603,
                        "name":"华美京剧"
                    },
                    {
                        "code":1604,
                        "name":"圆润粤剧"
                    },
                    {
                        "code":1605,
                        "name":"多彩沪剧"
                    },
                    {
                        "code":1606,
                        "name":"嬉笑怒骂二人转"
                    },
                    {
                        "code":1607,
                        "name":"明快黄梅"
                    },
                    {
                        "code":1608,
                        "name":"活泼评剧"
                    },
                    {
                        "code":1609,
                        "name":"温婉越剧"
                    },
                    {
                        "code":1610,
                        "name":"质朴豫剧"
                    }
                ]
            },
            {
                "code":17,
                "name":"电台",
                "sub":[
                    {
                        "code":1701,
                        "name":"交通台"
                    },
                    {
                        "code":1702,
                        "name":"体育台"
                    },
                    {
                        "code":1703,
                        "name":"外语台"
                    },
                    {
                        "code":1704,
                        "name":"故事台"
                    },
                    {
                        "code":1705,
                        "name":"文艺台"
                    },
                    {
                        "code":1706,
                        "name":"新闻台"
                    },
                    {
                        "code":1707,
                        "name":"旅游台"
                    },
                    {
                        "code":1708,
                        "name":"曲艺台"
                    },
                    {
                        "code":1709,
                        "name":"校园台"
                    },
                    {
                        "code":1710,
                        "name":"生活台"
                    },
                    {
                        "code":1711,
                        "name":"经济台"
                    },
                    {
                        "code":1712,
                        "name":"综合台"
                    },
                    {
                        "code":1713,
                        "name":"都市台"
                    },
                    {
                        "code":1714,
                        "name":"音乐台"
                    }
                ]
            },
            {
                "code":18,
                "name":"IT科技",
                "sub":[
                    {
                        "code":1801,
                        "name":"互联网+"
                    },
                    {
                        "code":1802,
                        "name":"创客"
                    },
                    {
                        "code":1803,
                        "name":"大数据"
                    },
                    {
                        "code":1804,
                        "name":"数码"
                    },
                    {
                        "code":1805,
                        "name":"智能"
                    },
                    {
                        "code":1806,
                        "name":"有料"
                    },
                    {
                        "code":1807,
                        "name":"科学"
                    }
                ]
            },
            {
                "code":20,
                "name":"校园",
                "sub":[
                    {
                        "code":2001,
                        "name":"上海校园"
                    },
                    {
                        "code":2002,
                        "name":"北京校园"
                    },
                    {
                        "code":2003,
                        "name":"卧谈会"
                    },
                    {
                        "code":2004,
                        "name":"天津校园"
                    },
                    {
                        "code":2005,
                        "name":"小编推荐"
                    },
                    {
                        "code":2006,
                        "name":"新技能get"
                    },
                    {
                        "code":2007,
                        "name":"江苏校园"
                    }
                ]
            },
            {
                "code":21,
                "name":"汽车",
                "sub":[
                    {
                        "code":2101,
                        "name":"摩托车"
                    },
                    {
                        "code":2102,
                        "name":"汽车脱口秀"
                    },
                    {
                        "code":2103,
                        "name":"热点汇"
                    },
                    {
                        "code":2104,
                        "name":"玩车"
                    },
                    {
                        "code":2105,
                        "name":"购车选车"
                    }
                ]
            },
            {
                "code":22,
                "name":"旅游",
                "sub":[
                    {
                        "code":2201,
                        "name":"地方人文"
                    },
                    {
                        "code":2202,
                        "name":"旅游大玩家"
                    },
                    {
                        "code":2203,
                        "name":"旅游攻略"
                    },
                    {
                        "code":2204,
                        "name":"旅途心情"
                    },
                    {
                        "code":2205,
                        "name":"景区讲解"
                    },
                    {
                        "code":2206,
                        "name":"漂洋过海"
                    },
                    {
                        "code":2207,
                        "name":"走遍中国"
                    }
                ]
            },
            {
                "code":23,
                "name":"电影",
                "sub":[
                    {
                        "code":2301,
                        "name":"原声记忆"
                    },
                    {
                        "code":2302,
                        "name":"大话影人"
                    },
                    {
                        "code":2303,
                        "name":"影评地带"
                    }
                ]
            },
            {
                "code":24,
                "name":"动漫游戏",
                "sub":[
                    {
                        "code":2401,
                        "name":"ACG广播"
                    },
                    {
                        "code":2402,
                        "name":"ACG脱口秀"
                    },
                    {
                        "code":2403,
                        "name":"ACG资讯"
                    },
                    {
                        "code":2404,
                        "name":"ACG音乐"
                    },
                    {
                        "code":2405,
                        "name":"CV配音"
                    },
                    {
                        "code":2406,
                        "name":"二次元大本营"
                    },
                    {
                        "code":2407,
                        "name":"古风"
                    },
                    {
                        "code":2408,
                        "name":"有声轻小说"
                    },
                    {
                        "code":2409,
                        "name":"英雄联盟"
                    },
                    {
                        "code":2410,
                        "name":"鬼畜娱乐"
                    },
                    {
                        "code":2411,
                        "name":"魔兽世界"
                    }
                ]
            },
            {
                "code":92,
                "name":"少儿教育",
                "sub":[
                    {
                        "code":92,
                        "name":"少儿教育"
                    }
                ]
            },
            {
                "code":31,
                "name":"时尚生活",
                "sub":[
                    {
                        "code":3101,
                        "name":"生活家"
                    },
                    {
                        "code":3102,
                        "name":"美容"
                    },
                    {
                        "code":3103,
                        "name":"美食"
                    },
                    {
                        "code":3104,
                        "name":"萌宠"
                    },
                    {
                        "code":3105,
                        "name":"运动"
                    }
                ]
            }
        ]
    }
}

```

<br/>

