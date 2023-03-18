# APP-登录模块

## 用户登录：

### 接口地址：/wisdom/app/login/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型   | 是否必传 | 命名          | 备注 |
| ------ | ------ | -------- | ------------- | ---- |
| mobile | STRING | 是       | 用户名-手机号 |      |
| pd     | STRING | 是       | 密码          |      |

### 请求示例:

```bash
{
    "mobile": "13069634825",
    "pd": 123456
}
```

### 响应

#### 200

```bash
{
    "data": {
        "name": "吕品品",  // 用户姓名
        "roles": 7,  // 角色ID
        "mobile": "13069634825",  // 用户手机号
        "roles_name": "管理员",  // 角色名称
        "company": "BAT",  // 工作单位
        "scope": "",  // 工作范围
        "id": 1,  // 用户ID
        "projects_info": [ // 负责的项目信息
            {
                "ship_info": [ // 项目中船的信息
                    {
                        "id": 29,  // 船的ID
                        "project_type": 1,  // 项目类型
                        "number": "0016"  // 船的编码
                        "name": "QDF-0016", // 船的名称
                    }
                ],
                "num": "JS-SZ-YYJ-ZJJX-20210508",  // 项目名称
                "id": 33, // 项目ID
                "name": "平江河项目",  // 项目名称
                "waters_id": 23，  // 水域ID(废弃)
                "waters_info": [  // 水域信息(新字段)
                    {
                        "waters_number": "TZ-001", // 水域编号
                        "waters_name": "台州河段",   // 水域名称
                        "waters_id": 57 // 水域ID
                    }
                ],
            },
        "auth": [  // 登录权限控制板块
            {
                "auth_type": 2,  // 类型: 1:大屏幕、2:app 、 3:后台、 4:驾驶舱
                "is_enabled": false, // false 表示启用、ture 表示禁用
                "name": "项目管理",  // 名称
                "project_desc": [ // 项目管理中, 会有配置的详情信息, 但是 接口已经返回， 此字段可以忽略
                    {
                        "num": "JS-SZ-YYJ-ZJJX-20210508",
                        "id": 33,
                        "name": "平江河项目"
                    }
                    ]
                "roles_id": 7,  // 角色ID
                "func_id": "XMGL",  // 函数命名
                "id": 464, // 权限角色ID
                "desc": null  // 角色详情
            }]
     ]
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## APP获取验证码接口(注册)：

### 接口地址：/v1/wisdom/app/sms/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型   | 是否必传 | 命名          | 备注 |
| ------ | ------ | -------- | ------------- | ---- |
| mobile | STRING | 是       | 用户名-手机号 |      |

### 请求示例:

```bash
{
    "mobile": "13069634825",
    "pd": 123456
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

## APP用户注册接口：

### 接口地址：/v1/wisdom/app/register/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名          | 备注 |
| ---------- | ------ | -------- | ------------- | ---- |
| mobile     | STRING | 是       | 用户名-手机号 |      |
| company    | STRING | 否       | 工作单位      |      |
| name       | STRING | 是       | 姓名          |      |
| mobile     | STRING | 是       | 手机号        |      |
| pd         | STRING | 否       | 密码          |      |
| verifyCode | INT    | 是       | 验证码        |      |

### 请求示例:

```bash
{
    "company": "公司",
    "name": "xxx",
    "mobile": "13011114222",
    "pd": 123456,
    "verifyCode": 6666
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

## APP获取验证码接口(忘记密码)：

### 接口地址：/v1/wisdom/app/forget/password/sms/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型   | 是否必传 | 命名           | 备注 |
| ------ | ------ | -------- | -------------- | ---- |
| mobile | STRING | 是       | 用户名-手机号  |      |
| pd1    | STRING | 是       | 第一次输入密码 |      |
| pd2    | STRING | 是       | 第二次输入密码 |      |

### 请求示例:

```bash
{
    "mobile": "13069634825",
    "pd1": "123456",
    "pd2": "123456"
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

## APP忘记密码：

### 接口地址：/v1/wisdom/app/forget/password/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名           | 备注 |
| ---------- | ------ | -------- | -------------- | ---- |
| mobile     | STRING | 是       | 用户名-手机号  |      |
| pd1        | STRING | 是       | 第一次输入密码 |      |
| pd2        | STRING | 是       | 第二次输入密码 |      |
| verifyCode | INT    | 是       | 验证码         |      |

### 请求示例:

```bash
{
    "mobile": "13069634825",
    "pd1": "123456",
    "pd2": "123456",
    "verifyCode": 6666
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

## 获取用户权限：

### 接口地址：/v1/wisdom/app/check/user_auth/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名   | 备注 |
| ------ | ---- | -------- | ------ | ---- |
| userId | INT  | 是       | 用户ID |      |

### 请求示例:

```bash
{"userId": 1}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "is_enabled": false,    // false 表示没有被禁用、 true 表示已经被禁用
            "is_authed": true, // true 表示已经认证、false 表示未认证
            "id": 1 // 用户ID
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 人脸识别接口：

### 接口地址：/app/verify/face/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名             | 备注 |
| -------- | ------ | -------- | ---------------- | ---- |
| userId   | INT    | 是       | 用户ID           |      |
| imageUrl | STRING | 是       | 用户图片外联地址 |      |

### 请求示例:

```bash
{
    "userId": 22,
    "imageUrl": "https://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/1590566581-object.png"
}
```

### 响应

#### 200

```bash
{
    "data": {
        "result": false  // 认证未通过、 true 表示认证通过
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

