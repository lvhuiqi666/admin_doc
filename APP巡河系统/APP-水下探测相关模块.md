# APP-水下探测相关模块

## 获取水下探测任务信息：

> 水域的ID, 根据登录时的账号进行获取

### 接口地址：/v1/wisdom/app/detect/task/list/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | LIST | 是       | 水域ID列表 |      |

### 请求示例:

```bash
{"watersId": [35,58,59]}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "area_id": 26,
            "ship__name": "QDF-0001",
            "waters_id": 59,
            "c_time": "2020-09-02 00:00:00",
            "city_id": 25,
            "waters__name": "巩义黄河",
            "city__name": "郑州市",
            "province__name": "河南省",
            "waters__number": "FYHH",
            "area__name": "中原区",
            "ship__number": "0001",
            "ship_id": 15,
            "province_id": 12,
            "id": 21
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取水下探测成果列表页：

> 交互逻辑，首先进来调佣使用Image_address，后端已经把视频 + 所有点位图片都已经返回

### 接口地址：/v1/wisdom/app/detect/result/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| detectId | INT  | 是       | 水域探测ID |      |

### 请求示例:

```bash
{"detectId": 8}
```

### 响应

#### 200

```bash
{
    "data": {
        "resultList": [  // 水下探测列表
            {
                "name": "疑似暗管017", // 水下异物名称
                "c_time": "2021-12-10 15:59:59",  // 日期
                "memo": null, // 备注
                "number": "0017",  // 编号
                "image_address": "http://image.yimingkeji.com/pr/16.png",  // 图片点位
                "lat": "27.77953241459639", // 纬度
                "lng": "120.6443970019125", // 经度
                "id": 30
            },
        ],
        "id": 8,  // 水下探测ID
        "imageAddress": "http://image.yimingkeji.com/river/1639988842220OWesG.mp4" // 水下探测视频
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

