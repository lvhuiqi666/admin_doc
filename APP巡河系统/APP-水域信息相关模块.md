# APP-水域信息相关模块

## 水域信息轮播图：

### 接口地址：/v1/wisdom/app/map/waters/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型 | 是否必传 | 命名   | 备注 |
| --------- | ---- | -------- | ------ | ---- |
| watersIds | LIST | 是       | 水域ID |      |

### 请求示例：

```bash
{
    "watersIds": [
        61,
        62
    ]
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "area_id": null,  // 区域ID
            "name": "锦江府河", // 水域名称
            "level": 2, // 水域等级： 1:省级、2:市级、3:区级、4:镇级、5:乡级
            "city_id": 27, // 城市ID
            "city__name": "成都市",  // 城市名称
            "province__name": "四川省", // 省份名称
            "area__name": null, // 区域名称
            "province_id": 13,  // 省份ID
            "quality": 2,  // 水质等级: 1.I、2:II、3:III、4:IV、5:V、6:VI
            "id": 62
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 水域信息列表页：

> 水域详情页面数据，也从列表页数据进行获取

### 接口地址：/v1/wisdom/app/waters/list/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型   | 是否必传 | 命名     | 备注                                  |
| --------- | ------ | -------- | -------- | ------------------------------------- |
| watersIds | LIST   | 是       | 水域ID   |                                       |
| category  | INT    | 否       | 水域类别 | 1:海洋、2:河流、3:胡泊、4:水库 (筛选) |
| name      | STRING | 否       | 水域名称 | 筛选                                  |

### 请求示例：

```bash
{
    "watersIds": [
        61,
        62,
        63
    ],
    "category": 3
}
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,
        "list": [
            {
                "id": 63,  // 水域id
                "category": 3,  // 分类、1:海洋、2:河流、3:湖泊、4:水库
                "quality": 2, // 等级： 1：I、2：II、3：III、4:IV、5：V、6：VI
                "level": 2, // 水域等级 1:省级、2:市级、3:区级、4:镇级、5:乡级
                "areas": "",  // 区域面积
                "sLng": "", // 起点经度
                "sLat": "", // 起点纬度
                "eLng": "",  // 终点经度
                "eLat": "", // 终点纬度
                "name": "大坂洋",  // 水域名称
                "number": "DBY-0001",  // 水域编码
                "provinceInfo": {  // 省份信息
                    "lat": "30.251057",
                    "lng": "120.193968",
                    "id": 1,
                    "name": "浙江省"
                },
                "cityInfo": {  // 城市信息
                    "lat": "30.0018",
                    "lng": "120.58316",
                    "id": 14,
                    "name": "绍兴市"
                },
                "areaInfo": {  // 区域信息
                    "id": 28,
                    "name": "孙端街道"
                },
                "townInfo": {}, // 城镇信息
                "villageInfo": {},  // 乡镇信息
                "user": "叶文明",  // 湖长
                "mobile": "15550067666",  // 湖长联系方式
                "job": "运维人员",  // 湖长职务
                "scope": "",  // 湖长工作范围
                "imageAddress": ""  // 水域封面图地址
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

