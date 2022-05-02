# APP-水面保洁相关模块

## 水面保洁列表页：

### 接口地址：/v1/wisdom/app/clean/list/?watersId=15

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名     | 备注         |
| -------- | ------ | -------- | -------- | ------------ |
| watersId | INT    | 是       | 水域ID   |              |
| sTime    | STRING | 否       | 开始时间 | 筛选YY-MM-DD |
| eTime    | STRING | 否       | 结束时间 | 筛选YY-MM-DD |

### 请求示例:

```bash
?watersId=56
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 1266,
        "list": [
            {
                "id": 2116,
                "provinceInfo": {
                    "lat": "30.251057",
                    "lng": "120.193968",
                    "id": 1,
                    "name": "浙江省"
                },
                "cityInfo": {
                    "lat": "27.775828",
                    "lng": "120.647685",
                    "id": 8,
                    "name": "温州市"
                },
                "areaInfo": {
                    "id": 12,
                    "name": "瑞安市"
                },
                "townInfo": {},
                "villageInfo": {},
                "shipInfo": {
                    "id": 24,
                    "name": "QDF-0010",
                    "number": "0010"
                },
                "watersInfo": {
                    "id": 15,
                    "name": "中塘河"
                },
                "sTime": "1650988800.000000",
                "eTime": "1650988800.000000",
                "category": null,
                "cleaningType": null,
                "areas": null,
                "distance": null,
                "weight": null,
                "user": "安鹏",
                "mobile": "13456905984",
                "memo": null,
                "runS_time": "1651018815",
                "runE_time": "1651019130",
                "duration": "315",
                "runAmStartTime": "30015",
                "runAmEndTime": "30330",
                "runPmStartTime": null,
                "runPmEndTime": null
            }
        ],
        "links": {
            "previous": null,
            "next": "http://127.0.0.1:8000/v1/wisdom/app/clean/list/?page=2&watersId=15"
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 水面保洁-年筛选报表：

### 接口地址：/v1/wisdom/app/clean/year/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     | 2022 |

### 请求示例:

```bash
{
    "watersId": 15, "year": 2022
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "cleaningList": [ // 保洁列表
                {
                    "cleaning_type": null, // 保洁类型
                    "weight": null // 垃圾重量
                },
                {
                    "cleaning_type": 1,
                    "weight": 13375.0
                },
                {
                    "cleaning_type": 2,
                    "weight": 19560.0
                }
            ],
            "sTime": "2021-12" // 保洁月份
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 水面保洁-月筛选报表：

### 接口地址：/v1/wisdom/app/clean/month/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     | 2022 |
| month    | INT  | 是       | 月     | 4    |

### 请求示例:

```bash
{
    "watersId": 15, "year": 2022, "month":4
}
```

### 响应

#### 200

```bash
{
    "data": [       
        {
            "cleaningList": [ // 保洁信息
                {
                    "cleaning_type": null, // 清洁类型 1:水上植物、2:生活垃圾、3:油污收集、4:水下植物
                    "weight": null // 垃圾重量
                },
                {
                    "cleaning_type": 1, 
                    "weight": 1000.0
                },
                {
                    "cleaning_type": 2,
                    "weight": 75.0
                }
            ],
            "sTime": "04-24"
        },
        {
            "cleaningList": [
                {
                    "cleaning_type": null,
                    "weight": null
                },
                {
                    "cleaning_type": 1,
                    "weight": 570.0
                },
                {
                    "cleaning_type": 2,
                    "weight": 415.0
                }
            ],
            "sTime": "04-25"
        },
        {
            "cleaningList": [
                {
                    "cleaning_type": null,
                    "weight": null
                },
                {
                    "cleaning_type": 1,
                    "weight": 800.0
                },
                {
                    "cleaning_type": 2,
                    "weight": 75.0
                }
            ],
            "sTime": "04-26"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 水面保洁-周报(日筛选)

### 接口地址：/v1/wisdom/app/clean/day/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名     | 备注 |
| -------- | ---- | -------- | -------- | ---- |
| watersId | INT  | 是       | 水域ID   |      |
| dataList | LIST | 是       | 日期范围 |      |

### 请求示例:

```bash
{
    "dataList": [
        "2022-04-26",
        "2022-04-27",
        "2022-04-28"
    ],
    "watersId": 15
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "cleaningList": [ // 保洁数据列表
                {
                    "cleaning_type": 1, // 保洁类型
                    "weight": 500.0  // 垃圾重量
                },
                {
                    "cleaning_type": 2,
                    "weight": 75.0
                }
            ],
            "sTime": "2022-04-26"  // 时间轴
        },
        {
            "cleaningList": [],
            "sTime": "2022-04-27"
        },
        {
            "cleaningList": [
                {
                    "cleaning_type": 1,
                    "weight": 500.0
                },
                {
                    "cleaning_type": 2,
                    "weight": 20.0
                },
                {
                    "cleaning_type": null,
                    "weight": null
                }
            ],
            "sTime": "2022-04-28"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 水面保洁-下方列表详情(月、日筛选下方展示详情列表页)

### 接口地址：/v1/wisdom/app/clean/range/day/?sTime=2022-05-02 00:00:00&eTime=2022-05-28 23:59:59&watersId=15

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名     | 备注       |
| -------- | ------ | -------- | -------- | ---------- |
| watersId | INT    | 是       | 水域ID   |            |
| sTime    | STRING | 是       | 开始时间 | 时间字符串 |
| eTime    | STRING | 是       | 结束时间 | 时间字符串 |

### 请求示例:

```bash
?sTime=2022-05-02 00:00:00&eTime=2022-05-28 23:59:59&watersId=15
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 5,
        "list": [
            {
                "id": 2175,
                "provinceInfo": {
                    "lat": "30.251057",
                    "lng": "120.193968",
                    "id": 1,
                    "name": "浙江省"
                },
                "cityInfo": {
                    "lat": "27.775828",
                    "lng": "120.647685",
                    "id": 8,
                    "name": "温州市"
                },
                "areaInfo": {
                    "id": 12,
                    "name": "瑞安市"
                },
                "townInfo": {},
                "villageInfo": {},
                "shipInfo": {
                    "id": 16,
                    "name": "QDF-0006",
                    "number": "0006"
                },
                "watersInfo": {
                    "id": 15,
                    "name": "中塘河"
                },
                "sTime": "1651420800.000000",
                "eTime": "1651420800.000000",
                "category": null,
                "cleaningType": null,
                "areas": null,
                "distance": "17.007",
                "weight": null,
                "user": "安鹏",
                "mobile": "13456905984",
                "memo": null,
                "runS_time": "1651449602",
                "runE_time": "1651475468",
                "duration": "25866",
                "runAmStartTime": "28802",
                "runAmEndTime": "43104",
                "runPmStartTime": "43491",
                "runPmEndTime": "54668"
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

## 水面保洁-本地下载(年统计接口)：

### 接口地址：/v1/wisdom/app/clean/download/year/?year=2022&watersId=15

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     | 2022 |

### 请求示例:

```bash
?year=2022&watersId=15
```

### 响应

#### 200

* 无

## 水面保洁-本地下载(月统计接口)：

### 接口地址：/v1/wisdom/app/clean/download/month/?year=2022&watersId=15?month=4

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| watersId | INT  | 是       | 水域ID |      |
| year     | INT  | 是       | 年     | 2022 |
| month    | INT  | 是       | 月     |      |

### 请求示例:

```bash
?year=2022&watersId=15?month=4
```

### 响应

#### 200

* 无

## 水面保洁-本地下载(周统计接口)：

### 接口地址：/v1/wisdom/app/clean/download/day/?watersId=15&dataList=2022-04-22,2022-04-23,2022-04-24

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名     | 备注 |
| -------- | ------ | -------- | -------- | ---- |
| watersId | INT    | 是       | 水域ID   |      |
| dataList | STRING | 是       | 日期列表 |      |

### 请求示例:

```bash
?watersId=15&dataList=2022-04-22,2022-04-23,2022-04-24
```

### 响应

#### 200

* 无
