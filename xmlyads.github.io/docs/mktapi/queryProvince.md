# 获取地域信息

定向信息查询

**请求地址 ：** /ads-catyph/v1/system-enum/province/get

**请求方式 ：** GET

**请求头参数 ：**

|  字段名   | 类型  | 是否必须 | 描述 |
|  ----  | ---- | ---- | ---- | 
| access-token  | string | 是 | 鉴权用access-token |

**请求参数 ：** 无

**返回字段释义：**

|  字段名   | 类型  | 描述 |
|  ----  | ---- | ---- | 
| status  | int  | [状态码](errorCode.md#错误码和描述)  0：正常 ， 其他：异常 |
| type  | string  | [返回类型](errorCode.md#错误码和描述) |
| msg  | string  | [返回信息](errorCode.md#错误码和描述) |
| data  | array | 返回城市数组 |
| - code  | int | 城市code |
| - name  | string | 城市名 |
| - desc  | string | 定向枚举描述 |
| - sub  | array | 子级城市名 |
| -- code  | int | 城市code |
| -- name  | string | 城市名 |

**返回示例 :**

```json

{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": [
        {
            "code": 1,
            "name": "北京",
            "sub": [
                {
                    "code": 110000,
                    "name": "北京"
                }
            ]
        },
        {
            "code": 2,
            "name": "天津",
            "sub": [
                {
                    "code": 120000,
                    "name": "天津"
                }
            ]
        },
        {
            "code": 3,
            "name": "上海",
            "sub": [
                {
                    "code": 310000,
                    "name": "上海"
                }
            ]
        },
        {
            "code": 4,
            "name": "重庆",
            "sub": [
                {
                    "code": 500000,
                    "name": "重庆"
                }
            ]
        },
        {
            "code": 5,
            "name": "河北",
            "sub": [
                {
                    "code": 88,
                    "name": "石家庄市"
                },
                {
                    "code": 89,
                    "name": "唐山市"
                },
                {
                    "code": 90,
                    "name": "秦皇岛市"
                },
                {
                    "code": 91,
                    "name": "邯郸市"
                },
                {
                    "code": 92,
                    "name": "邢台市"
                },
                {
                    "code": 93,
                    "name": "保定市"
                },
                {
                    "code": 94,
                    "name": "张家口市"
                },
                {
                    "code": 95,
                    "name": "承德市"
                },
                {
                    "code": 96,
                    "name": "沧州市"
                },
                {
                    "code": 97,
                    "name": "廊坊市"
                },
                {
                    "code": 98,
                    "name": "衡水市"
                }
            ]
        },
        {
            "code": 6,
            "name": "山西",
            "sub": [
                {
                    "code": 99,
                    "name": "太原市"
                },
                {
                    "code": 100,
                    "name": "大同市"
                },
                {
                    "code": 101,
                    "name": "阳泉市"
                },
                {
                    "code": 102,
                    "name": "长治市"
                },
                {
                    "code": 103,
                    "name": "晋城市"
                },
                {
                    "code": 104,
                    "name": "朔州市"
                },
                {
                    "code": 105,
                    "name": "晋中市"
                },
                {
                    "code": 106,
                    "name": "运城市"
                },
                {
                    "code": 107,
                    "name": "忻州市"
                },
                {
                    "code": 108,
                    "name": "临汾市"
                },
                {
                    "code": 109,
                    "name": "吕梁市"
                }
            ]
        },
        {
            "code": 7,
            "name": "台湾",
            "sub": [
                {
                    "code": 472,
                    "name": "台湾"
                }
            ]
        },
        {
            "code": 8,
            "name": "辽宁",
            "sub": [
                {
                    "code": 134,
                    "name": "沈阳市"
                },
                {
                    "code": 135,
                    "name": "大连市"
                },
                {
                    "code": 136,
                    "name": "鞍山市"
                },
                {
                    "code": 137,
                    "name": "抚顺市"
                },
                {
                    "code": 138,
                    "name": "本溪市"
                },
                {
                    "code": 139,
                    "name": "丹东市"
                },
                {
                    "code": 140,
                    "name": "锦州市"
                },
                {
                    "code": 141,
                    "name": "营口市"
                },
                {
                    "code": 142,
                    "name": "阜新市"
                },
                {
                    "code": 143,
                    "name": "辽阳市"
                },
                {
                    "code": 144,
                    "name": "盘锦市"
                },
                {
                    "code": 145,
                    "name": "铁岭市"
                },
                {
                    "code": 146,
                    "name": "朝阳市"
                },
                {
                    "code": 147,
                    "name": "葫芦岛市"
                }
            ]
        },
        {
            "code": 9,
            "name": "吉林",
            "sub": [
                {
                    "code": 148,
                    "name": "长春市"
                },
                {
                    "code": 149,
                    "name": "吉林市"
                },
                {
                    "code": 150,
                    "name": "四平市"
                },
                {
                    "code": 151,
                    "name": "辽源市"
                },
                {
                    "code": 152,
                    "name": "通化市"
                },
                {
                    "code": 153,
                    "name": "白山市"
                },
                {
                    "code": 154,
                    "name": "松原市"
                },
                {
                    "code": 155,
                    "name": "白城市"
                },
                {
                    "code": 156,
                    "name": "延边朝鲜族自治州"
                }
            ]
        },
        {
            "code": 10,
            "name": "黑龙江",
            "sub": [
                {
                    "code": 157,
                    "name": "哈尔滨市"
                },
                {
                    "code": 158,
                    "name": "齐齐哈尔市"
                },
                {
                    "code": 159,
                    "name": "鹤岗市"
                },
                {
                    "code": 160,
                    "name": "双鸭山市"
                },
                {
                    "code": 161,
                    "name": "鸡西市"
                },
                {
                    "code": 162,
                    "name": "大庆市"
                },
                {
                    "code": 163,
                    "name": "伊春市"
                },
                {
                    "code": 164,
                    "name": "牡丹江市"
                },
                {
                    "code": 165,
                    "name": "佳木斯市"
                },
                {
                    "code": 166,
                    "name": "七台河市"
                },
                {
                    "code": 167,
                    "name": "黑河市"
                },
                {
                    "code": 168,
                    "name": "绥化市"
                },
                {
                    "code": 169,
                    "name": "大兴安岭地区"
                }
            ]
        },
        {
            "code": 11,
            "name": "江苏",
            "sub": [
                {
                    "code": 170,
                    "name": "南京市"
                },
                {
                    "code": 171,
                    "name": "无锡市"
                },
                {
                    "code": 172,
                    "name": "徐州市"
                },
                {
                    "code": 173,
                    "name": "常州市"
                },
                {
                    "code": 174,
                    "name": "苏州市"
                },
                {
                    "code": 175,
                    "name": "南通市"
                },
                {
                    "code": 176,
                    "name": "连云港市"
                },
                {
                    "code": 177,
                    "name": "淮安市"
                },
                {
                    "code": 178,
                    "name": "盐城市"
                },
                {
                    "code": 179,
                    "name": "扬州市"
                },
                {
                    "code": 180,
                    "name": "镇江市"
                },
                {
                    "code": 181,
                    "name": "泰州市"
                },
                {
                    "code": 182,
                    "name": "宿迁市"
                }
            ]
        },
        {
            "code": 12,
            "name": "浙江",
            "sub": [
                {
                    "code": 183,
                    "name": "杭州市"
                },
                {
                    "code": 184,
                    "name": "宁波市"
                },
                {
                    "code": 185,
                    "name": "温州市"
                },
                {
                    "code": 186,
                    "name": "嘉兴市"
                },
                {
                    "code": 187,
                    "name": "湖州市"
                },
                {
                    "code": 188,
                    "name": "绍兴市"
                },
                {
                    "code": 189,
                    "name": "金华市"
                },
                {
                    "code": 190,
                    "name": "衢州市"
                },
                {
                    "code": 191,
                    "name": "舟山市"
                },
                {
                    "code": 192,
                    "name": "台州市"
                },
                {
                    "code": 193,
                    "name": "丽水市"
                }
            ]
        },
        {
            "code": 13,
            "name": "安徽",
            "sub": [
                {
                    "code": 194,
                    "name": "合肥市"
                },
                {
                    "code": 195,
                    "name": "芜湖市"
                },
                {
                    "code": 196,
                    "name": "蚌埠市"
                },
                {
                    "code": 197,
                    "name": "淮南市"
                },
                {
                    "code": 198,
                    "name": "马鞍山市"
                },
                {
                    "code": 199,
                    "name": "淮北市"
                },
                {
                    "code": 200,
                    "name": "铜陵市"
                },
                {
                    "code": 201,
                    "name": "安庆市"
                },
                {
                    "code": 202,
                    "name": "黄山市"
                },
                {
                    "code": 203,
                    "name": "滁州市"
                },
                {
                    "code": 204,
                    "name": "阜阳市"
                },
                {
                    "code": 205,
                    "name": "宿州市"
                },
                {
                    "code": 206,
                    "name": "六安市"
                },
                {
                    "code": 207,
                    "name": "亳州市"
                },
                {
                    "code": 208,
                    "name": "池州市"
                },
                {
                    "code": 209,
                    "name": "宣城市"
                }
            ]
        },
        {
            "code": 14,
            "name": "福建",
            "sub": [
                {
                    "code": 210,
                    "name": "福州市"
                },
                {
                    "code": 211,
                    "name": "厦门市"
                },
                {
                    "code": 212,
                    "name": "莆田市"
                },
                {
                    "code": 213,
                    "name": "三明市"
                },
                {
                    "code": 214,
                    "name": "泉州市"
                },
                {
                    "code": 215,
                    "name": "漳州市"
                },
                {
                    "code": 216,
                    "name": "南平市"
                },
                {
                    "code": 217,
                    "name": "龙岩市"
                },
                {
                    "code": 218,
                    "name": "宁德市"
                }
            ]
        },
        {
            "code": 15,
            "name": "江西",
            "sub": [
                {
                    "code": 219,
                    "name": "南昌市"
                },
                {
                    "code": 220,
                    "name": "景德镇市"
                },
                {
                    "code": 221,
                    "name": "萍乡市"
                },
                {
                    "code": 222,
                    "name": "九江市"
                },
                {
                    "code": 223,
                    "name": "新余市"
                },
                {
                    "code": 224,
                    "name": "鹰潭市"
                },
                {
                    "code": 225,
                    "name": "赣州市"
                },
                {
                    "code": 226,
                    "name": "吉安市"
                },
                {
                    "code": 227,
                    "name": "宜春市"
                },
                {
                    "code": 228,
                    "name": "抚州市"
                },
                {
                    "code": 229,
                    "name": "上饶市"
                }
            ]
        },
        {
            "code": 16,
            "name": "山东",
            "sub": [
                {
                    "code": 230,
                    "name": "济南市"
                },
                {
                    "code": 231,
                    "name": "青岛市"
                },
                {
                    "code": 232,
                    "name": "淄博市"
                },
                {
                    "code": 233,
                    "name": "枣庄市"
                },
                {
                    "code": 234,
                    "name": "东营市"
                },
                {
                    "code": 235,
                    "name": "烟台市"
                },
                {
                    "code": 236,
                    "name": "潍坊市"
                },
                {
                    "code": 237,
                    "name": "济宁市"
                },
                {
                    "code": 238,
                    "name": "泰安市"
                },
                {
                    "code": 239,
                    "name": "威海市"
                },
                {
                    "code": 240,
                    "name": "日照市"
                },
                {
                    "code": 241,
                    "name": "莱芜市"
                },
                {
                    "code": 242,
                    "name": "临沂市"
                },
                {
                    "code": 243,
                    "name": "德州市"
                },
                {
                    "code": 244,
                    "name": "聊城市"
                },
                {
                    "code": 245,
                    "name": "滨州市"
                },
                {
                    "code": 246,
                    "name": "菏泽市"
                }
            ]
        },
        {
            "code": 17,
            "name": "河南",
            "sub": [
                {
                    "code": 247,
                    "name": "郑州市"
                },
                {
                    "code": 248,
                    "name": "开封市"
                },
                {
                    "code": 249,
                    "name": "洛阳市"
                },
                {
                    "code": 250,
                    "name": "平顶山市"
                },
                {
                    "code": 251,
                    "name": "安阳市"
                },
                {
                    "code": 252,
                    "name": "鹤壁市"
                },
                {
                    "code": 253,
                    "name": "新乡市"
                },
                {
                    "code": 254,
                    "name": "焦作市"
                },
                {
                    "code": 255,
                    "name": "濮阳市"
                },
                {
                    "code": 256,
                    "name": "许昌市"
                },
                {
                    "code": 257,
                    "name": "漯河市"
                },
                {
                    "code": 258,
                    "name": "三门峡市"
                },
                {
                    "code": 259,
                    "name": "南阳市"
                },
                {
                    "code": 260,
                    "name": "商丘市"
                },
                {
                    "code": 261,
                    "name": "信阳市"
                },
                {
                    "code": 262,
                    "name": "周口市"
                },
                {
                    "code": 263,
                    "name": "驻马店市"
                },
                {
                    "code": 264,
                    "name": "济源市"
                }
            ]
        },
        {
            "code": 18,
            "name": "湖北",
            "sub": [
                {
                    "code": 265,
                    "name": "武汉市"
                },
                {
                    "code": 266,
                    "name": "黄石市"
                },
                {
                    "code": 267,
                    "name": "十堰市"
                },
                {
                    "code": 268,
                    "name": "荆州市"
                },
                {
                    "code": 269,
                    "name": "宜昌市"
                },
                {
                    "code": 270,
                    "name": "襄樊市"
                },
                {
                    "code": 271,
                    "name": "鄂州市"
                },
                {
                    "code": 272,
                    "name": "荆门市"
                },
                {
                    "code": 273,
                    "name": "孝感市"
                },
                {
                    "code": 274,
                    "name": "黄冈市"
                },
                {
                    "code": 275,
                    "name": "咸宁市"
                },
                {
                    "code": 276,
                    "name": "随州市"
                },
                {
                    "code": 277,
                    "name": "仙桃市"
                },
                {
                    "code": 278,
                    "name": "天门市"
                },
                {
                    "code": 279,
                    "name": "潜江市"
                },
                {
                    "code": 280,
                    "name": "神农架林区"
                },
                {
                    "code": 281,
                    "name": "恩施土家族苗族自治州"
                }
            ]
        },
        {
            "code": 19,
            "name": "湖南",
            "sub": [
                {
                    "code": 282,
                    "name": "长沙市"
                },
                {
                    "code": 283,
                    "name": "株洲市"
                },
                {
                    "code": 284,
                    "name": "湘潭市"
                },
                {
                    "code": 285,
                    "name": "衡阳市"
                },
                {
                    "code": 286,
                    "name": "邵阳市"
                },
                {
                    "code": 287,
                    "name": "岳阳市"
                },
                {
                    "code": 288,
                    "name": "常德市"
                },
                {
                    "code": 289,
                    "name": "张家界市"
                },
                {
                    "code": 290,
                    "name": "益阳市"
                },
                {
                    "code": 291,
                    "name": "郴州市"
                },
                {
                    "code": 292,
                    "name": "永州市"
                },
                {
                    "code": 293,
                    "name": "怀化市"
                },
                {
                    "code": 294,
                    "name": "娄底市"
                },
                {
                    "code": 295,
                    "name": "湘西土家族苗族自治州"
                }
            ]
        },
        {
            "code": 20,
            "name": "广东",
            "sub": [
                {
                    "code": 296,
                    "name": "广州市"
                },
                {
                    "code": 297,
                    "name": "深圳市"
                },
                {
                    "code": 298,
                    "name": "珠海市"
                },
                {
                    "code": 299,
                    "name": "汕头市"
                },
                {
                    "code": 300,
                    "name": "韶关市"
                },
                {
                    "code": 301,
                    "name": "佛山市"
                },
                {
                    "code": 302,
                    "name": "江门市"
                },
                {
                    "code": 303,
                    "name": "湛江市"
                },
                {
                    "code": 304,
                    "name": "茂名市"
                },
                {
                    "code": 305,
                    "name": "肇庆市"
                },
                {
                    "code": 306,
                    "name": "惠州市"
                },
                {
                    "code": 307,
                    "name": "梅州市"
                },
                {
                    "code": 308,
                    "name": "汕尾市"
                },
                {
                    "code": 309,
                    "name": "河源市"
                },
                {
                    "code": 310,
                    "name": "阳江市"
                },
                {
                    "code": 311,
                    "name": "清远市"
                },
                {
                    "code": 312,
                    "name": "东莞市"
                },
                {
                    "code": 313,
                    "name": "中山市"
                },
                {
                    "code": 314,
                    "name": "潮州市"
                },
                {
                    "code": 315,
                    "name": "揭阳市"
                },
                {
                    "code": 316,
                    "name": "云浮市"
                }
            ]
        },
        {
            "code": 21,
            "name": "甘肃",
            "sub": [
                {
                    "code": 317,
                    "name": "兰州市"
                },
                {
                    "code": 318,
                    "name": "金昌市"
                },
                {
                    "code": 319,
                    "name": "白银市"
                },
                {
                    "code": 320,
                    "name": "天水市"
                },
                {
                    "code": 321,
                    "name": "嘉峪关市"
                },
                {
                    "code": 322,
                    "name": "武威市"
                },
                {
                    "code": 323,
                    "name": "张掖市"
                },
                {
                    "code": 324,
                    "name": "平凉市"
                },
                {
                    "code": 325,
                    "name": "酒泉市"
                },
                {
                    "code": 326,
                    "name": "庆阳市"
                },
                {
                    "code": 327,
                    "name": "定西市"
                },
                {
                    "code": 328,
                    "name": "陇南市"
                },
                {
                    "code": 329,
                    "name": "临夏回族自治州"
                },
                {
                    "code": 330,
                    "name": "甘南藏族自治州"
                }
            ]
        },
        {
            "code": 22,
            "name": "四川",
            "sub": [
                {
                    "code": 331,
                    "name": "成都市"
                },
                {
                    "code": 332,
                    "name": "自贡市"
                },
                {
                    "code": 333,
                    "name": "攀枝花市"
                },
                {
                    "code": 334,
                    "name": "泸州市"
                },
                {
                    "code": 335,
                    "name": "德阳市"
                },
                {
                    "code": 336,
                    "name": "绵阳市"
                },
                {
                    "code": 337,
                    "name": "广元市"
                },
                {
                    "code": 338,
                    "name": "遂宁市"
                },
                {
                    "code": 339,
                    "name": "内江市"
                },
                {
                    "code": 340,
                    "name": "乐山市"
                },
                {
                    "code": 341,
                    "name": "南充市"
                },
                {
                    "code": 342,
                    "name": "眉山市"
                },
                {
                    "code": 343,
                    "name": "宜宾市"
                },
                {
                    "code": 344,
                    "name": "广安市"
                },
                {
                    "code": 345,
                    "name": "达州市"
                },
                {
                    "code": 346,
                    "name": "雅安市"
                },
                {
                    "code": 347,
                    "name": "巴中市"
                },
                {
                    "code": 348,
                    "name": "资阳市"
                },
                {
                    "code": 349,
                    "name": "阿坝藏族羌族自治州"
                },
                {
                    "code": 350,
                    "name": "甘孜藏族自治州"
                },
                {
                    "code": 351,
                    "name": "凉山彝族自治州"
                }
            ]
        },
        {
            "code": 23,
            "name": "贵州",
            "sub": [
                {
                    "code": 352,
                    "name": "贵阳市"
                },
                {
                    "code": 353,
                    "name": "六盘水市"
                },
                {
                    "code": 354,
                    "name": "遵义市"
                },
                {
                    "code": 355,
                    "name": "安顺市"
                },
                {
                    "code": 356,
                    "name": "铜仁地区"
                },
                {
                    "code": 357,
                    "name": "毕节地区"
                },
                {
                    "code": 358,
                    "name": "黔西南布依族苗族自治州"
                },
                {
                    "code": 359,
                    "name": "黔东南苗族侗族自治州"
                },
                {
                    "code": 360,
                    "name": "黔南布依族苗族自治州"
                }
            ]
        },
        {
            "code": 24,
            "name": "海南",
            "sub": [
                {
                    "code": 361,
                    "name": "海口市"
                },
                {
                    "code": 362,
                    "name": "三亚市"
                },
                {
                    "code": 363,
                    "name": "三沙市"
                },
                {
                    "code": 364,
                    "name": "五指山市"
                },
                {
                    "code": 365,
                    "name": "琼海市"
                },
                {
                    "code": 366,
                    "name": "儋州市"
                },
                {
                    "code": 367,
                    "name": "文昌市"
                },
                {
                    "code": 368,
                    "name": "万宁市"
                },
                {
                    "code": 369,
                    "name": "东方市"
                },
                {
                    "code": 371,
                    "name": "定安县"
                },
                {
                    "code": 373,
                    "name": "临高县"
                },
                {
                    "code": 374,
                    "name": "白沙黎族自治县"
                },
                {
                    "code": 375,
                    "name": "昌江黎族自治县"
                },
                {
                    "code": 376,
                    "name": "乐东黎族自治县"
                },
                {
                    "code": 377,
                    "name": "陵水黎族自治县"
                },
                {
                    "code": 378,
                    "name": "保亭黎族苗族自治县"
                },
                {
                    "code": 379,
                    "name": "琼中黎族苗族自治县"
                },
                {
                    "code": 500009,
                    "name": "澄迈县"
                }
            ]
        },
        {
            "code": 25,
            "name": "云南",
            "sub": [
                {
                    "code": 380,
                    "name": "昆明市"
                },
                {
                    "code": 381,
                    "name": "曲靖市"
                },
                {
                    "code": 382,
                    "name": "玉溪市"
                },
                {
                    "code": 383,
                    "name": "保山市"
                },
                {
                    "code": 384,
                    "name": "昭通市"
                },
                {
                    "code": 385,
                    "name": "丽江市"
                },
                {
                    "code": 386,
                    "name": "普洱市"
                },
                {
                    "code": 387,
                    "name": "临沧市"
                },
                {
                    "code": 388,
                    "name": "文山壮族苗族自治州"
                },
                {
                    "code": 389,
                    "name": "红河哈尼族彝族自治州"
                },
                {
                    "code": 390,
                    "name": "西双版纳傣族自治州"
                },
                {
                    "code": 391,
                    "name": "楚雄彝族自治州"
                },
                {
                    "code": 392,
                    "name": "大理白族自治州"
                },
                {
                    "code": 393,
                    "name": "德宏傣族景颇族自治州"
                },
                {
                    "code": 394,
                    "name": "怒江傈僳族自治州"
                },
                {
                    "code": 395,
                    "name": "迪庆藏族自治州"
                }
            ]
        },
        {
            "code": 26,
            "name": "青海",
            "sub": [
                {
                    "code": 396,
                    "name": "西宁市"
                },
                {
                    "code": 397,
                    "name": "海东地区"
                },
                {
                    "code": 398,
                    "name": "海北藏族自治州"
                },
                {
                    "code": 399,
                    "name": "黄南藏族自治州"
                },
                {
                    "code": 400,
                    "name": "海南藏族自治州"
                },
                {
                    "code": 401,
                    "name": "果洛藏族自治州"
                },
                {
                    "code": 402,
                    "name": "玉树藏族自治州"
                },
                {
                    "code": 403,
                    "name": "海西蒙古族藏族自治州"
                }
            ]
        },
        {
            "code": 27,
            "name": "陕西",
            "sub": [
                {
                    "code": 404,
                    "name": "西安市"
                },
                {
                    "code": 405,
                    "name": "铜川市"
                },
                {
                    "code": 406,
                    "name": "宝鸡市"
                },
                {
                    "code": 407,
                    "name": "咸阳市"
                },
                {
                    "code": 408,
                    "name": "渭南市"
                },
                {
                    "code": 409,
                    "name": "延安市"
                },
                {
                    "code": 410,
                    "name": "汉中市"
                },
                {
                    "code": 411,
                    "name": "榆林市"
                },
                {
                    "code": 412,
                    "name": "安康市"
                },
                {
                    "code": 413,
                    "name": "商洛市"
                }
            ]
        },
        {
            "code": 28,
            "name": "广西",
            "sub": [
                {
                    "code": 414,
                    "name": "南宁市"
                },
                {
                    "code": 415,
                    "name": "柳州市"
                },
                {
                    "code": 416,
                    "name": "桂林市"
                },
                {
                    "code": 417,
                    "name": "梧州市"
                },
                {
                    "code": 418,
                    "name": "北海市"
                },
                {
                    "code": 419,
                    "name": "防城港市"
                },
                {
                    "code": 420,
                    "name": "钦州市"
                },
                {
                    "code": 421,
                    "name": "贵港市"
                },
                {
                    "code": 422,
                    "name": "玉林市"
                },
                {
                    "code": 423,
                    "name": "百色市"
                },
                {
                    "code": 424,
                    "name": "贺州市"
                },
                {
                    "code": 425,
                    "name": "河池市"
                },
                {
                    "code": 426,
                    "name": "来宾市"
                },
                {
                    "code": 427,
                    "name": "崇左市"
                }
            ]
        },
        {
            "code": 29,
            "name": "西藏",
            "sub": [
                {
                    "code": 428,
                    "name": "拉萨市"
                },
                {
                    "code": 429,
                    "name": "那曲地区"
                },
                {
                    "code": 430,
                    "name": "昌都地区"
                },
                {
                    "code": 431,
                    "name": "山南地区"
                },
                {
                    "code": 432,
                    "name": "日喀则地区"
                },
                {
                    "code": 433,
                    "name": "阿里地区"
                },
                {
                    "code": 434,
                    "name": "林芝地区"
                }
            ]
        },
        {
            "code": 30,
            "name": "宁夏",
            "sub": [
                {
                    "code": 435,
                    "name": "银川市"
                },
                {
                    "code": 436,
                    "name": "石嘴山市"
                },
                {
                    "code": 437,
                    "name": "吴忠市"
                },
                {
                    "code": 438,
                    "name": "固原市"
                },
                {
                    "code": 439,
                    "name": "中卫市"
                }
            ]
        },
        {
            "code": 31,
            "name": "新疆",
            "sub": [
                {
                    "code": 440,
                    "name": "乌鲁木齐市"
                },
                {
                    "code": 441,
                    "name": "克拉玛依市"
                },
                {
                    "code": 442,
                    "name": "石河子市"
                },
                {
                    "code": 446,
                    "name": "吐鲁番地区"
                },
                {
                    "code": 447,
                    "name": "阿克苏地区"
                },
                {
                    "code": 448,
                    "name": "喀什地区"
                },
                {
                    "code": 449,
                    "name": "哈密地区"
                },
                {
                    "code": 450,
                    "name": "和田地区"
                },
                {
                    "code": 451,
                    "name": "克孜勒苏柯尔克孜自治州"
                },
                {
                    "code": 452,
                    "name": "巴音郭楞蒙古自治州"
                },
                {
                    "code": 453,
                    "name": "昌吉回族自治州"
                },
                {
                    "code": 454,
                    "name": "博尔塔拉蒙古自治州"
                },
                {
                    "code": 455,
                    "name": "伊犁哈萨克自治州"
                },
                {
                    "code": 456,
                    "name": "塔城地区"
                },
                {
                    "code": 457,
                    "name": "阿勒泰地区"
                },
                {
                    "code": 500010,
                    "name": "阿拉尔"
                },
                {
                    "code": 500011,
                    "name": "图木舒克"
                },
                {
                    "code": 500012,
                    "name": "五家渠"
                },
                {
                    "code": 500013,
                    "name": "北屯"
                },
                {
                    "code": 500014,
                    "name": "铁门关"
                },
                {
                    "code": 500015,
                    "name": "双河"
                },
                {
                    "code": 500016,
                    "name": "可克达拉"
                }
            ]
        },
        {
            "code": 32,
            "name": "内蒙古",
            "sub": [
                {
                    "code": 458,
                    "name": "呼和浩特市"
                },
                {
                    "code": 459,
                    "name": "包头市"
                },
                {
                    "code": 460,
                    "name": "乌海市"
                },
                {
                    "code": 461,
                    "name": "赤峰市"
                },
                {
                    "code": 462,
                    "name": "通辽市"
                },
                {
                    "code": 463,
                    "name": "鄂尔多斯市"
                },
                {
                    "code": 464,
                    "name": "呼伦贝尔市"
                },
                {
                    "code": 465,
                    "name": "巴彦淖尔市"
                },
                {
                    "code": 466,
                    "name": "乌兰察布市"
                },
                {
                    "code": 467,
                    "name": "锡林郭勒盟"
                },
                {
                    "code": 468,
                    "name": "兴安盟"
                },
                {
                    "code": 469,
                    "name": "阿拉善盟"
                }
            ]
        },
        {
            "code": 33,
            "name": "澳门",
            "sub": [
                {
                    "code": 470,
                    "name": "澳门"
                }
            ]
        },
        {
            "code": 34,
            "name": "香港",
            "sub": [
                {
                    "code": 471,
                    "name": "香港"
                }
            ]
        }
    ]
}

```