# 业务编号

platform.data.element.statdata

# api请求地址

[http://api.bonree.com/platform/data/element/statdata](http://api.bonree.com/platform/element/statdata)

# 请求参数：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string | 是 | xxxxxxxxxxxxx | 令牌 |
| params | string | 是 | {"dtype":"json","appId":"1035","dtime":"20170201000000-20170301000000"} | 参数json |

**params说明：**

| 参数名称 | 参数类型 | 是否必选 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json | 数据类型\(csv、json\) |
| appId | string | 是 | 1035 | 应用ID |
| dTime | string | 是 | 20170201000000-20170301000000 | 查询时间范围 |
| pageNum | string | 否 | 1 | 页码 |
| pageRecorders | string | 否 | 50 | 每页行数 |
| order | string | 否 | DTIME$AVG DESC | 排序字段 |
| group | strng | 是 | PARTURLCODE | 分组字段（APPID,TASKID,TASKTYPE,CITYCODE,NETSERVICEID,ACCESSMODE,OSID,OSVERID,BROWSERID,BROWSERVERID,ERRORID,PARTURLCODE） |
| filters | string | 否 | {"netserviceAndNetStandard":\[{"netserviseId":"1","netStandard":"1"},{"netserviseId":"1","netStandard":"2"}\],"cityCode":\[1100000,1200000\],"browsr":\[0,1,2,3,4\],"onlyError":"1"} | 过滤条件：netserviceAndNetStandard:运营商&网络接入方式；cityCode:地域；browsr:浏览器；onlyError:0-只查正确数据,1-只查错误数据,2-只查慢元素；errorId:错误码筛选; |
| dHeader | string | 是 | APPID,PARTURLCODE,DTIME$MAX,DTIME$MIN,DTIME$AVG,DTIME$SUM,DNSTIME$AVG,TCPTIME$AVG | \*指标数据项 |

# dHeader字段说明：

| 字段 | 名称 |
| :--- | :--- |
| MONITORTIME | 监测时间 |
| APPID | 应用ID |
| TASKID | 任务ID |
| TASKTYPE | 任务类型 |
| CITYCODE | 城市ID |
| NETSERVICEID | 运营商ID |
| ACCESSMODE | 接入方式 |
| OSID | 系统类型 |
| OSVERID | 系统版本 |
| BROWSERID | 浏览器类型 |
| BROWSERVERID | 浏览器版本 |
| TERMINAL\_TYPE | 客户端类型\(1:pc browser; 2:mobile brower;3:mobile app\) |
| ERRORID | 错误码 |
| PARTURLCODE | 截取后的URL CODE |
| DTIME$MAX | 最大响应时间 |
| DTIME$MIN | 最小响应时间 |
| DTIME$AVG | 平均响应时间 |
| DTIME$SUM | 总响应时间 |
| DNSTIME$AVG | 平均DNS时间 |
| TCPTIME$AVG | 平均TCP时间 |
| SSLTIME$AVG | 平均SSL时间 |
| SERVERRESPONSETIME$AVG | 平均服务器响应时间 |
| SERVERDEALTIME$AVG | 平均服务器处理时间 |
| DOWNSIZE$AVG | 平均下载大小 |
| DOWNTIME$AVG | 平均下载时间 |
| DOWNSPEED$AVG | 平均下载速度 |
| REQUESTNUM$SUM | 总请求次数 |
| SLOWREQUESTNUM$SUM | 总慢请求次数 |
| ERRORREQUESTNUM$SUM | 总错误请求数 |
| SLOWRATE | 慢速比 |
| ERRORRATE | 请求错误率 |
| MONITORTIME$MIN | 首次发生时间 |
| MONITORTIME$MAX | 末次发生时间 |
| VISITNUM$SUM | 受影响访问次数 |
| KEYVISITNUM$SUM | 受影响访问次数（按关键元素统计） |

# 返回参数说明：

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码 |
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
    formparams.add(new BasicNameValuePair("params", "{\"dType\":\"json\",\"appId\":\"1035\",\"dTime\":\"20170201000000-20170301000000\",\"pageNum\":\"1\",\"pageRecorders\":\"50\",\"order\":\"DTIME$AVG DESC\",\"dHeader\":\"appId,domain,eleDnsAvg,eleDnsMax,eleDnsMin\"}"));
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
    "errorCode": 0,
    "reason": "查询成功",
    "result": [
        ["appId","domain","eleDnsAvg","eleDnsMax","eleDnsMin"],
        ["1035", "www.baidu.com", "1021", "10","929","7"],
        ["1035", "www.bonree.com", "2021", "20","930","7"]
    ]
}
```



