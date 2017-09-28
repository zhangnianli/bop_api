# **业务编号**

net.data.report.transfer.statdata

# api请求地址

[https://api.bonree.com/net/data/transfer/statdata](https://api.bonree.com/net/data/transfer/statdata)

# 请求方式

POST／GET

# 请求参数

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| username | string | 是 | bonreetest | 用户名 |
| token | string（32） | 是 | xxx | 令牌 |
| params | string | 是 | {“dType”:2,"taskId":123456} | 请求参数 |

## params说明：

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | 是 | json/csv | 数据类型 |
| taskId | string | 是 | 170435,170436 | 任务ID |
| dTime | string | 是 | 20161101000000-20161102000000 | 数据时间范围，（时间最长一个月） |
| dHeader | string | 是 | ROLE\_ID,CITY\_CODE,D\_TIME | 指定返回的指标,多个逗号分隔,具体字段查看dHeader字典表 |
| user | string | 是 | bonreetest | V4用户名 |
| group | string | 是 | ROLE\_ID,CITY\_CODE | 分组条件，字段顺序为分组顺序,详见分组列表 |
| weekTime | string | 否 | {"startWeek":"1", "endWeek":"3","startHour":"00:00","endHour":"12:00"} | 选中dTime时间内的交集,示例值表示查询周一到周三,0点到12点范围内的数据 |
| dateFM | string | 否 | 默认是yyyy-MM-dd HH:mm:ss | 数据时间类型 |
| filters | string | 否 | {"browser":\["1","2"\],"os":\["2","3","4"\],"clientIds":{"selected":"in", "ids":\["123", "456"\]}} | 字段值筛选条件,详见筛选条件列表 |
| mainIndex | string | 否 | {"name":"D\_TIME", "warnNormal":"10","warnGeneral":"20"} | 主指标,结果返回最小值,最大值,中位数和平均值;warnNormal正常警显值;warnGeneral普通警显值,根据配置的值计算慢速比 |
| calType | string | 否 | avg/max/min/mid | 指标计算方式,只有主指标会计算中位数,默认为平均值 |
| granule | string | 否 | STR\_HOUR | 查询数据的时间频度，单位为分钟，当传时间频度的时候，group参数必填 |
| order | string | 否 | ROLE\_ID ASC,CITY\_CODE DESC | 排序条件 |
| dgmParam | string | 否 | {"group":{"123":\["1100101\_1\_1"\],"124":\["1100101\_2\_1"\]}, "groupDmg":"true"} | 分组统计条件,groupDmg:是否分组;group为具体的分组条件,key为groupId,value为监测点组,监测点形式为CITYCODE\_NETSERVICEID\_CLIENTTYPE;返回的数据中每行都包含DMG\_ID用于标识属于哪个监测组 |

### filters字段

| 参数名称 | 参数类型 | 是否必填 | 示例值 | 参数说明 |
| :--- | :--- | :--- | :--- | :--- |
| monitors | string | 否 | {"idc": {"selected": "in","agents": \["1100101\_1","1100101\_2" \]},"lm": {"selected": "all","agents": \[\]},"mb": {"selected": "notin","agents": \["1100503\_16"\]},"bmtp": {"selected": "all","agents": \[\]},"pp": {"selected": "all","agents": \[\]}} | 监测点类型,默认全选.selected表示选中类型,all:为全部选中;in:选中agents里面的值,notin:排除agents里面的值;agents为数组,里面的值为字符串,citycode\_netserverid |
| access | string | 否 | \["1","2"\] | 接入方式,仅支持wap与bmtp |
| agentSpeed | string | 否 | \["1","2","3"\] | 监测点带宽,1:\[0, 512Kb\];2:\(512Kb, 2Mb\];3:\(2Mb, 4Mb\];4:\(4Mb, 10Mb\];5:\(10Mb, 20Mb\];6:\(20Mb, ∞\) |
| browser | string | 否 | \["1","2","3"\] | 监测点浏览器版本,1: IE6; 2: IE7; 3: IE8; 4:IE9; 5:IE10; 6:IE11; 100:chrome\(WebKit\); 101:chrome\(blink\); -1:其它 |
| os | string | 否 | \["2","3","4","5"\] | 监测点操作系统版本: 2:WIN2003; 3:WINXP; 4:WINVISTA; 5:WIN7; 6:WIN8; 9:WIN10; -1:其它 |
| clientIds | string | 否 | {"selected":"in", "ids":\["123", "456"\]} | 客户端ID,selected表示选中类型,in:选中ids里面的值,notin:排除ids里面的值 |
| clientIPs | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 客户端IP,selected表示选中类型,in:选中ips里面的值,notin:排除ips里面的值 |
| clientDNS | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 客户端DNS,selected表示选中类型,in:选中ips里面的值,notin:排除ips里面的值 |
| roleIPs | string | 否 | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | 目标IP,selected表示选中类型,in:选中ips里面的值,notin:排除ips里面的值 |
| CPURate | string | 否 | {"min":"48", max:"60"} | 客户端CUP占用率 |
| memoryRate | string | 否 | {"min":"48", max:"60"} | 客户端内存占用率 |
| processNum | string | 否 | {"min":"48", max:"60"} | 客户端进程数量 |
| cycleSpeed | string | 否 | {"min":"1000", max:"2000"} | 周期平均速度,单位:KB/s |
| cycleSpeedWeigh | int | 否 | 2 | 整体速度大于几倍的平均周期速度 |
| tracertMatching | int | 否 | 0 | 是否匹配出口ip 0:否;1:是 |
| groupFilter | int | 否 | 0 | 是否排除样本数不一致数据,0:否;1:是 |
| errorIds | string | 否 | \["302","404"\] | 错误ID,默认包含0 |
| performanceIndex | string | 否 | {"type":"0","name":"D\_TIME","min":"0.5","max":"1.0","mark":"0", "group":"0"} | 指标筛选,type:筛选样式,0:指定值,1:指标百分比,2:样本数; index:指标; min:最小值; max:最大值; mark:标识,0:与\(保留\),1:或\(排除\);group分组, type为1或2时生效,0表示没有分组,1表示城市运营商,2表示地区运营商 |
| hijack | int | 否 | 0 | 是否排除劫持数据;0:不排除;1排除 |
| clickParam | string | 否 | {"onlyError":"0","granule":{"key":"STR\_HOUR","value":"201708302300"},"index":{"ROLE\_IP":"1.1.1.1","OS\_VERSION":"2"},"indexFilter":{"name":"D\_TIME","min":"0.097","max":"0.099"}} | 点击条件,onlyError:1只有错误;0都有;2只有正确;granule粒度,key表示点击时的粒度,value表示粒度的值;index指标,里面包含指标筛选条件,indexFilter性能值筛选,name指标名称,min最小值,max最大值,左闭右开 |

#### 时间频度字典表

| 值 | 含义 |
| :--- | :--- |
| STR\_MINUTE5 | 5分钟频度 |
| STR\_MINUTE10 | 10分钟频度 |
| STR\_MINUTE15 | 15分钟频度 |
| STR\_MINUTE30 | 30分钟频度 |
| STR\_HOUR | 1小时频度 |
| STR\_HOUR2 | 2小时频度 |
| STR\_HOUR4 | 4小时频度 |
| STR\_HOUR8 | 8小时频度 |
| STR\_HOUR12 | 12小时频度 |
| STR\_DAY | 1天频度 |
| STR\_WEEK | 1周频度 |
| STR\_MONTH | 1个月频度 |
| STR\_YEAR | 1年频度 |

# dHeader字典表：

### 统计字段:

| 字段英文名称 | 字段中文名称 | 备注 |
| :--- | :--- | :--- |
| ROLE\_ID | 任务ID |  |
| D\_TIME | 整体性能\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| DOWN\_SPEED | 平均传输速度\(KB/s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| DOWN\_TIME | 传输用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| DNS\_TIME | DNS用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| TCP\_TIME | TCP用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| SEND\_TIME | 发送用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| R\_TIME | 响应用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| SSL\_TIME | SSL握手用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| ONEBYTE\_TIME | 首包用时\(s\) | $MIN最小值;$MAX最大值;$MID中位数 |
| BYTES\_RECEIVED | 传输大小\(KB\) | $MIN最小值;$MAX最大值;$MID中位数 |
| USEABLE | 成功率\(%\) | 有效次数/\(有效次数+错误次数\) |
| ERRNUM | 错误次数 |  |
| MNUM | 有效监测次数 |  |
| SLOW\_RATE | 慢速比\(%\) |  |
| HIJACK | 总劫持次数 |  |
| HIJACKPER | 劫持比例\(%\) |  |
| HIJACKDNS | 域名劫持次数 |  |
| CITY\_CODE | 城市码 |  |
| DISTRICTCODE | 地区码 |  |
| NETSERVICE\_ID | 运营商码 |  |
| ROLE\_CITYCODE | 目标城市码 |  |
| ROLE\_DISTRICTCODE | 目标地区码 |  |
| ROLE\_NETSERVICE | 目标运营商码 |  |
| ARRIVAL\_SCALE | 到达率 |  |
| COVERAGE\_SCALE | 覆盖率 |  |
| ROLE\_IP | 目标IP |  |

### 分组字段

| 字段英文名称 | 字段中文名称 | 备注 |
| :--- | :--- | :--- |
| ROLE\_ID | 任务ID |  |
| CITY\_CODE | 城市码 |  |
| DISTRICTCODE | 地区码 |  |
| NETSERVICE\_ID | 运营商码 |  |
| ROLE\_CITYCODE | 目标城市码 |  |
| ROLE\_DISTRICTCODE | 目标地区码 |  |
| ROLE\_NETSERVICE | 目标运营商码 |  |
| ROLE\_IP | 目标IP |  |

# 返回参数说明

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| errorCode | int | 错误码,0表示查询正常 |
| reason | string | 返回说明 |
| result | string | 返回结果集 |

# 请求示例

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/net/data/transfer/statdata";
        HttpPost httppost = new HttpPost(url);
        System.out.println("请求: " + httppost.getRequestLine());
        // 创建参数队列
        List<NameValuePair> formparams = new ArrayList<NameValuePair>();
        formparams.add(new BasicNameValuePair("username", "bonreetest"));
        formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
        formparams.add(new BasicNameValuePair("params", "{\"dType\":\"json\",\"taskId\":\"1035\",\"user\":\"bonreetest\",\"dTime\":\"20170201000000-20170301000000\",\"dHeader\":\"ROLE_ID,CITY_CODE,D_TIME\",\"group\":\"ROLE_ID,CITY_CODE\"}"));
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
            "ROLE_ID",
            "CITY_CODE",
            "D_TIME"
        ],
        [
            "1035",
            "1100101",
            "0.34"
        ]
    ]
}
```

# api工具：

api测试工具， api响应码查询工具，监测点查询工具，指标查询工具，监测数据错误码查询工具

# FAQ：



