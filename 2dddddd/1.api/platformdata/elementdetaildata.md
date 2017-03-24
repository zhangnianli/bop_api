# 业务编号

platform.data.element.detaildata

# api请求地址

[http://api.bonree.com/platform/data/element/detaildata](http://api.bonree.com/platform/element/detaildata)

# 请求参数：

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| username | string | bonreetest | \*用户名 |
| token | string | xxxxxxxxxxxxx | \*令牌 |
| params | string | {"dtype":"json","appId":"1035","dtime":"20170201000000-20170301000000"} | \*参数json |

**params说明：**

| 参数名称 | 参数类型 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- |
| dtype | string | json | \*数据类型\(csv、json\) |
| appId | string | 1035,1023,2023 | \*应用ID |
| partUrlCode | string | 13575031,15465778 | 截取后的URL CODE |
| dtime | string | 20170201000000-20170301000000 | \*查询时间范围 |
| pageNum | string | 1 | \*页码 |
| pageRecorders | string | 50 | \*每页行数 |
| orderByFlag | string | DTIME DESC | \*排序字段 |
| filters | string | {<br/>"netserviceAndNetStandard":\[{"netserviseId":"1","netStandard":"1"},{"netserviseId":"1","netStandard":"2"}\],<br/>"cityCode":\[1100000,1200000\],<br/>"browsr":\[0,1,2,3,4\],<br/>"onlyError":"1"<br/>} | 过滤条件：<br/>netserviceAndNetStandard:运营商&网络接入方式；<br/>cityCode:地域；<br/>browsr:浏览器；<br/>onlyError:0-只查正确数据;1-只查错误数据; |
| dHeader | string | APPID,URLCODE,DTIME,DNSTIME,<br/>TCPTIME,SSLTIME | \*指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| MONITORTIME | 监测时间 |
| APPID | 应用ID |
| TASKTYPE | task类型 |
| CITYCODE | 城市ID |
| NETSERVICEID | 运营商ID |
| ACCESSMODE | 接入方式 |
| OSID | 系统类型 |
| OSVERID | 系统版本 |
| BROWSERID | 浏览器类型 |
| BROWSERVERID | 浏览器版本 |
| PARTURLCODE | 截取后的URLCODE |
| URLCODE | 完整的URLCODE |
| FLAG | 元素类型：1-慢元素，2-错误元素 |
| DTIME | 响应时间 |
| DNSTIME | DNS时间 |
| TCPTIME | TCP时间 |
| SSLTIME | SSL时间 |
| SERVERRESPONSETIME | 服务器响应时间 |
| SERVERDEALTIME | 服务器处理时间 |
| DOWNTIME | 下载时间 |
| DOWNSIZE | 下载大小 |
| DOWNSPEED | 下载速度 |
| ERRORID | 错误码 |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| error\_code | int | 错误码 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
    HttpClient httpclient = new DefaultHttpClient();
    String url = "http://api.bonree.com/apm/backendcall/statdata";
    HttpPost httppost = new HttpPost(url);
    System.out.println("请求: " + httppost.getRequestLine());
    // 创建参数队列
    List<NameValuePair> formparams = new ArrayList<NameValuePair>();
    formparams.add(new BasicNameValuePair("username", "bonreetest"));
    formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
    formparams.add(new BasicNameValuePair("params", "{\"token\":\"*******\",\"dtype\":\"json\",\"appId\":\"1035\",\"dtime\":\"20170201000000-20170301000000\",\"pageNum\":\"1\",\"pageRecorders\":\"50\",\"orderByFlag\":\"DTIME DESC\",\"dHeader\":\"APPID,URLCODE,DTIME,DNSTIME,TCPTIME\"}"));
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

# 返回结果示例：

```
{
    "error_code": 0,
    "reason": "查询成功",
    "result": [
        ["APPID","URLCODE","DTIME","DNSTIME","TCPTIME"],
        ["1035", "111111", "10","929","7"],
        ["1023", "122222", "20","930","7"]
    ]
}
```



