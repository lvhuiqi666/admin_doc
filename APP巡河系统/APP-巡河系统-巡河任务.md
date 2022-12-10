# APP-巡河任务

## 发布巡河任务：

### 接口地址：/wisdom/app/release/task/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名         | 备注 |
| ---------- | ------ | -------- | ------------ | ---- |
| name       | STRING | 是       | 任务名称     |      |
| sTime      | INT    | 是       | 发布时间戳   |      |
| company    | STRING | 是       | 发布单位     |      |
| watersId   | INT    | 是       | 水域的ID     |      |
| cUser      | STRING | 是       | 发布人       |      |
| areaData   | STRING | 是       | 所属区县     |      |
| patrolType | INT    | 是       | 巡河方式     |      |
| user       | STRING | 是       | 任务人       |      |
| distance   | STRING | 否       | 巡河距离     |      |
| sLocation  | STRING | 否       | 起点位置     |      |
| eLocation  | STRING | 否       | 终点位置     |      |
| sLng       | STRING | 否       | 起点经度坐标 |      |
| sLat       | STRING | 否       | 起点纬度坐标 |      |
| eLng       | STRING | 否       | 终点经度坐标 |      |
| eLat       | STRING | 否       | 终点纬度坐标 |      |
| content    | STRING | 否       | 任务内容     |      |

### 请求示例:

```bash
{
    "name": "西湖巡河",
    "sTime": 1647005538,
    "company": "西湖管委会",
    "cUser": "吕品品",
    "areaData": "杭州市西湖区",
    "patrolType": 1,
    "user": "仰望星空",
    "distance": "2.2",
    "sLocation": "云水光中",
    "eLocation": "慕才亭",
    "sLng": "120.640957927",
    "sLat": "31.3169841432",
    "eLng": "120.641169659",
    "eLat": "31.3156987507",
    "content": "日常巡河、游人和堤防安全、水质监测。",
    "watersId": 22
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 更新巡河任务：

### 接口地址：/v1/wisdom/app/update/task/

### 请求方式：POST

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名         | 备注 |
| ---------- | ------ | -------- | ------------ | ---- |
| taskId     | INT    | 是       | 巡河任务ID   |      |
| name       | STRING | 是       | 任务名称     |      |
| company    | STRING | 是       | 发布单位     |      |
| watersId   | INT    | 是       | 水域的ID     |      |
| cUser      | STRING | 是       | 发布人       |      |
| areaData   | STRING | 是       | 所属区县     |      |
| patrolType | INT    | 是       | 巡河方式     |      |
| user       | STRING | 是       | 任务人       |      |
| distance   | STRING | 否       | 巡河距离     |      |
| sLocation  | STRING | 否       | 起点位置     |      |
| eLocation  | STRING | 否       | 终点位置     |      |
| sLng       | STRING | 否       | 起点经度坐标 |      |
| sLat       | STRING | 否       | 起点纬度坐标 |      |
| eLng       | STRING | 否       | 终点经度坐标 |      |
| eLat       | STRING | 否       | 终点纬度坐标 |      |
| content    | STRING | 否       | 任务内容     |      |

### 请求示例:

```bash
{
    "taskId": 1,
    "name": "西湖巡河",
    "company": "西湖管委会",
    "cUser": "吕品品",
    "areaData": "杭州市西湖区",
    "patrolType": 1,
    "user": "仰望星空",
    "distance": "2.2",
    "sLocation": "云水光中",
    "eLocation": "慕才亭",
    "sLng": "120.640957927",
    "sLat": "31.3169841432",
    "eLng": "120.641169659",
    "eLat": "31.3156987507",
    "content": "日常巡河、游人和堤防安全、水质监测。",
    "watersId": 22
}
```

### 响应

#### 200

```bash
{
    "data": {
        "id": 1  // 巡河任务ID
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 新建巡河任务-船运行轨迹：

> 注意：先创建发布巡河任务, 拿到巡河任务的ID, 才可以进行给这个任务创建船的轨迹点

### 接口地址：/wisdom/app/create/task/track/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型 | 是否必传 | 命名             | 备注 |
| --------- | ---- | -------- | ---------------- | ---- |
| taskId    | INT  | 是       | 巡河任务ID       |      |
| trackList | LIST | 是       | 巡河任务轨迹列表 |      |

### 请求示例:

```bash
{
    "taskId": 6, // 巡河任务ID
    "trackList": [  // 注意: 列表中的顺序, 正序,  索引为0 表示第一个点位
        {
            "lng": "116.147856",  // 经度
            "lat": "39.925117"  // 纬度
        },
        {
            "lng": "116.168553",
            "lat": "39.899881"
        },
        {
            "lng": "116.212822",
            "lat": "39.87685"
        },
        {
            "lng": "116.230069",
            "lat": "39.846721"
        }
    ]
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改、清空巡河任务-船运行轨迹：

> 注意：当前接口用在第一次创建航线并且任务为待处理时调用(简单理解就是船没有开，第一次时的操作)

### 接口地址：/wisdom/app/clear/task/track/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型 | 是否必传 | 命名             | 备注                                       |
| --------- | ---- | -------- | ---------------- | ------------------------------------------ |
| taskId    | INT  | 是       | 巡河任务ID       |                                            |
| trackList | LIST | 是       | 巡河任务轨迹列表 | []传递为空说明是清空操作、不为空说明是更新 |

### 请求示例:

```bash
{
    "taskId": 6, // 巡河任务ID
    "trackList": [  // 注意: 列表中的顺序, 正序,  索引为0 表示第一个点位
        {
            "lng": "116.147856",  // 经度
            "lat": "39.925117"  // 纬度
        },
        {
            "lng": "116.168553",
            "lat": "39.899881"
        },
        {
            "lng": "116.212822",
            "lat": "39.87685"
        },
        {
            "lng": "116.230069",
            "lat": "39.846721"
        }
    ]
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 删除巡河任务接口：

> 注意：只有巡河任务为待处理, 才可进行删除

### 接口地址：/wisdom/app/delete/task/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| taskId | INT  | 是       | 巡河任务ID |      |
| userId | INT  | 是       | 操作人ID   |      |

### 请求示例:

```bash
{"taskId":6, "userId": 1}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取智慧巡河列表页接口：

> 注意：当前接口【待处理】、【处理中】、【已处理】状态通过status字段来区别，默认为【待处理】

### 接口地址：/wisdom/app/wisdom/river/list/

### 请求方式：GET

### 请求参数：

| 参数名     | 类型   | 是否必传 | 命名                | 备注                         |
| ---------- | ------ | -------- | ------------------- | ---------------------------- |
| userId     | INT    | 是       | 任务人用户ID        |                              |
| status     | INT    | 是       | 状态                | 1:待处理、2:处理中、3:已处理 |
| sTime      | INT    | 否       | 开始时间-时间戳(秒) | 筛选                         |
| eTime      | INT    | 否       | 结束时间-时间戳(秒) | 筛选                         |
| watersName | STRING | 否       | 水域名称            | 筛选                         |

### 请求示例:

```bash
{
    "userId": 5, // 用户ID
    "status": 3  // 状态
}
```

### 响应

#### 200

```bash
{
    "data": {
        "count": 1,  // 当前页总数
        "list": [
            {
                "id": 9,  // 巡河任务ID
                "patrolType": 1,  // 巡河任务类型: 1:无人船、2:无人机、3:人工
                "status": 3, // 状态: 1:待处理、2:处理中、3:已处理
                "areaData": "杭州市西湖区",  // 区域名称
                "name": "西湖巡河D",  // 任务名称
                "distance": "2.2",  // 距离
                "sTime": 1647005538,  // 发布时间戳
                "cTime": "1647008383.706826",  // 发布毫秒时间戳
                "cUser": "吕品品",  // 发布人名
                "user": "仰望星空", // 任务人名
                "sLocation": "云水光中",  // 起点位置名称
                "eLocation": "慕才亭",  // 终点位置名称
                "cCompany": "西湖管委会", // 发布人公司
                "content": "日常巡河、游人和堤防安全、水质监测。",  // 发布内容
                "watersInfo": {  // 水域相关信息
                    "id": 22,
                    "name": "后塘河"
                },
                "shipInfo": {  // 船舶相关信息
                    "id": 33,
                    "name": "QDF-0020",
                    "number": "0020",
                    "streamAddress": "https://open.ys7.com/v3/openlive/G16325270_1_1.m3u8?expire=1670552894&id=390812221267427328&t=958444bf1e8181adbbef9e1b9ff3c3f98f05c6181ded5d7968647a3c3c5a3dcc&ev=100", // 船的实时流地址
                }
            }
        ],
        "links": {
            "previous": null, // 上一页
            "next": null  // 下一页
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 开始-巡河接口：

> 巡河任务相关信息, 从上个列表页带过来，船的实时流信息等在列表页都有返回

### 接口地址：/wisdom/app/start/patrol/river/

### 请求方式：POST

### 请求参数：

| 参数名            | 类型   | 是否必传 | 命名                             | 备注      |
| ----------------- | ------ | -------- | -------------------------------- | --------- |
| taskId            | INT    | 是       | 巡河任务ID                       |           |
| shipId            | INT    | 是       | 船的ID                           |           |
| startTime         | INT    | 是       | 开始巡河时间(秒时间戳)           |           |
| sLocation         | STRING | 是       | 开始位置                         |           |
| sLng              | STRING | 是       | 开始位置经度                     |           |
| sLat              | STRING | 是       | 结束位置纬度                     |           |
| user              | STRING | 是       | 任务人名                         |           |
| isStarted         | INT    | 是       | 0:app保存操作、1:app开始巡河操作 | 默认值为0 |
| frontImageAddress | STRING | 否       | 开始巡河拍照                     | 外链地址  |

### 请求示例:

```bash
{
    "taskId":18,
    "shipId": 35, 
    "startTime": 1647011934,
    "sLocation": "修改后的地址",
    "sLng": "123",
    "sLat": "456",
    "user": "Lishuang",
    "isStarted": 1
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 结束-巡河接口：

> 点击结束时调用此接口

### 接口地址：/wisdom/app/stop/patrol/river/

### 请求方式：POST

### 请求参数：

| 参数名            | 类型   | 是否必传 | 命名                   | 备注     |
| ----------------- | ------ | -------- | ---------------------- | -------- |
| taskId            | INT    | 是       | 巡河任务ID             |          |
| shipId            | INT    | 是       | 船的ID                 |          |
| endTime           | INT    | 是       | 结束巡河时间(秒时间戳) |          |
| eLocation         | STRING | 是       | 结束位置               |          |
| eLng              | STRING | 是       | 结束位置经度           |          |
| eLat              | STRING | 是       | 结束位置纬度           |          |
| weight            | STRING | 否       | 垃圾重量               |          |
| afterImageAddress | STRING | 否       | 结束巡河拍照           | 外链地址 |

### 请求示例:

```bash
{
    "taskId":6,
    "shipId": 33,
    "endTime": 1647022932,
    "eLocation": "通州",
    "eLng": "116.165032",
    "eLat": "39.903755",
    "weight": "66"
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 实时巡河接口：

> 当前接口返回船舶所有的信息, 前端工程师取自己所用到的字段即可，当前接口需要轮训请求(获取船的实时数据), 轮训时长与产品经理确认。

### 接口地址：/wisdom/app/patrol/river/realtime/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| taskId | INT  | 是       | 巡河任务ID |      |

### 请求示例:

```bash
{
    "taskId":18
}
```

### 响应

#### 200

```bash
{
    "data": {
        "alarmCount": 2, // 预警事件
        "shipNum": "0019" // 船的编码
        "shipName": "QDF-0019", // 船的名称
        "pitchAngle": -1.5773258209228516, // 俯仰角
        "velocityEast": -0.00035086582647636533,//东向速度
        "navigationTime": 6034350,// 导航时间 
        "height": 13.934898376464844,// 高度
        "speed": 0.0013401746344045616, // 速度
        "waterDistance": 0, // 水深距离  0表示没有传感器数据
        "wgs84Longitude": 121.0802308, // wgs84 经度
        "trackId": 19, // 轨迹编号
        "socPerKilo": 2.0, // 每公里消耗电量
        "remainMiles": "None", / 剩余里程 None表示无有效数据
        "latitude": 31.325337075135742, // 纬度
        "steerControlDrive": "1", // 驾驶模式
        "waterDistanceWarn": 0,  // 水深告警  0表示无告警
        "rollingAngle": -0.8274579048156738, // 滚转角
        "angleNorth": -1.8229105472564697, // 航向角
        "socMean": 52.0,// 平均电量
        "inTrack": 0,// 是否偏航  0表示没有偏航
        "velocityUniverse": 0.00027741200756281614,// 天向速度
        "noSv": 11,// 导航卫星个数  
        "wgs84Latitude": 31.320791, // wgs84 维度
        "velocityNorth": 0.0012449314817786217,  // 北向速度
        "longitude": 121.09125693075195,  // 经度
        "shipNum": "0004",  // 船号码
        "batteryNum": 2,  // // 电池数量
        "waterQuality": {  // 水质信息
            "oxy": 6.62, // 溶解氧 单位 mg/L
            "cTime": 1627889136,  // 数据采集时间
            "chlorophy": 0.0,  // 叶绿素含量 单位 ug/L
            "K": 0.0, // K+离子 单位 mg/L
            "dissOxySaturation": 91.4, // 溶解氧饱和度 单位%
            "NH4": 1.3, // 铵离子  单位 mg/L
            "cod": 1.4, // 化学需氧量  单位 mg/L
            "NH3": 0.0,  // 氨气  单位mg/L
            "ph": 7.03,  // PH值
            "turbidity": 19.5// 浊度 单位NTU
        }
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 预警事件详情接口：

### 接口地址：/wisdom/app/monitor_alarm/detail/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| taskId | INT  | 是       | 巡河任务ID |      |

### 请求示例:

```bash
{
    "taskId":18
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "ai_t__name": "树枝", // 事件三级类型名称
            "image_address": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/river/1646980401468.png", // 预警详情图片
            "ship_id": 32,  // 船ID
            "ai_t_id": 11, // 事件三级类型ID
            "ship__number": "0019",  // 船的编码
            "lat": "27.7899203", // 事件纬度
            "lng": "120.6850416",  // 事件经度
            "ship__name": "QDF-0019",  // 船的名称
            "id": 11563  // 事件ID
        },
        {
            "ai_t__name": "树枝",
            "image_address": null,
            "ship_id": 32,
            "ai_t_id": 11,
            "ship__number": "0019",
            "lat": "27.7899203",
            "lng": "120.6850416",
            "ship__name": "QDF-0019",
            "id": 11564
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取当前执行任务船舶的运行轨迹：

> 修改航线时, 需要先获取航线详情,调用当前接口

### 接口地址：/wisdom/app/get/ship_track/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| taskId | INT  | 是       | 巡河任务ID |      |

### 请求示例:

```bash
{
    "taskId":18
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "lat": "39.925117", // 纬度
            "patrol_task_id": 6,  // 任务ID
            "lng": "116.147856",  // 经度
            "id": 1,  // 轨迹ID
            "s_time": 1647007432 // 轨迹创建时间(秒时间戳)
        },
        {
            "lat": "39.899881",
            "patrol_task_id": 6,
            "lng": "116.168553",
            "id": 2,
            "s_time": 1647007432
        },
        {
            "lat": "39.87685",
            "patrol_task_id": 6,
            "lng": "116.212822",
            "id": 3,
            "s_time": 1647007432
        },
        {
            "lat": "39.846721",
            "patrol_task_id": 6,
            "lng": "116.230069",
            "id": 4,
            "s_time": 1647007432
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 修改当前执行任务船舶的运行轨迹：

> 1.修改的时候, 当天巡河任务一定有运行轨迹,如果没有去调用创建接口。
>
> 2.修改成功,可以在此调用详情列表页渲染修改成功后的轨迹, 或者客户端缓存修改时的入参。

### 接口地址：/wisdom/app/update/ship_track/

### 请求方式：POST

### 请求参数：

| 参数名    | 类型 | 是否必传 | 命名       | 备注 |
| --------- | ---- | -------- | ---------- | ---- |
| taskId    | INT  | 是       | 巡河任务ID |      |
| trackList | LIST | 是       | 修改的轨迹 |      |

### 请求示例:

```bash
{
    "taskId": 6,
    "trackList": [ 
        {
            "lng": "118.147856",
            "lat": "39.925117"
        },
        {
            "lng": "116.168553",
            "lat": "39.899881"
        },
        {
            "lng": "112.212822",
            "lat": "40.87685"
        },
        {
            "lng": "118.230069",
            "lat": "39.846721"
        }
    ]
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取船舶历史运行轨迹：

> 最新5次历史运行轨迹

### 接口地址：/wisdom/app/history/ship_track/

### 请求方式：POST

### 请求参数：

| 参数名   | 类型 | 是否必传 | 命名   | 备注 |
| -------- | ---- | -------- | ------ | ---- |
| shipId   | INT  | 是       | 船舶ID |      |
| watersId | INT  | 是       | 水域ID |      |

### 请求示例:

```bash
{
    "shipId": 33,
    "watersId": 22
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "task": {  // 任务详情
                "id": 6, // 任务ID
                "name": "西湖巡河A" // 任务名称
            },
            "c_time": 1657437544943.0,  // 创建时间
            "track": [  // 轨迹点位信息
                {
                    "c_time": 1657437544496.0,  // 创建时间(毫秒级别)
                    "wgs84_lng": "116.147856", // 经度
                    "wgs84_lat": "39.925117", // 纬度
                    "s_time": 1657437544 // 创建时间戳(秒级别)
                },
                {
                    "c_time": 1657437544496.0,
                    "wgs84_lng": "116.168553",
                    "wgs84_lat": "39.899881",
                    "s_time": 1657437544
                },
                {
                    "c_time": 1657437544496.0,
                    "wgs84_lng": "116.212822",
                    "wgs84_lat": "39.87685",
                    "s_time": 1657437544
                },
                {
                    "c_time": 1657437544496.0,
                    "wgs84_lng": "116.230069",
                    "wgs84_lat": "39.846721",
                    "s_time": 1657437544
                }
            ],
            "waters": { // 水域信息
                "id": 22, // 水域ID
                "name": "后塘河" // 水域名称
            },
            "c_ts": 1657437544, // 当前创建时间戳
            "s_time": 1657382400, // 当前凌晨时间戳
            "ship": { // 船舶信息
                "number": "0020",
                "id": 33,
                "name": "QDF-0020"
            },
            "_id": "62ca7d68a541dd50c434ba93", // 主键ID
            "_cls": "wisdom_waters_service.models.HistoryPatrolTaskTrack"
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```



## 巡河记录接口：

> 1.当前巡河记录,如果是待处理,那么只有巡河基础信息
>
> 2.如果是处理中, 那么有 基础信息 + 开始时间 + 事件信息
>
> 3.如果是已处理, 那么包含所有信息

### 接口地址：/wisdom/app/patrol_river/record/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名       | 备注 |
| ------ | ---- | -------- | ---------- | ---- |
| taskId | INT  | 是       | 巡河任务ID |      |

### 请求示例:

```bash
{
    "taskId": 6
}
```

### 响应

#### 200

```bash
{
    "data": {
        "startData": {  // 开始巡河
            "sLocation": "云水光中",  // 起点位置
            "sLongitude": "120.640957927",  // 起点经度
            "shipNumber": "0019",  //船的编码
            "startTime": 1647011934,  // 巡河开始时间
            "shipName": "QDF-0019",  // 船的名称
            "user": "仰望星空",  // 任务人员
            "sLatitude": "31.3169841432",  // 起点纬度
            "isStarted": 0:未开船、1:已开船 ,
            "shipStreamAddress": "https://open.ys7.com/v3/openlive/F10240821_1_1.m3u8?expire=1665537079&id=369774369014853632&t=7f75a52a8c9bbb33ced65da0d52df783c55177b30a2c1f7787fb40f86709f92c&ev=100"  // 船舶的视频流地址
        },
        "endData": { // 结束巡河
            "shipNumber": "0019",  // 船编码
            "weight": "66",  // 垃圾重量
            "eLocation": "通州",  // 结束位置
            "eLatitude": "39.903755",  // 结束纬度
            "duration": 3,  // 运行时长
            "sLocation": "云水光中", // 开始位置
            "eventCount": 2,  // 巡河事件
            "shipName": "QDF-0019",  // 船的编码
            "endTime": 1647022932,  // 结束时间
            "eLongitude": "116.165032",  // 结束经度
            "realDistance": "7.899"  // 实际运行距离
            "isStarted": 0:未开船、1:已开船 ,
        },
        "taskData": {  // 巡河基础信息
            "status": 3,  // 巡河状态: 1:待处理 、2:处理中、3:已处理
            "distance": "2.2",  // 设置距离 
            "sLocation": "云水光中",  // 开始位置
            "user": "仰望星空",  // 任务人员
            "sTime": 1647005538,  // 任务创建时间
            "patrolType": 1,  // 巡河方式: 1:无人船、2:无人机、3:人工
            "cUser": "吕品品",  // 发布人  
            "name": "西湖巡河A",  // 任务名称
            "eLocation": "通州",  // 结束位置
            "areaData": "杭州市西湖区",  // 任务名称
            "content": "日常巡河、游人和堤防安全、水质监测。",  // 任务内容
            "cCompany": "西湖管委会"  // 发布单位
            "isStarted": 0:未开船、1:已开船 ,

        },
        "eventList": [  // 预警事件
            {
                "image_address": null,  // 预警图片
                "ai_s__name": "水草海藻", // 预警类型
                "ai_s_id": 2, //预警ID
                "ship_id": 32, //船的ID
                "ship__number": "0019",  // 船的编码
                "lat": "27.7899203",  // 预警纬度
                "lng": "120.6850416", // 预警经度
                "ship__name": "QDF-0019",  // 船的名称
                "id": 11564 // 预警的ID,
                "is_reported":0  // 0:未报、1:已报
            },
            {
                "image_address": "http://qingdaofu-bucket.oss-cn-hangzhou.aliyuncs.com/river/1646980401468.png",
                "ai_s__name": "水草海藻",
                "ai_s_id": 2,
                "ship_id": 32,
                "ship__number": "0019",
                "lat": "27.7899203",
                "lng": "120.6850416",
                "ship__name": "QDF-0019",
                "id": 11563
            }
        ]
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 上传预警照片接口：

### 接口地址：/wisdom/app/upload/alarm_image/

### 请求方式：POST

### 请求参数：

| 参数名       | 类型   | 是否必传 | 命名           | 备注 |
| ------------ | ------ | -------- | -------------- | ---- |
| alarmId      | INT    | 是       | 预警ID         |      |
| imageAddress | STRING | 是       | 图片的外链地址 |      |

### 请求示例:

```bash
{
    "alarmId": 102,
    "imageAddress": "123"
}
```

### 响应

#### 200

```bash
{
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 事件(撤回操作)：

### 接口地址：/wisdom/app/event/unreported/

### 请求方式：POST

### 请求参数：

| 参数名  | 类型 | 是否必传 | 命名   | 备注 |
| ------- | ---- | -------- | ------ | ---- |
| eventId | INT  | 是       | 事件ID |      |

### 请求示例:

```bash
{
    "eventId": 11564
}
```

### 响应

#### 200

```bash
{
    "data": {
        "id": 11564,
        "isReported": 0 // 已撤回
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 事件(上报)：

### 接口地址：/wisdom/app/event/reported/

### 请求方式：POST

### 请求参数：

| 参数名  | 类型 | 是否必传 | 命名   | 备注 |
| ------- | ---- | -------- | ------ | ---- |
| eventId | INT  | 是       | 事件ID |      |

### 请求示例:

```bash
{
    "eventId": 11564
}
```

### 响应

#### 200

```bash
{
    "data": {
        "id": 11564,
        "isReported": 1  // 已上报
    },
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取当前任务人所负责的水域(智慧巡河-水域名称筛选)：

### 接口地址：/wisdom/app/get/waters_name/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名     | 备注 |
| ------ | ---- | -------- | -------- | ---- |
| userId | INT  | 是       | 任务人ID |      |

### 请求示例:

```bash
{
    "userId": 5
}
```

### 响应

#### 200

```bash
{
    "data": [
         {
            "id": 14,
            "name": "莫愁湖"
        },
        {
            "id": 15,
            "name": "中塘河"
        },
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取当前运维人员负责的船舶信息(筛选)

### 接口地址：/wisdom/app/get/ship_data/

### 请求方式：POST

### 请求参数：

| 参数名 | 类型 | 是否必传 | 命名     | 备注 |
| ------ | ---- | -------- | -------- | ---- |
| userId | INT  | 是       | 任务人ID |      |

### 请求示例:

```bash
{
    "userId": 5
}
```

### 响应

#### 200

```bash
{
    "data": [
        {
            "id": 15,
            "name": "QDF-0001",
            "number": "0001"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取当前系统任务信息

### 接口地址：/v1/wisdom/app/get/task_user/

### 请求方式：POST

### 请求参数：

* 

### 请求示例:

* 

### 响应

#### 200

```bash
{
    "data": [
        {
            "company": "BAT", // 任务人单位
            "roles__name": "管理员",  // 角色
            "id": 1, // 用户ID
            "roles": 7,  // 角色ID
            "name": "吕品品" // 用户名
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

## 获取所有背景音乐列表页

### 接口地址：/wisdom/app/voice_play/list/

### 请求方式：GET

### 请求参数：

| 参数名  | 类型   | 是否必传 | 命名     | 备注 |
| ------- | ------ | -------- | -------- | ---- |
| detect  | INT    | 否       | 播报类型 | 筛选 |
| event   | INT    | 否       | 事件类型 | 筛选 |
| content | STRING | 否       | 内容     | 筛选 |

### 请求示例:

* 

### 响应

#### 200

```bash
{
    "data": [
        {
            "id": 28,
            "cTime": "1637653772.973381",
            "detect": 5,
            "event": "Can you speak English?",
            "content": "I am a language genius, I am proficient in Chinese and English.",
            "name": "吕品品"
        },
        {
            "id": 27,
            "cTime": "1637653758.882378",
            "detect": 5,
            "event": "how old are you?",
            "content": "I am six years old.",
            "name": "吕品品"
        }
    ],
    "retCode": 0,
    "retMsg": "成功 | Success"
}
```

