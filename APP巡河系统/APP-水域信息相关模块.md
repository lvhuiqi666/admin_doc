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

## 定点水质列表页：

> 将在此接口把水质指标全部返回, 客户端做筛选从本地缓存中取数据来做。

### 接口地址：/v1/wisdom/app/fixed_point/list/

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名     | 备注     |
| -------- | ------ | -------- | -------- | -------- |
| watersId | INT    | 是       | 水域ID   |          |
| sTime    | STRING | 是       | 开始时间 | YY-MM-DD |
| eTime    | STRING | 是       | 结束时间 | YY-MM-DD |

### 请求示例：

```bash
?watersId=22&sTime=2021-06-09&eTime=2021-06-11
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "water_quality_id": 17,  // 水质水域ID
            "c_time": "2021-06-08T23:45:28Z", // 日期
            "k": "0.0", // 钾离子
            "water_quality__name": "后塘河水域水质-001", // 水质名称
            "water_quality__number": "HTH-0001",// 水质的编号
            "oxy_saturation": "1.97", // 溶解氧饱和度
            "diss_oxy": "24.8", // 溶解氧
            "nh4": "1.0", // nh4
            "cod": "76.3",  // 化学需氧量
            "nh3": "0",  // nh3
            "ph": "7.34", // ph
            "turbidity": "60.8", // 浊度
            "id": 18 // 信息表ID
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 动态水质列表页：

### 接口地址：/v1/wisdom/app/dynamic/list/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名     | 备注         |
| -------- | ---- | -------- | -------- | ------------ |
| watersId | INT  | 是       | 水域ID   |              |
| tsList   | LIST | 是       | 日期时间 | 毫秒级时间戳 |

### 请求示例：

```bash
{
    "watersId": 22,
    "tsList": [1623888000000, 1624320000000]
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "result_list": [  // 水质相关信息
                {
                    "c_data": {
                        "id": 1,
                        "name": "杭州市"
                    },
                    "p_data": {
                        "id": 1,
                        "name": "浙江省"
                    },
                    "turbidity": "[u'turb']",
                    "water_quality": {
                        "id": 5,
                        "name": "断面003"
                    },
                    "wgs84_lat": "31.4001943",
                    "c_time": 1631750400000.0,
                    "chlorophy": "33",
                    "k": "23",
                    "_cls": "wisdom_waters_service.models.DynamicWaterQuality",
                    "oxy_saturation": "11",
                    "diss_oxy": "123",
                    "nh4": "12",
                    "a_data": {
                        "id": 1,
                        "name": "萧山区"
                    },
                    "cod": "123.12",
                    "nh3": "3",
                    "s_time": 1631893159,
                    "ph": "7.1",
                    "_id": "6144b6a7a541dda8ff126385",
                    "wgs84_lng": "120.866966",
                    "ship": {
                        "number": "0017",
                        "id": 2,
                        "name": "西湖前进号"
                    },
                    "waters": {
                        "id": 2,
                        "name": "西湖"
                    }
                }
            ],
            "ts": 1631721600000.0  // 日期时间戳 毫秒
        },
        {
            "result_list": [
                {
                    "height": "4.66137361526",
                    "s_time": 1635651790,
                    "ship": {
                        "number": "0004",
                        "id": 2,
                        "name": "西湖前进号"
                    },
                    "c_data": {
                        "id": 1,
                        "name": "杭州市"
                    },
                    "wgs84_lat": "32.0371814",
                    "c_time": 1635651789578.0,
                    "a_data": {
                        "id": 1,
                        "name": "萧山区"
                    },
                    "ph": "",
                    "cod": "",
                    "waters": {
                        "id": 2,
                        "name": "西湖"
                    },
                    "nh4": "",
                    "nh3": "",
                    "oxy_saturation": "",
                    "_id": "617e10cdad0529004617726c",
                    "p_data": {
                        "id": 1,
                        "name": "浙江省"
                    },
                    "k": "",
                    "diss_oxy": "",
                    "_cls": "wisdom_waters_service.models.DynamicWaterQuality",
                    "water_quality": {
                        "id": 5,
                        "name": "断面003"
                    },
                    "chlorophy": "",
                    "turbidity": "",
                    "wgs84_lng": "118.752899"
                }
            ],
            "ts": 1635609600000.0
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}

```

## 报表-年度筛选：

### 接口地址：/v1/wisdom/app/water_quality/year/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     |      |

### 请求示例：

```bash
{
    "waterId": 15, "year":2020
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "avgData": {
                "nh3__avg": 2.183904761904762,
                "ph__avg": 7.230168534863196,
                "k__avg": 0.5874999999999999,
                "oxySaturation__avg": 1.48875,
                "cod__avg": 45.58163636363636,
                "turbidity__avg": 51.95854545454545,
                "dissOxy__avg": 8.66214090909091,
                "nh4__avg": 1.55
            },
            "sTime": "2021-06"  // 月份
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 报表-月度筛选：

### 接口地址：/v1/wisdom/app/water_quality/month/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     |      |
| month    | INT  | 是       | 月份   |      |

### 请求示例：

```bash
{
    "waterId": 15, "year":2021, "month":6
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "avgData": {
                "nh3__avg": 2.183904761904762,
                "ph__avg": 7.230168534863196,
                "k__avg": 0.5874999999999999,
                "oxySaturation__avg": 1.48875,
                "cod__avg": 45.58163636363636,
                "turbidity__avg": 51.95854545454545,
                "dissOxy__avg": 8.66214090909091,
                "nh4__avg": 1.55
            },
            "sTime": "06-22"  // 日期
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 报表-周筛选：

> 周前端做判断，传入的指标为日期

### 接口地址：/v1/wisdom/app/water_quality/day/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注                           |
| -------- | ---- | -------- | ------ | ------------------------------ |
| watersId | INT  | 是       | 水域ID |                                |
| dateList | LIST | 是       | 日期   | 客户端判断周后端接受参数为日期 |

### 请求示例：

```bash
{
    "dateList": [
        "2021-06-18",
        "2021-06-19",
        "2021-06-20",
        "2021-06-21"
    ],
    "waterId": 15
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "avgData": {
                "nh3__avg": 2.183904761904762,
                "ph__avg": 7.230168534863196,
                "k__avg": 0.5874999999999999,
                "oxySaturation__avg": 1.48875,
                "cod__avg": 45.58163636363636,
                "turbidity__avg": 51.95854545454545,
                "dissOxy__avg": 8.66214090909091,
                "nh4__avg": 1.55
            },
            "sTime": "2021-06-18"  // 年月日
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 报表-年报表下载接口：

> 返回文件的二进制

### 接口地址：/v1/wisdom/app/download/water_quality/year/?waterId=15&year=2021

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年份   |      |

### 请求示例：

```bash
/year/?waterId=15&year=2021
```

### 响应

#### 200

```bash
# 文件二进制
```

## 报表-月报表下载接口：

> 返回文件的二进制

### 接口地址：/v1/wisdom/app/download/water_quality/month/?waterId=15&year=2021&month=6

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年份   |      |
| month    | INT  | 是       | 月份   |      |

### 请求示例：

```bash
?waterId=15&year=2021&month=6
```

### 响应

#### 200

```bash
# 文件二进制
```

## 报表-月报表下载接口：

> 返回文件的二进制

### 接口地址：/v1/wisdom/app/download/water_quality/day/??date=2021-06-18,2021-06-19,2021-06-20&waterId=15

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名   | 备注           |
| -------- | ------ | -------- | ------ | -------------- |
| watersId | INT    | 是       | 水域ID |                |
| date     | STRING | 是       | 日期   | 字符串逗号拼接 |

### 请求示例：

```bash
?date=2021-06-18,2021-06-19,2021-06-20&waterId=15
```

### 响应

#### 200

```bash
# 文件二进制
```

