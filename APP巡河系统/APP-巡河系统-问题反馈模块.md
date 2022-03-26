# APP-巡河系统-问题反馈模块

## 发布反馈问题接口：

### 接口地址：/v1/wisdom/app/release/feedback/

### 请求方式：POST

### 请求参数：

| 参数名       | 类型   | 是否必传 | 命名     | 备注                               |
| ------------ | ------ | -------- | -------- | ---------------------------------- |
| content      | STRING | 是       | 问题描述 |                                    |
| cTime        | STRING | 是       | 问题时间 |                                    |
| waterId      | INT    | 是       | 水域名称 |                                    |
| address      | STRING | 是       | 发现地址 |                                    |
| reportUserId | INT    | 是       | 上报人ID | 姓名、手机从登录成功带过来自动填写 |
| imageAddress | STRING | 是       | 上报图片 |                                    |
| videoAddress | STRING | 否       | 上报视频 |                                    |

### 请求示例:

```bash
{
    "content": "非法捕鱼",
    "cTime": 1647963269,
    "waterId": 32,
    "address": "附近",
    "reportUserId": 1,
    "imageAddress": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/1641364340-front_img.png"
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除反馈问题接口：

### 接口地址：/v1/wisdom/app/delete/feedback/

### 请求方式：POST

### 请求参数：

| 参数名       | 类型 | 是否必传 | 命名       | 备注       |
| ------------ | ---- | -------- | ---------- | ---------- |
| fbId         | INT  | 是       | 反馈问题ID |            |
| reportUserId | INT  | 是       | 上报人ID   | 登录时获取 |

### 请求示例:

```bash
{
	"fbId": 1,
	"reportUserId": 1
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 处理上报问题接口：

### 接口地址：/v1/wisdom/app/process/feedback/

### 请求方式：POST

### 请求参数：

| 参数名          | 类型   | 是否必传 | 命名       | 备注                         |
| --------------- | ------ | -------- | ---------- | ---------------------------- |
| fbId            | INT    | 是       | 问题ID     |                              |
| proUserId       | INT    | 是       | 处理人员ID |                              |
| proTs           | STRING | 是       | 处理时间   | 秒级别时间戳                 |
| status          | INT    | 是       | 问题状态   | 1:待处理、2:处理中、3:已处理 |
| answer          | STRING | 是       | 处理事项   |                              |
| proImageAddress | STRING | 是       | 上报图片   |                              |
| proVideoAddress | STRING | 否       | 上报视频   |                              |

### 请求示例:

```bash
{
    "fbId": 1,
    "proUserId": 5,
    "proTs": "1647996093",
    "status": 3,
    "answer": "处理",
    "proImageAddress": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/1641364340-front_img.png"

}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 反馈问题列表：

> 根据status 状态不同，来区分待处理、处理中 跟已处理的字段

### 接口地址：/v1/wisdom/app/feedback/list/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名             | 备注                         |
| ---------- | ------ | -------- | ---------------- | ---------------------------- |
| watersId   | LIST   | 是       | 当前人负责的水域 | 账号登录时获取               |
| status     | INT    | 是       | 问题状态         | 1:待处理、2:处理中、3:已处理 |
| watersName | STRING | 否       | 水域名称         | 筛选                         |
| sTime      | INT    | 否       | 反馈问题开始时间 | 筛选                         |
| eTime      | INT    | 否       | 反馈问题结束时间 | 筛选                         |

### 请求示例:

```bash
{
    "watersId": [
        32
    ],
    "status": 3,  // 1:待处理、2:处理中、3:已处理
    "watersName": "祥",
    "sTime": 1647963268,
    "eTime": 1647963333
}
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 2,
        "list": [
            {
                "id": 18, // 问题ID
                "cTime": "1648193976.393878", // 上报时间
                "content": "1111",  //上报问题内容
                "watersInfo": {  // 水域信息
                    "id": 61,
                    "name": "温瑞塘河-瑞安(早)"
                },
                "imageAddress": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/images/164817574479997.png",  // 上报图片
                "videoAddress": "",  // 上报视频 
                "status": 2,  // 状态
                "address": "还好吧",  // 上报地址
                "cTs": 1648187497,  //上报时间 
                "proUser": "吕品品",  // 处理人
                "proMobile": "13069634825", // 处理人手机号
                "proTs": 1648193946,  // 处理时间
                "answer": "asf",  // 处理事项
                "proVideoAddress": "",  // 处理视频
                "proImageAddress": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/images/1648193967134148.png", // 处理图片
                "reportUser": "吕品品",  // 上报人
                "reportMobile": "13069634825", // 上报手机号
                "userId": 42,  // 上报人ID
                "processUserId": 1 // 处理人ID
            }
        ],
        "links": {
            "previous": null,
            "next": null
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 用户反馈问题列表：

> 当前登录角色反馈的问题列表

### 接口地址：/v1/wisdom/app/report/feedback/list/

### 请求方式：POST

### 请求参数：

| 参数名       | 类型 | 是否必传 | 命名     | 备注           |
| ------------ | ---- | -------- | -------- | -------------- |
| reportUserId | INT  | 是       | 上报人ID | 账号登录时获取 |

### 请求示例:

```bash
{"reportUserId": 1}
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 13, // 总数
        "list": [
            {
                "id": 13,  // 反馈问题的ID
                "cTime": "1647964578.378882",  // 反馈时间
                "content": "非法捕鱼J",  // 问题内容
                "watersInfo": { // 水域信息
                    "id": 32,
                    "name": "祥符荡"
                },
                "imageAddress": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/1641364340-front_img.png",  // 上面图片
                "videoAddress": "", 
                "status": 1,  // 1:待处理、2:处理中、3:已处理
                "cTs": 1647963269 // 反馈时间
            }
        ],
        "links": {
            "previous": null,  // 上一页
            "next": "http://127.0.0.1:8000/v1/wisdom/app/report/feedback/list/?page=2" //下一页
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 反馈问题详情接口：

> 如果是待处理状态，点击当前问题，变成处理中。

### 接口地址：/v1/wisdom/app/feedback/detail/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| fbId   | INT  | 是       | 反馈问题ID |      |

### 请求示例:

```bash
{
    "fbId": 2
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "status": 2, // 1:待处理、2:处理中、3:已处理
            "user__name": "吕品品", // 上报人
            "waters_id": 32, // 水域ID
            "pro_ts": null, // 处理时间
            "address": "附近",  // 发现位置
            "process_user__mobile": null, // 处理人联系方式
            "user__mobile": "13069634825", // 上报人联系方式
            "content": "非法捕鱼A",  // 问题描述
            "waters__name": "祥符荡", // 水域名称
            "answer": null, // 处理事项
            "user_id": 1, // 上报人ID
            "process_user_id": null, // 处理人ID
            "image_address": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/1641364340-front_img.png", // 上报图片
            "id": 2, // 问题ID
            "process_user__name": null, // 处理人名
            "pro_image_address": null // 处理图片
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

