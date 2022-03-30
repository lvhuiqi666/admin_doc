# APP-广告模块&新闻模块

## 获取广告列表：

### 接口地址：/v1/wisdom/app/advert/list/

### 请求方式：POST

### 请求参数：

* 

### 请求示例：

* 

### 响应

#### 200

```bash
{
    "data": {
        "count": 2,
        "list": [
            {
                "id": 1,  // 广告ID
                "title": "3标题",  // 广告标题
                "fileAddress": "3地址",  // 广告链接地址
                "coverImg": "3xxxxx", // 广告封面图
                "index": 3, // 排序
                "cTime": "1647792000.000000",  // 发布时间
                "isPublished": false
            }
        "links": {
            "previous": null,
            "next": null
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取新闻列表：

### 接口地址：/v1/wisdom/app/news/list/

### 请求方式：POST

### 请求参数：

* 

### 请求示例：

* 

### 响应

#### 200

```bash
{
    "data": {
        "count": 3,
        "list": [
            {
                "id": 5, // 新闻ID
                "title": "标题",  // 新闻标题
                "fileAddress": "地址", // 新闻链接地址
                "coverImg": "xxxxx", // 新闻封面图
                "index": 1, // 暂无
                "cTime": "1648654839.925197", // 新闻发布时间
                "isPublished": false,
                "content": "内容" // 新闻正文
            },
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

