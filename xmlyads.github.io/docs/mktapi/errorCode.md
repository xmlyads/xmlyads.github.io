# 错误码

**返回示例 : 成功**

```json
{
    "status": 0,
    "type": "SUCCESS",
    "msg": "success",
    "data": "xxxx"
}

```

**返回示例 : 失败**

```json

{
    "status": 10003,
    "type": "ERROR",
    "msg": "权限校验不通过",
    "data": null
}

```
<br/>

### 错误码和描述
|  错误码(status)   | 类型（type） | 描述(msg)  | 
|  ----  | ---- | ---- | 
| 0  | SUCCESS | 正常 | 
| 10003  | ERROR | 权限校验不通过 | 
| 10011  | ERROR | 登录失败 |
| 50000  | ERROR | 未知错误 |
| 50001  | ERROR | 入参校验错误 | 




 


