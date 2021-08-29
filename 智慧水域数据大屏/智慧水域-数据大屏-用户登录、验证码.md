# 智慧水域-大屏-登录模块

描述:

> 登录模块

## 发送验证码：

### 接口地址：/v1/pc/sms/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型   | 是否必传 | 命名          | 备注 |
| ------ | ------ | -------- | ------------- | ---- |
| mobile | STRING | 是       | 用户名-手机号 |      |
| pd     | STRING | 是       | 密码          |      |

### 请求示例:

```bash
{
    "mobile":"13069634826",
    "pd": "1234567"
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

## 用户登录：

### 接口地址：/v1/pc/login/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名          | 备注 |
| ---------- | ------ | -------- | ------------- | ---- |
| mobile     | STRING | 是       | 用户名-手机号 |      |
| pd         | STRING | 是       | 密码          |      |
| verifyCode | STRING | 是       | 验证码        |      |

### 请求示例:

```bash
{
    "mobile":"13069634826",
    "pd": "123456",
    "verifyCode": "6666"
}
```

### 响应

#### 200

```bash
{
    "data": {
        "name": "吕品品123", // 用户姓名
        "roles": 6,  // 角色
        "mobile": "13069634826",  // 手机号|用户名
        "roles_name": "普通用户",  // 角色名称
        "auth": [  // 权限管理 true 不可看到当前板块    false:可以看到当前板块
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "综合业务",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "ZHYW",
                "id": 1,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "水面保洁",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "SMBJ",
                "id": 2,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "水质检测",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "ZSJC",
                "id": 3,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "安防应急",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "AFYJ",
                "id": 4,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "水下探测",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "SXTC",
                "id": 5,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "智能巡河",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "ZNXH",
                "id": 6,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "试剂投放",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "SJTF",
                "id": 7,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "设备自控",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "SBZK",
                "id": 8,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "监控云台",
                "project_desc": null,
                "roles_id": 6,
                "func_id": "JKYT",
                "id": 9,
                "desc": null
            },
            {
                "auth_type": 1,
                "is_enabled": false,
                "name": "项目管理",
                "project_desc": [
                    {
                        "num": "1232132132",
                        "id": 3,
                        "name": "项目名册"
                    },
                    {
                        "num": "12321322132",
                        "id": 4,
                        "name": "项目名册"
                    }
                ],
                "roles_id": 6,
                "func_id": "XMGL",
                "id": 10,
                "desc": null
            }
        ],
        "id": 1,  
        "projects_ids": [  // 当前角色所关联的项目IDS
            3,
            4
        ]
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

