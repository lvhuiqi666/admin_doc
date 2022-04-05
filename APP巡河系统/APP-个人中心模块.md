# APP-个人中心模块

## 个人中心-我的列表页：

### 接口地址：/v1/wisdom/app/center/list/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名   | 备注 |
| ------ | ---- | -------- | ------ | ---- |
| userId | INT  | 是       | 用户ID |      |

### 请求示例:

```bash
{
    "userId": 1
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "mobile": "13069634825",  // 手机号
            "is_authed": true,  // 是否已验证： true：已经验证、 false:未验证
            "id": 1,  // 用户ID
            "avatar_url": null, // 头像地址
            "name": "吕品品"  // 用户名称
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 个人中心-上传头像接口：

### 接口地址：/v1/wisdom/app/save/user_avatar/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型   | 是否必传 | 命名            | 备注 |
| --------- | ------ | -------- | --------------- | ---- |
| userId    | INT    | 是       | 用户ID          |      |
| avatarUrl | STRING | 是       | 头像外链地址URL |      |

### 请求示例:

```bash
{
    "userId": 1,
    "avatarUrl": "xxx"
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

## 个人中心-删除头像接口：

### 接口地址：/v1/wisdom/app/clear/user_avatar/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名   | 备注 |
| ------ | ---- | -------- | ------ | ---- |
| userId | INT  | 是       | 用户ID |      |

### 请求示例:

```bash
{
    "userId": 1
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

## 个人中心-用户身份认证：

### 接口地址：/v1/wisdom/app/user/auth/

### 请求方式：POST

### 请求参数：

| 参数名      | 类型   | 是否必传 | 命名         | 备注 |
| ----------- | ------ | -------- | ------------ | ---- |
| userId      | INT    | 是       | 用户ID       |      |
| name        | STRING | 否       | 用户姓名     |      |
| mobile      | STRING | 否       | 用户手机号   |      |
| company     | STRING | 否       | 工作单位     |      |
| frontUrl    | STRING | 否       | 身份证(姓名) |      |
| backUrl     | STRING | 否       | 身份证(国徽) |      |
| identityNum | STRING | 否       | 身份证号     |      |

### 请求示例:

```bash
{
    "userId": 1,
    "identityNum": "123",
    "frontUrl": "xxx"
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

