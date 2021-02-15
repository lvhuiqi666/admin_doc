# Web官网

## 联系手机号与地址列表：

### 地址：/web/contact_list/

### 请求方式：get

### 请求参数：

* 无

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,  // 总数
        "list": [
            {
                "id": 5,  // 联系ID
                "mobile": "12313213",  // 手机号
                "email": "3123122",  // 邮箱号
                "isPublished": true  // 是否发布
            }
        ],
        "links": {
            "previous": null,  // 上一页
            "next": null // 下一页
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 轮播图列表：

### 地址：/web/carousel_list/

### 请求方式：get

### 请求参数：

* 无

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,
        "list": [
            {
                "id": 1,  // 轮播图id
                "index": 1,  // 轮播图排序索引
                "imageUrl": "12313212",  // 轮播图的外链地址
                "isPublished": false,  // 是否推送 false 表示不推送  true 表示推送
                "eTime": "2021-02-16T03:19:46+08:00",  // 修改时间
                "cTime": "2021-02-16T03:19:49+08:00"  // 创建时间
            }
        ],
        "links": {
            "previous": null,  // 上一页
            "next": null  // 下一页
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 岗位列表：

### 地址：/web/recruitment_list/

### 请求方式：get

### 请求参数：

* 无

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,
        "list": [
            {
                "id": 1,
                "content": "12313123",  // 内容
                "isPublished": true  // false 不允许发布  true 允许发布
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

## 新闻列表：

### 地址：/web/recruitment_list/

### 请求方式：get

### 请求参数：

* 无

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,
        "list": [
            {
                "id": 1, // 新闻ID
                "title": "123",  // 新闻标题
                "coverImg": "123", // 新闻封面 
                "content": "123",  // 新闻内容
                "isPublished": true,  // 是否推送
                "cTime": "2021-02-16T04:17:21+08:00"  // 创建时间
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

