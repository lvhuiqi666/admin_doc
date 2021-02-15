# 管理后台-Web官网(联系地址、轮播图)

## 发布联系手机号与地址：

### 地址：/admin/contact/

### 请求方式：post

### 请求参数：

* mobile：string 类型 手机号
* email：string 类型 邮箱

### 响应

#### 200

```bas
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改联系人手机号与地址：

### 地址：/admin/contact/

### 请求方式：put

### 请求参数：

* contactId：int 联系ID
* mobile：string 类型 手机号
* email：string 类型 邮箱

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除联系人手机号与地址：

### 地址：/admin/contact/

### 请求方式：delete

### 请求参数：

* contactId：int 联系ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 允许发布联系人手机号与地址：

### 地址：/admin/is_contacted/

### 请求方式：post

### 请求参数：

* contactId：int 联系ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 不允许发布联系人手机号与地址：

### 地址：/admin/is_contacted/

### 请求方式：put

### 请求参数：

* contactId：int 联系ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 联系人手机号与地址列表页：

### 地址：/admin/contact/list/

### 请求方式：get

### 请求参数：

* 无

### 响应

#### 200

```bash
{
    "data": {
        "count": 2, // 总数
        "list": [
            {
                "id": 4,  // 联系ID
                "mobile": "1231321",  // 手机号
                "email": "3123131232", // email 邮箱
                "isPublished": false  // false 表示不允许发布, true 表示允许发布
            },
            {
                "id": 2,
                "mobile": "131231231232",
                "email": "12313213212@163.com",
                "isPublished": false
            }
        ],
        "links": {
            "previous": null,  // 上一页
            "next": null   // 下一页
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 发布轮播图：

### 地址：/admin/web_carousel/

### 请求方式：post

### 请求参数：

* imageUrl：sting 轮播图地址

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改轮播图：

### 地址：/admin/web_carousel/

### 请求方式：put

### 请求参数：

* carouseId：int 轮播图id
* imageUrl：sting 轮播图地址

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除轮播图：

### 地址：/admin/web_carousel/

### 请求方式：delete

### 请求参数：

* carouseId：int 轮播图id

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 轮播图列表页：

### 地址：/admin/web_carousel/list/

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

## 发布轮播接口：

### 地址：/admin/web_carousel/publish/

### 请求方式：post

### 请求参数：

* carouseId：int 轮播图ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 取消发布轮播接口：

### 地址：/admin/web_carousel/publish/

### 请求方式：put

### 请求参数：

* carouseId：int 轮播图ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 创建联系我们接口：

### 地址：/admin/contact_us/

### 请求方式：post

### 请求参数：

* name：string 姓名
* mobile： string 手机号
* email：string 邮箱
* content：string 内存

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改联系我们接口：

### 地址：/admin/contact_us/

### 请求方式：put

### 请求参数：

* usId：int 联系我们ID

* name：string 姓名
* mobile： string 手机号
* email：string 邮箱
* content：string 内存

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除联系我们接口：

### 地址：/admin/contact_us/

### 请求方式：delete

### 请求参数：

* usId: int 联系我们ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 已经联系接口：

### 地址：/admin/contact_us/publish/

### 请求方式：post

### 请求参数：

* usId：int 联系ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 未联系接口：

### 地址：/admin/contact_us/publish/

### 请求方式：put

### 请求参数：

* usId：int 联系ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 联系我们列表页接口：

### 地址：/admin/contact_us/list/

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
                "id": 1, // 联系我们ID
                "name": "123",  // 姓名
                "email": "123",  // 邮箱
                "mobile": "123", // 手机号
                "content": "123",  // 内容
                "isContacted": false  // false 表示未联系 true 表示已联系
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

## 创建岗位接口：

### 地址：/admin/recruitment/

### 请求方式：post

### 请求参数：

* content：string 内容

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改岗位接口：

### 地址：/admin/recruitment/

### 请求方式：put

### 请求参数：

* recId：int 岗位ID
* content：string 内容

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除岗位接口：

### 地址：/admin/recruitment/

### 请求方式：delete

### 请求参数：

* recId：int 岗位ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 已经发布接口：

### 地址：/admin/recruitment/publish/

### 请求方式：post

### 请求参数：

* recId：int 岗位ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 取消发布接口：

### 地址：/admin/recruitment/publish/

### 请求方式：put

### 请求参数：

* recId：int 岗位ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 岗位列表页接口：

### 地址：/admin/recruitment/list/

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
                "isPublished": false  // false 不允许发布  true 允许发布
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

## 创建官网新闻接口：

### 地址：/admin/web_news/

### 请求方式：post

### 请求参数：

* title：string 标题
* cover_img：string 封面图
* content：string 内容

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改官网新闻接口：

### 地址：/admin/web_news/

### 请求方式：put

### 请求参数：

* newsId：int 新闻ID
* title：string 标题
* cover_img：string 封面图
* content：string 内容

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除官网新闻接口：

### 地址：/admin/web_news/

### 请求方式：delete

### 请求参数：

* newsId：int 新闻ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 已经发布接口：

### 地址：/admin/web_news/publish/

### 请求方式：post

### 请求参数：

* newsId：int 新闻ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 取消发布接口：

### 地址：/admin/web_news/publish/

### 请求方式：put

### 请求参数：

* newsId：int 新闻ID

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 后台新闻列表页接口：

### 地址：/admin/web_news/list/

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
                "title": "123", // 新闻标题
                "coverImg": "123",  // 新闻的封面图
                "content": "123",  // 新闻的内容
                "isPublished": false,  // 是否推送
                "cTime": "2021-02-16T04:17:21+08:00"  // 创建时间
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

