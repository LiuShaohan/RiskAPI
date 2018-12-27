# 身份证照片和活体照片相似度

@method

```
验证身份证照片和活体照片相似度
```

@introduction

```
活体认证流程中进行判断身份证正面照片和活体照片是否为同一个人
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
| first\_image\_url | Y | String | 第一张图片地址（比如身份证或活体） |
| second\_image\_url | Y | String | 第二张图片地址（比如身份证或活体） |
| submitTime | Y | long | 提交时的时间戳 |

PS：此处图片有可能不都是正面，请自行旋转

@request json

```js
{
  'userId':'xxx',
  'first_image_url':'xxx',
  'second_image_url':'xxx',
  'submitTime':xxxxxxxxxxxx
}
```

@response param

| 字段 | 类型 | 说明 |
| :--- | :--- | :--- |
| code | int | 系统响应码:1000，  其他你们定义，可参看如下code demo |
| verification\_score | float | 人脸比对得分，值为 0~1，值越大表示是同一个人的可能性越大 |
| message | String | 错误信息 |

@response json

```js
{
  'code': xxx,
  'verification_score': xxx
  'message':xxx
}
```

@code demo

| `code` | 字段值 | 描述 |
| :--- | :--- | :--- |
| 1100 | invalid crendential | 账号密码不匹配或签名认证生成有误 |
| 1200 | invalid argument | 输入参数无效 |
| 1101 | expired crendential | 账号过期 |
| 1103 | url no permission | 该接口没有权限 |
| 1002 | rate limit exceeded | 调用频率超过限制 |
| 2003 | invalid image size | 图片大小不符合要求 |
| 2004 | invalid content length | 输入内容长度不符合要求 |
| 2005 | invalid image type | 图片类型不符合要求 |
| 2006 | corrupted image error | 图片损坏 |
| 4000 | detection failed | 提取特征失败,没有检测到图片中的人脸 |



