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
                "waters_id": 23  // 水域ID
            },
     ]
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

