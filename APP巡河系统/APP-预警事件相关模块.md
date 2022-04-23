# APP-预警事件相关模块

## 预警事件列表页：

### 接口地址：/v1/wisdom/app/alert/list/

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名         | 备注         |
| -------- | ------ | -------- | ------------ | ------------ |
| aiSId    | INT    | 否       | 二级事件类型 | 筛选         |
| watersId | INT    | 是       | 水域ID       |              |
| sTime    | STRING | 否       | 开始时间     | 筛选YY-MM-DD |
| eTime    | STRING | 否       | 结束时间     | 筛选YY-MM-DD |

### 请求示例:

```bash
?watersId=56&aiSId=1
```

### 响应

#### 200

```bash
// 具体看详情
{
    "data": {
        "count": 88,
        "list": [
            {
                "id": 89,  // 预警ID
                "address": "xxxx",  // 地址
                "lng": "1231", // 经度
                "lat": "123",  // 纬度
                "isReported": true,  // true 已报： false 未报
                "sTime": "1628179200.000000",  // 开始时间
                "eTime": "1628179200.000000", // 结束时间
                "provinceInfo": {  // 省份信息
                    "id": 1,
                    "name": "浙江省"
                },
                "cityInfo": { // 城市信息
                    "id": 1,
                    "name": "杭州市"
                },
                "areaInfo": {  // 区域信息
                    "id": 1,
                    "name": "萧山区"
                },
                "townInfo": {},  // 城镇
                "villageInfo": {},  // 乡镇
                "shipInfo": {  // 船的信息
                    "userName": "吕品品123", // 运维人员
                    "userId": 1,// 运维人员ID
                    "id": 2,  
                    "userMobile": "13069634826",  // 联系方式
                    "number": "0002"  // 船的编码
                },
                "watersInfo": { // 水域信息
                    "id": 2, // 水域ID
                    "name": "西湖"  // 水面名称
                },
                "userInfo": {  // 河长信息
                    "mobile": "13069634826",
                    "id": 1,
                    "name": "吕品品123"
                },
                "aiP_info": {  // 一级预警分类
                    "id": 1,
                    "name": "水上识别"
                },
                "aiS_info": {  // 二级预警分类
                    "text": "河长办、环保局、城管局",
                    "id": 1,
                    "name": "生活垃圾"
                },
                "aiT_info": { // 三级预警分类
                    "id": 1,
                    "name": "塑料袋"
                }
            }
        ],
        "links": {
            "previous": null,
            "next": "http://127.0.0.1:8000/v1/admin/alarm/list/?page=2"
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 预警事件-年筛选：

### 接口地址：/v1/wisdom/app/alert/year/list/?year=2022&watersId=15

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| year     | INT  | 是       | 年     |      |
| watersId | INT  | 是       | 水域ID |      |

### 请求示例:

```bash
?year=2022&watersId=15
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "sum": 461,// 当天的总数
            "aiS_list": [
                {
                    "count": 338,  // 数量
                    "ai_s": 2,  // 二级分类别
                    "ai_s__name": "水草海藻"
                },
                {
                    "count": 74,
                    "ai_s": 1,
                    "ai_s__name": "生活垃圾"
                },
                {
                    "count": 82,
                    "ai_s": 4,
                    "ai_s__name": "堤坝安全"
                },
                {
                    "count": 5,
                    "ai_s": 9,
                    "ai_s__name": "非法捕鱼"
                },
                {
                    "count": 1,
                    "ai_s": 7,
                    "ai_s__name": "阻水生物"
                }
            ],
            "sTime": "2022-01" // 日期
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 预警事件-月筛选：

### 接口地址：/v1/wisdom/app/alert/month/list/?watersId=15&year=2022&month=4

### 请求方式：GET

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| year     | INT  | 是       | 年     |      |
| month    | INT  |          |        |      |
| watersId | INT  | 是       | 水域ID |      |

### 请求示例:

```bash
?watersId=15&year=2022&month=4
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "sum": 1, // 总数
            "aiS_list": [
                {
                    "count": 1,  // 类型总数
                    "ai_s": 1,
                    "ai_s__name": "生活垃圾"
                }
            ],
            "sTime": "2022-04-03"  // 月份日期
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 预警事件详情接口：

> 当前接口，在预警事件、月筛选、年筛设计图中，下面的筛选列表页中使用，因为年筛选与日筛选、月筛选的表示方式不同。

### 接口地址：/v1/wisdom/app/alert/month/detail/?watersId=15&cTime=2022-04

### 请求方式：GET

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名        | 备注    |
| -------- | ------ | -------- | ----------- | ------- |
| cTime    | STRING | 是       | 年-月字符串 | YYYY-MM |
| watersId | INT    | 是       | 水域ID      |         |

### 请求示例:

```bash
?watersId=15&year=2022&month=4
```

### 响应

#### 200

```bash
// 具体看详情
{
    "data": {
        "count": 88,
        "list": [
            {
                "id": 89,
                "address": "xxxx",
                "lng": "1231",
                "lat": "123",
                "isReported": true,
                "sTime": "1628179200.000000",
                "eTime": "1628179200.000000",
                "provinceInfo": {
                    "id": 1,
                    "name": "浙江省"
                },
                "cityInfo": {
                    "id": 1,
                    "name": "杭州市"
                },
                "areaInfo": {
                    "id": 1,
                    "name": "萧山区"
                },
                "townInfo": {},
                "villageInfo": {},
                "shipInfo": {
                    "userName": "吕品品123",
                    "userId": 1,
                    "id": 2,
                    "userMobile": "13069634826",
                    "number": "0002"
                },
                "watersInfo": {
                    "id": 2,
                    "name": "西湖"
                },
                "userInfo": {
                    "mobile": "13069634826",
                    "id": 1,
                    "name": "吕品品123"
                },
                "aiP_info": {
                    "id": 1,
                    "name": "水上识别"
                },
                "aiS_info": {
                    "text": "河长办、环保局、城管局",
                    "id": 1,
                    "name": "生活垃圾"
                },
                "aiT_info": {
                    "id": 1,
                    "name": "塑料袋"
                }
            }
        ],
        "links": {
            "previous": null,
            "next": "http://127.0.0.1:8000/v1/admin/alarm/list/?page=2"
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

