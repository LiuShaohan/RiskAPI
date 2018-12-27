# 运营商认证-待完善

@method

```
获取用户运营商报告和通话详单
```

@introduction

```
用户提交手机号、密码、验证码，风控系统接收三方返回的报告与数据
```

@URL

```
/
```

@request method

```
http/post
```

@request param

| 参数 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| userId | Y | String | 用户唯一标示 |
| token | Y | Sting | token |
| mobile\_no | Y | String | 用户手机号 |
| identity\_card | Y | String | 用户身份证号 |
| name | Y | String | 用户姓名 |
| password | Y | String | 运营商登录密码 |
| callback\_set | Y | String | 回调地址的JSON数据集合，详情见下文 |

@@callback\_set param

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| callback\_url | String | 异步回调URL |
| token | String | token |

@request json

```js
{
    'token':'xxxxxxxxx',
    'mobile_no':'xxxxxxxxxxxx',
    'identity_card':'xxxxxxxxxxxxxxxxxxxxx',
    'name':'xxx',
    'password':'xxxxxx',
    'callback_set':{
        'callback_url':'xxxxxxxxxxxxxx',
        'token':'xxxxxxxxxxxxxx'
    }
}
```

@response param

| 返回字段 | 字段类型 | 说明 |
| :--- | :--- | :--- |
| code | String | 流程进度代码，释义见@code demo |
| message | String | code的解释 |
| trace\_id | String | 将该值赋给下一接口的traceId |
| data\_stamp | String | 时间戳 |
| data | String | 返回的JSON数据集合，详情见下文@@data param |

@@data param

| 参数 | 类型 | 说明 |
| :--- | :--- | :--- |
| task\_id | String | 魔蝎运营商返回数据 |
| guide\_code | String | 释义见@guide\_code demo |
| guide\_message | String | 释义见@guide\_code demo |
| auth\_code | String | 需要图片验证码是会出现该字段，该字段是base64编码的图片 |

@response json

```js
{
    'code':'103',
    'message':'xxxxxxx',
    'trace_id':'xxxxxx',
    'date_stamp':'xxxxxxxxx',
    'data':{
        'task_id':'xxxxxxxxx',
        'guide_code':'xxxxxxxxx',
        'guide_message':'xxxxxxxxx',
        'auth_code':'xxxxxxxxx'
    }
}
```

@code demo

| code | 说明 |
| :--- | :--- |
| 103 | 系统异常 |
| 104 | 流程进行中，根据guide\_code中的值判断下一步做什么 |
| 105 | 提交成功，后台认证中，认证结果会通过回调通知APP |

@guide\_code demo （当code=104时，处理）

