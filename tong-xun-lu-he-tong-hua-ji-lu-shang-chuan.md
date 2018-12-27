
---

# 通讯录和通话记录上传

@method

```
App后台静默上传用户通讯录与通话记录
```

@introduction

```
通讯录为必填项，通话记录为选填项
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
| userId | Y | String | 用户唯一标识 |
| contacts | Y | String | 联系人的json字符串list，见下文@@contacts param |
| records | N | String | 通话记录json字符串list，见下文@@records param |
| submitTime | Y | long | 提交时的时间戳 |

@@contacts param

| 参数 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| name | Y | String | 联系人姓名 |
| phone | Y | String | 联系人电话号码 |
| create\_time | Y | String | 创建时间戳 |
| contactTimes | Y | int | 联系次数 |

@@records param

| 参数 | 必选 | 类型 | 说明 |
| :--- | :--- | :--- | :--- |
| from\_name | N | String | 联系人姓名 |
| from\_phone | N | String | 联系人电话号码 |
| time | N | long | 通话日期 |
| type | N | int | 呼叫情况，1：来电；2：呼出；3：未接 |
| duration | N | long | 通话时长 |

@request json

```js
{
    'mobile':'xxxxxxxxx',
    'id_card':'xxxxxxxxxxxx',
    'submitTime':xxxxxx,
    'contacts':[
        {
            'name':'xxxxxxxxxxxxxx',
            'phone':'xxxxxxxxxxxxxx',
            'create_time':'xxxxxxxxxxxxxx',
            'contactTimes':xxxxxxxxxxxxxx
        },
        {
            'name':'xxxxxxxxxxxxxx',
            'phone':'xxxxxxxxxxxxxx',
            'create_time':'xxxxxxxxxxxxxx',
            'contactTimes':xxxxxxxxxxxxxx
        }
     ],   
    'records':[
        {
            'from_name':'xxxxxxxxxxxxxx',
            'from_phone':'xxxxxxxxxxxxxx',
            'time':xxxxxxxxxxxxxx,
            'type':xxxxxxxxxxxxxx,
            'type':xxxxxxxxxxxxxx
        },
        {
            'from_name':'xxxxxxxxxxxxxx',
            'from_phone':'xxxxxxxxxxxxxx',
            'time':xxxxxxxxxxxxxx,
            'type':xxxxxxxxxxxxxx,
            'duration':xxxxxxxxxxxxxx
        }
    ]
}
```

@response param

| 返回字段 | 字段类型 | 说明 |
| :--- | :--- | :--- |
| code | String | 系统响应码：1000，其他你们定义 |
| message | String | code的解释 |

@response json

```js
{
    'code':'103',
    'message':'xxxxxxx'
}
```



