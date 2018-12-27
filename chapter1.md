# 黑名单库拉取

@method

```
拉取风控系统中的黑名单
```

@introduction

```
拉取风控所有黑名单数据到业务系统，方便前置判断
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
| timestamp | Y | datetime | 该时间戳后的数据正序，获取1000条 |
| type | Y | int | 1：身份证 2：手机号码 |

@response param

| 返回字段 | 字段类型 | 父类 | 说明 |
| :--- | :--- | :--- | :--- |
| code | int | 无 | 系统响应码：1000，其他你们定义 |
| message | String | 无 | 错误信息 |
| data | Object | 无 | 返回的JSON数据集合，详情见下文@@data param |

@@data param

| 参数 | 字段类型 | 说明 |
| :--- | :--- | :--- |
| pageCount | int | 总页数 |
| content | List | eg.:字符串数组\["17759219164","17759219165"\] |

@response josn

```js
{
  'code': xxx,
  'message':'xxx',
  'data':{
    'pageount':xxxxx,
    'content':["17759219164","17759219165"]
  }
}
```


