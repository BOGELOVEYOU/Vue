# 新闻项目文档

此文档为v0.0.1版本

## 通用说明

接口根地址为：https://www.young1024.com:3002  或  http://www.young1024.com:82

请求方式：POST

返回参数说明

| 名称   | 类型        | 说明                        |
| ------ | ----------- | --------------------------- |
| status | String      | success为成功，fail为是失败 |
| msg    | String      | 提示信息                    |
| data   | Json/String | 对应返回的数据              |

**说明:**  context 和 content 字段都是详情

**说明**: pubtime 和 time  字段都是时间

如接口无其他特别说明，则以上是接口的通用说明



## 1.注册

地址： /sign

说明：此接口仅支持 multipart/form-data 表单类型的数据

参数：

| 名称     | 类型   | 必填 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| username | String | 是   | -      | -        |
| password | String | 是   | -      |          |
| avatar   | file   | 是   | -      | 头像文件 |

返回值

```
{
	"status":"success",
	"msg":"æ³¨åæå",
	"data"{
		"_id":"614b3ebc9af8501e1a51b973",
    "username":"young",
    "password":"e10adc3949ba59abbe56e057f20f883e",
    "avatar":"1632321212160.jpg",
    "__v":0
  }
}
```



## 2.登录

地址：/login

参数：

| 名称     | 类型   | 必填 |
| -------- | ------ | ---- |
| username | String | 是   |
| password | String | 是   |

返回值：

```
{
    "status": "success",
    "msg": "登录成功",
    "data": {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2MTRiM2ViYzlhZjg1MDFlMWE1MWI5NzMiLCJ1c2VybmFtZSI6InlvdW5nIiwiYXZhdGFyIjoiMTYzMjMyMTIxMjE2MC5qcGciLCJpYXQiOjE2MzIzMjE4MzYsImV4cCI6MTYzMjkyNjYzNn0.YLWY-cPMRWxMEwrSlOeOEdkqjLZWEW39Yljpc23lkws",
        "userinfo": {
            "_id": "614b3ebc9af8501e1a51b973",
            "username": "young",
            "avatar": "1632321212160.jpg"
        }
    }
}
```



## 3.获取新闻

地址: /news

参数：

| 名称 | 类型   | 必填 | 默认值 | 说明                                            |
| ---- | ------ | ---- | ------ | ----------------------------------------------- |
| type | String | 是   | -      | '军事','财经','NBA','汽车','文化','股票','时政' |
| size | Number | 否   | 20     |                                                 |
| page | Number | 否   | 1      |                                                 |

返回值：

```
{
    "status": "success",
    "msg": "查询成功",
    "data": [
        {
            "_id": "5e5a8f9fbf5faa84e2f00cc6",
            "title": "中信建投：短期已超卖 三条主线加仓",
            "pubtime": "1582984745000",
            "media": "中信建投",
            "source": "https://new.qq.com/omn/FIN20200/FIN2020022903618200.html",
            "type": "财经"
        },
       	....
    ]
}
```

**说明**: pubtime 和 time  字段都是时间



## 4.搜索新闻

地址：/search

参数：

| 名称    | 类型   | 必填 |
| ------- | ------ | ---- |
| keyword | String | 是   |
| size    | Number | 否   |
| page    | Number | 否   |

返回值：

```
{
    "status": "success",
    "msg": "查询成功",
    "data": [
        {
            "_id": "5e5a8f9fbf5faa84e2f00cc6",
            "title": "中信建投：短期已超卖 三条主线加仓",
            "pubtime": "1582984745000",
            "media": "中信建投",
            "source": "https://new.qq.com/omn/FIN20200/FIN2020022903618200.html",
            "type": "财经"
        },
        {
            "_id": "5f9938d1232a2c205391b0cd",
            "title": "中信证券前高管给“竞争对手”讲课被开除！125万年终奖打水漂",
            "time": "1603875420000",
            "type": "股票",
            "source": "券业观察",
            "img": "https://x0.ifengimg.com/ucms/2020_44/FFA2EFF26C1E41C13A8CC2BFD1589C37B1EB62BC_w1080_h459.jpg"
        }
    ]
}
```



## 5.新闻详情

地址:  /newsinfo

参数：

| 名称   | 类型 | 必填 |
| ------ | ---- | ---- |
| newsid | id   | 是   |

返回值：

```
{
    "status": "success",
    "msg": "查询成功",
    "data": {
        "_id": "5f9938d1232a2c205391b0c4",
        "title": "25万股民的狂欢！溢价45%换股吸并，300亿央企一字涨停",
        "context": "<div><div class=\"text-3w2e3DBc\"><p>原标题：25万股民的狂欢！溢价45%换股吸并，300亿央企一字涨停，这一板块机会来了？</p></div>",
        "time": "1603874508000",
        "type": "股票",
        "source": "券商中国",
        "img": "https://x0.ifengimg.com/res/2020/F86AAEA6BD76006EA5A17C4910F0145520B85234_size36_w600_h333.jpeg",
        "__v": 0
    }
}
```

**说明:**  context 和 content 字段都是详情



## 6.收藏

地址： /collect

参数：

| 名称 | 类型 | 必填 |
| ---- | ---- | ---- |
| uid  | id   | 是   |
| aid  | id   | 是   |

返回值:

```
{
    "status": "success",
    "msg": "收藏成功",
    "data": {
        "_id": "614b4ddf70d32b0a0b62425a",
        "uid": "614b3ebc9af8501e1a51b973",
        "aid": "5f9938d1232a2c205391b0c4",
        "__v": 0
    }
}
```



## 7.取消收藏

地址：/cancelCollect

参数：

| 名称 | 类型 | 必填 |
| ---- | ---- | ---- |
| uid  | id   | 是   |
| aid  | id   | 是   |

返回值：

```
{
    "status": "success",
    "msg": "取消收藏成功",
    "data": "del:1"
}
```



## 8.查看收藏列表

地址：/clist

参数：

| 名称 | 类型 | 必填 |
| ---- | ---- | ---- |
| uid  | id   | 是   |

返回值:

```
{
    "status": "success",
    "msg": "查询成功",
    "data": [
        {
            "_id": "614b4f346862f1126a5c9391",
            "uid": "614b3ebc9af8501e1a51b973",
            "aid": {
                "_id": "5f9938d1232a2c205391b0c4",
                "title": "25万股民的狂欢！溢价45%换股吸并，300亿央企一字涨停",
                "time": "1603874508000",
                "type": "股票",
                "source": "券商中国",
                "img": "https://x0.ifengimg.com/res/2020/F86AAEA6BD76006EA5A17C4910F0145520B85234_size36_w600_h333.jpeg"
            },
            "__v": 0
        }
    ]
}
```



## 9.检查是否收藏

地址：/checkcollect

参数：

| 名称   | 类型 | 必填 |
| ------ | ---- | ---- |
| newsid | id   | 是   |
| uid    | id   | 是   |

返回值：

```
{
    "status": "success",
    "msg": "已经收藏",
    "data": true
}
```



## 10.检查登录状态

地址： /status

参数：

| 名称  | 类型   | 必填 |
| ----- | ------ | ---- |
| token | String | 是   |

返回值

```
{
    "status": "success",
    "msg": "查询成功",
    "data": {
        "_id": "614b3ebc9af8501e1a51b973",
        "username": "young",
        "avatar": "1632321212160.jpg",
        "iat": 1632321546,
        "exp": 1632926346
    }
}
```

