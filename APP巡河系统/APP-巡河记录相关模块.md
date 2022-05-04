# APP-巡河记录相关模块

## 巡河记录-年筛选(图标)：

### 接口地址：/v1/wisdom/app/patrol_task/year/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | INT  | 是       | 水域ID列表 |      |
| year     | INT  | 是       | 年         |      |

### 请求示例:

```bash
{"year": 2022, "watersId": 62}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "count": 1,  // 数量
            "c_time": "2022-03"  // 月份
        },
        {
            "count": 11,
            "c_time": "2022-04"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 巡河记录-月筛选(图标)：

### 接口地址：/v1/wisdom/app/patrol_task/month/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | INT  | 是       | 水域ID列表 |      |
| year     | INT  | 是       | 年         |      |
| month    | INT  | 是       | 月         |      |

### 请求示例:

```bash
{"year": 2022, "watersId": 62, "month": 4}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "count": 3, // 数量
            "c_time": "04-06" // 时间
        },
        {
            "count": 2, // 数量
            "c_time": "04-07" // 时间
        },
        {
            "count": 1,
            "c_time": "04-09"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 巡河记录-周筛选(图标)：

### 接口地址：/v1/wisdom/app/patrol_task/day/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | INT  | 是       | 水域ID列表 |      |
| dataList | LIST | 是       | 日期       |      |

### 请求示例:

```bash
{
    "dataList": [
        "2022-04-06",
        "2022-04-07",
        "2022-04-09"
    ],
    "watersId": 62
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "count": 3, // 数量
            "cTime": "2022-04-06" // 时间轴
        },
        {
            "count": 2,
            "cTime": "2022-04-07"
        },
        {
            "count": 1,
            "cTime": "2022-04-09"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 巡河记录-年统计(报表)：

### 接口地址：/v1/wisdom/app/patrol_task/year/list/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | INT  | 是       | 水域ID列表 |      |
| year     | INT  | 是       | 年         |      |

### 请求示例:

```bash
{
    "year":2022,
    "watersId": 62
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "cleanCount": {  // 水面保洁信息
                "weight__sum": null // 垃圾重量
            },
            "patrolData": { // 巡河数据
                "weight__sum": 0.0, // 巡河任务重垃圾重量
                "duration__sum": 37, // 巡河时长
                "realDistance__sum": 0.898 // 巡河距离
            },
            "alarmCount": 0, // 预警事件
            "cTime": "2022-03" // 时间日期
        },
        {
            "cleanCount": {
                "weight__sum": null
            },
            "patrolData": {
                "weight__sum": 0.0,
                "duration__sum": 68871,
                "realDistance__sum": 5.404999999999999
            },
            "alarmCount": 3,
            "cTime": "2022-04"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 巡河记录-月、日统计(报表)：

> 巡河记录、月、如统计报表的格式相似，使用一个接口。
>
> 月统计：举个栗子：
>
> 2022-03-01:00:00:00 ~ 2022-03-30 23:59:59
>
> 周统计：举个栗子:
>
> 2022-03-01:00:00:00 ~ 2022-03-07 23:59:59

### 接口地址：/v1/wisdom/app/patrol_task/month/list/?watersId=62&sTime=2022-04-01&eTime=2022-04-30

### 请求方式：POST

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名       | 备注 |
| -------- | ------ | -------- | ---------- | ---- |
| watersId | INT    | 是       | 水域ID列表 |      |
| sTime    | STRING | 是       | 开始时间   |      |
| eTime    | STRING | 是       | 结束时间   |      |

### 请求示例:

```bash
?watersId=62&sTime=2022-04-01&eTime=2022-04-30
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "weight": "", // 水面垃圾
            "e_latitude": "30.612241", // 终点位置
            "ship_id": 65, // 船的ID
            "s_time": 1651075200, // 开始时间
            "duration": 3060, // 巡河时长 
            "alarm_count": 0, // 预警事件
            "id": 143, // 巡河ID 
            "s_location": "1", // 起点位置
            "waters_id": 62,  // 水域ID
            "c_time": "2022-04-28T09:00:37.961288Z",  // 开始时间
            "waters__name": "锦江府河",  // 水域名称 
            "e_longitude": "104.085385",  // 结束经度
            "real_distance": "0.0", // 实际距离 
            "e_location": "1",  // 终点位置
            "start_time": 1651208978,  // 开始时间
            "ship__number": "0025",  // 船的编号
            "distance": "1",  // 距离
            "name": "锦江府河",  // 任务名称
            "s_longitude": "104.0847",  // 气短经度
            "s_latitude": "30.611497",  // 起点 纬度
            "end_time": 1651212038,  // 结束时间
            "ship__name": "QDF-0025" // 船的名称
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 

## 巡河记录-年统计(报表)下载：

### 接口地址：/v1/wisdom/app/patrol_task/download/year/?year=2022&watersId=62

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名       | 备注 |
| -------- | ---- | -------- | ---------- | ---- |
| watersId | INT  | 是       | 水域ID列表 |      |
| year     | INT  | 是       | 年         |      |

### 请求示例:

```bash
?year=2022&watersId=62
```

### 响应

#### 200

* 

## 巡河记录-月-日统计(报表)下载：

### 接口地址：/v1/wisdom/app/patrol_task/download/year/?watersId=62&sTime=2022-04-01&eTime=2022-04-30

### 请求方式：POST

### 请求参数：

| 参数名   | 类型   | 是否必传 | 命名       | 备注 |
| -------- | ------ | -------- | ---------- | ---- |
| watersId | INT    | 是       | 水域ID列表 |      |
| sTime    | STRING | 是       | 开始日期   |      |
| eTime    | STRING | 是       | 结束日期   |      |

### 请求示例:

```bash
?watersId=62&sTime=2022-04-01&eTime=2022-04-30
```

### 响应

#### 200

* 

