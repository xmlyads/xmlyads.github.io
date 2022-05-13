# 枚举信息列表

**请求地址 ：** /ads-catyph/v1/system-enum/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access_token  | string | 是 | 鉴权用access_token |

**请求参数 ：**  

**传参形式 ：** Url Param

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| version  | string | 是 | [版本号](versionCode.md) |

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
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