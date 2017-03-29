# 

# 业务编号

net.data.network.statdata

# api请求地址

[https://api.bonree.com/net/data/network/](https://[api.bonree.com/net/report/taskdata]\(http://api.bonree.com/net/report/taskdata)statdata

# 请求方式

POST／GET

# 请求参数

# 请求参数

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string\(32\) | 是 | XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 令牌 |
| params | string | 是 | {“type”:2,"taskId":123456} | 请求参数 |

params说明：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| type | string | 是 | json/csv | 数据类型 |
| taskId | string | 否 | 170435,170436 | 任务ID |
| dtime | string | 是 | 20161101000000-20161102000000 | 数据时间范围，（时间最长一个月） |
| monitors | string | 是 | ALL/IDC/LM/PP/IDC\|PP | 监测点类型 |
| dateFM | string | 否 | 默认是yyyy-MM-dd HH:mm:ss | 数据时间类型 |
| filters | string | 否 | \[{“filed”:”CPU\_RATE”, “condo”:”&gt;=”,”value”:”6”}\] | 字段值筛选条件 |
| group | string | 否 | city,netservice | 分组条件，字段顺序为分组顺序 |
| dHeader | string | 是 | city,netservice | 指定计算哪些指标，并作为查询结果返回 |

field列表：

| 字段英文名称 | 字段中文名称 |
| :--- | :--- |
| PING\_SET | 时延 |
| PING\_LOST\_RATE | 丢包率 |
| TASKID | roleid |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码，0表示正常查询 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/net/network/statdata";
        HttpPost httppost = new HttpPost(url);
        System.out.println("请求: " + httppost.getRequestLine());
        // 创建参数队列
        List<NameValuePair> formparams = new ArrayList<NameValuePair>();
        formparams.add(new BasicNameValuePair("username", "bonreetest"));
        formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
        formparams.add(new BasicNameValuePair("params", "{\"token\":\"*******\",\"dtype\":\"json\",\"taskId\":\"1035\",\"dtime\":\"20170201000000-20170301000000\"}"));
        UrlEncodedFormEntity uefEntity = new UrlEncodedFormEntity(formparams, "UTF-8");
        httppost.setEntity(uefEntity);
        // 执行
        HttpResponse response = httpclient.execute(httppost);
        HttpEntity entity = response.getEntity();
        System.out.println("----------------------------------------");
        System.out.println("状态:" + response.getStatusLine());
        if (entity != null) {
            System.out.println("Response content length: " + entity.getContentLength());
            System.out.println("Response content :" + EntityUtils.toString(entity, "UTF-8"));
        }
        // 关闭连接,释放资源
        httpclient.getConnectionManager().shutdown();
```

# 返回结果示例

```
{
    "error_code": 0,
    "reason": "查询成功",
    "result": [
        [
            "role_id",
            "domain"
        ],
        [
            "1035",
            "www.baidu.com"
        ],
        [
            "1023",
            "www.bonree.com"
        ]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



