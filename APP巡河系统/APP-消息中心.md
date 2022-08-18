# APP-消息中心

## 版本发布：

> 我们的APP、后台、大屏都要有个版本的包，每次发版时，请求当前接口，如果是安装包的外链地址，那么将传入到content中，版本发布接口，主要为了做消息推送，用户实时更新版本包。

### 接口地址：/wisdom/update/version/

### 请求方式：POST

### 请求参数：

| 参数名      | 类型   | 是否必传 | 命名         | 备注                      |
| ----------- | ------ | -------- | ------------ | ------------------------- |
| versionType | INT    | 是       | 版本类型     | 1:管理后台、2:APP、3:大屏 |
| content     | STRING | 是       | 版本更新内容 |                           |
| versionNum  | STRING | 是       | 版本号       | 命名规则: 1.0.0.1         |

### 请求示例:

```bash
{
    "versionType": 2,
    "content": "内容",
    "versionNum": "1.0.0"
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

## 消息中心列表页：

### 接口地址：/wisdom/app/message/list/?userId=1&content=仰望

### 请求方式：GET

### 请求参数：

| 参数名  | 类型   | 是否必传 | 命名 | 备注           |
| ------- | ------ | -------- | ---- | -------------- |
| userId  | INT    | 是       |      | 登录人的用户ID |
| content | STRING | 是       | 内容 | 支持模糊搜索   |

### 请求示例:

```bash
?userId=1&content=仰望
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 2,  // 列表页总数
        "list": [
            {
                "id": 37,  // 消息ID
                "msgType": 5,  // 消息类型
                "readAlready": true,  // 是否已读
                "content": "仰望星空管理员回复了非法捕鱼问题。",  // 消息内容
                "sTime": 1660667216 // 推送时间
            },
            {
                "id": 32,
                "msgType": 4,
                "readAlready": true,
                "content": "仰望星空用户完成了西湖巡河A巡河任务。",
                "sTime": 1660665079
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

## 是否未读消息接口：

> 登录以后右上角，消息的提醒展示，多少消息是未读的数量

### 接口地址：/wisdom/app/message/count/?userId=5

### 请求方式：GET

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名 | 备注           |
| ------ | ---- | -------- | ---- | -------------- |
| userId | INT  | 是       |      | 登录人的用户ID |

### 请求示例:

```bash
?userId=1
```

### 响应

#### 200

```bash
{
    "data": {
        "unreadCount": 4,  // 未读的消息
        "readCount": 0  // 已读的消息
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

