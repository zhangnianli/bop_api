# **ҵ����**

net.data.report.transfer

# api�����ַ

[https://api.bonree.com/net/data/transfer](https://api.bonree.com/net/element/]%28https://[api.bonree.com/net/report/taskdata]%28http://api.bonree.com/net/report/taskdata%29statdata]%28https://api.bonree.com/net/element/]%28https://[api.bonree.com/net/report/taskdata]%28http://api.bonree.com/net/report/taskdata%29statdata)/statdata

# ����ʽ

POST��GET

# �������

| �������� | �������� | �Ƿ���� | ʾ��ֵ | ����˵�� |
| :--- | :--- | :--- | :--- | :--- |
| username | string | �� | bonreetest | �û��� |
| token | string��32�� | �� | xxx | ���� |
| params | string | �� | {��dType��:2,"taskId":123456} | ������� |

## params˵����

| �������� | �������� | �Ƿ���� | ʾ��ֵ | ����˵�� |
| :--- | :--- | :--- | :--- | :--- |
| dType | string | �� | json/csv | �������� |
| taskId | string | �� | 170435,170436 | ����ID |
| dTime | string | �� | 20161101000000-20161102000000 | ����ʱ�䷶Χ����ʱ���һ���£� |
| dHeader | string | �� | ROLE\_ID,CITY\_CODE,D\_TIME | ָ�����ص�ָ��,������ŷָ�,�����ֶβ鿴dHeader�ֵ�� |
| user | string | �� | bonreetest | V4�û��� |
| weekTime | string | �� | {"startWeek":"1", "endWeek":"3","startHour":"00:00","endHour":"12:00"} | ѡ��dTimeʱ���ڵĽ���,ʾ��ֵ��ʾ��ѯ��һ������,0�㵽12�㷶Χ�ڵ����� |
| dateFM | string | �� | Ĭ����yyyy-MM-dd HH:mm:ss | ����ʱ������ |
| filters | string | �� | {"browser":\["1","2"\],"os":\["2","3","4"\],"clientIds":{"selected":"in", "ids":\["123", "456"\]}} | �ֶ�ֵɸѡ����,���ɸѡ�����б� |
| group | string | �� | ROLE\_ID,CITY\_CODE | �����������ֶ�˳��Ϊ����˳�� |
| mainIndex | string | �� | {"name":"D\_TIME", "warnNormal":"10","warnGeneral":"20"} | ��ָ��,���������Сֵ,���ֵ,��λ����ƽ��ֵ;warnNormal��������ֵ;warnGeneral��ͨ����ֵ,�������õ�ֵ�������ٱ� |
| calType | string | �� | avg/max/min/mid | ָ����㷽ʽ,ֻ����ָ��������λ��,Ĭ��Ϊƽ��ֵ |
| pageNum | int | �� | 1 | ��ҳ�������ڼ�ҳ |
| pageRecorders | int | �� | 50 | ��ҳ��ѯʱ����ҳ������ |
| granule | string | �� | STR\_HOUR | ��ѯ���ݵ�ʱ��Ƶ�ȣ���λΪ���ӣ�����ʱ��Ƶ�ȵ�ʱ��group�������� |
| order | string | �� | ROLE\_ID ASC,CITY\_CODE DESC | �������� |
| dgmParam | string | �� | {"group":{"123":\["1100101\_1\_1"\],"124":\["1100101\_2\_1"\]}, "groupDmg":"true"} | ����ͳ������,groupDmg:�Ƿ����;groupΪ����ķ�������,keyΪgroupId,valueΪ������,������ʽΪCITYCODE\_NETSERVICEID\_CLIENTTYPE;���ص�������ÿ�ж�����DMG\_ID���ڱ�ʶ�����ĸ������ |

### filters�ֶ�

| �������� | �������� | �Ƿ���� | ʾ��ֵ | ����˵�� |
| :--- | :--- | :--- | :--- | :--- |
| monitors | string | �� | {"idc": {"selected": "in","agents": \["1100101\_1","1100101\_2" \]},"lm": {"selected": "all","agents": \[\]},"mb": {"selected": "notin","agents": \["1100503\_16"\]},"bmtp": {"selected": "all","agents": \[\]},"pp": {"selected": "all","agents": \[\]}} | ��������,Ĭ��ȫѡ.selected��ʾѡ������,all:Ϊȫ��ѡ��;in:ѡ��agents�����ֵ,notin:�ų�agents�����ֵ;agentsΪ����,�����ֵΪ�ַ���,citycode\_netserverid |
| access | string | �� | \["1","2"\] | ���뷽ʽ,��֧��wap��bmtp |
| agentSpeed | string | �� | \["1","2","3"\] | �������,1:\[0, 512Kb\];2:\(512Kb, 2Mb\];3:\(2Mb, 4Mb\];4:\(4Mb, 10Mb\];5:\(10Mb, 20Mb\];6:\(20Mb, ��\) |
| browser | string | �� | \["1","2","3"\] | ����������汾,1: IE6; 2: IE7; 3: IE8; 4:IE9; 5:IE10; 6:IE11; 100:chrome\(WebKit\); 101:chrome\(blink\); -1:���� |
| os | string | �� | \["2","3","4","5"\] | �������ϵͳ�汾: 2:WIN2003; 3:WINXP; 4:WINVISTA; 5:WIN7; 6:WIN8; 9:WIN10; -1:���� |
| clientIds | string | �� | {"selected":"in", "ids":\["123", "456"\]} | �ͻ���ID,selected��ʾѡ������,in:ѡ��ids�����ֵ,notin:�ų�ids�����ֵ |
| clientIPs | string | �� | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | �ͻ���IP,selected��ʾѡ������,in:ѡ��ips�����ֵ,notin:�ų�ips�����ֵ |
| clientDNS | string | �� | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | �ͻ���DNS,selected��ʾѡ������,in:ѡ��ips�����ֵ,notin:�ų�ips�����ֵ |
| roleIPs | string | �� | {"selected":"in", "ips":\["1.1.1.1", "8.8.8.8"\]} | Ŀ��IP,selected��ʾѡ������,in:ѡ��ips�����ֵ,notin:�ų�ips�����ֵ |
| CPURate | string | �� | {"min":"48", max:"60"} | �ͻ���CUPռ���� |
| memoryRate | string | �� | {"min":"48", max:"60"} | �ͻ����ڴ�ռ���� |
| processNum | string | �� | {"min":"48", max:"60"} | �ͻ��˽������� |
| cycleSpeed | string | �� | {"min":"1000", max:"2000"} | ����ƽ���ٶ�,��λ:KB/s |
| cycleSpeedWeigh | int | �� | 2 | �����ٶȴ��ڼ�����ƽ�������ٶ� |
| tracertMatching | int | �� | 0 | �Ƿ�ƥ�����ip 0:��;1:�� |
| groupFilter | int | �� | 0 | �Ƿ��ų���������һ������,0:��;1:�� |
| errorIds | string | �� | \["302","404"\] | ����ID,Ĭ�ϰ���0 |
| performanceIndex | string | �� | {"type":"0","index":"D\_TIME","min":"0.5","max":"1.0","mark":"0", "group":"0"} | ָ��ɸѡ,type:ɸѡ��ʽ,0:ָ��ֵ,1:ָ��ٷֱ�,2:������; index:ָ��; min:��Сֵ; max:���ֵ; mark:��ʶ,0:��\(����\),1:��\(�ų�\);group����, typeΪ1��2ʱ��Ч,0��ʾû�з���,1��ʾ������Ӫ��,2��ʾ������Ӫ�� |
| hijack | int | �� | 0 | �Ƿ��ų��ٳ�����;0:���ų�;1�ų� |
| clickParam | string | �� | {"onlyError":"0","granule":{"key":"STR\_HOUR","value":"201708302300"},"index":{"ROLE\_IP":"1.1.1.1","OS\_VERSION":"2"},"indexFilter":{"name":"D\_TIME","min":"0.097","max":"0.099"}} | �������,onlyError:1ֻ�д���;0����;2ֻ����ȷ;granule����,key��ʾ���ʱ������,value��ʾ���ȵ�ֵ;indexָ��,�������ָ��ɸѡ����,indexFilter����ֵɸѡ,nameָ������,min��Сֵ,max���ֵ,����ҿ� |

#### ʱ��Ƶ���ֵ��

| ֵ | ���� |
| :--- | :--- |
| STR\_MINUTE5 | 5����Ƶ�� |
| STR\_MINUTE10 | 10����Ƶ�� |
| STR\_MINUTE15 | 15����Ƶ�� |
| STR\_MINUTE30 | 30����Ƶ�� |
| STR\_HOUR | 1СʱƵ�� |
| STR\_HOUR2 | 2СʱƵ�� |
| STR\_HOUR4 | 4СʱƵ�� |
| STR\_HOUR8 | 8СʱƵ�� |
| STR\_HOUR12 | 12СʱƵ�� |
| STR\_DAY | 1��Ƶ�� |
| STR\_WEEK | 1��Ƶ�� |
| STR\_MONTH | 1����Ƶ�� |
| STR\_YEAR | 1��Ƶ�� |

# dHeader�ֵ��

### ͳ���ֶ�:

| �ֶ�Ӣ������ | �ֶ��������� | ��ע |
| :--- | :--- | :--- |
| ROLE\_ID | ����ID |  |
| D\_TIME | ��������\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| DOWN\_SPEED | ƽ�������ٶ�\(KB/s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| DOWN\_TIME | ������ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| DNS\_TIME | DNS��ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| TCP\_TIME | TCP��ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| SEND\_TIME | ������ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| R\_TIME | ��Ӧ��ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| SSL\_TIME | SSL������ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| ONEBYTE\_TIME | �װ���ʱ\(s\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| BYTES\_RECEIVED | �����С\(KB\) | $MIN��Сֵ;$MAX���ֵ;$MID��λ�� |
| USEABLE | �ɹ���\(%\) | ��Ч����/\(��Ч����+�������\) |
| ERRNUM | ������� |  |
| MNUM | ��Ч������ |  |
| SLOW\_RATE | ���ٱ�\(%\) |  |
| HIJACK | �ܽٳִ��� |  |
| HIJACKPER | �ٳֱ���\(%\) |  |
| HIJACKDNS | �����ٳִ��� |  |
| CITY\_CODE | ������ |  |
| DISTRICTCODE | ������ |  |
| NETSERVICE\_ID | ��Ӫ���� |  |
| ROLE\_CITYCODE | Ŀ������� |  |
| ROLE\_DISTRICTCODE | Ŀ������� |  |
| ROLE\_NETSERVICE | Ŀ����Ӫ���� |  |
| ARRIVAL\_SCALE | ������ |  |
| COVERAGE\_SCALE | ������ |  |

# ���ز���˵��

| ���� | ���� | ���� |
| :--- | :--- | :--- |
| errorCode | int | ������,0��ʾ��ѯ���� |
| reason | string | ����˵�� |
| result | string | ���ؽ���� |

# ����ʾ��

```
        HttpClient httpclient = new DefaultHttpClient();
        String url = "https://api.bonree.com/net/report/transfer";
        HttpPost httppost = new HttpPost(url);
        System.out.println("����: " + httppost.getRequestLine());
        // ������������
        List<NameValuePair> formparams = new ArrayList<NameValuePair>();
        formparams.add(new BasicNameValuePair("username", "bonreetest"));
        formparams.add(new BasicNameValuePair("token", "xxxxxxxxxx"));
        formparams.add(new BasicNameValuePair("params", "{\"dType\":\"json\",\"taskId\":\"1035\",\"user\":\"bonreetest\",\"dTime\":\"20170201000000-20170301000000\",\"dHeader\":\"ROLE_ID,CITY_CODE,D_TIME\",\"group\":\"ROLE_ID,CITY_CODE\"}"));
        UrlEncodedFormEntity uefEntity = new UrlEncodedFormEntity(formparams, "UTF-8");
        httppost.setEntity(uefEntity);
        // ִ��
        HttpResponse response = httpclient.execute(httppost);
        HttpEntity entity = response.getEntity();
        System.out.println("----------------------------------------");
        System.out.println("״̬:" + response.getStatusLine());
        if (entity != null) {
            System.out.println("Response content length: " + entity.getContentLength());
            System.out.println("Response content :" + EntityUtils.toString(entity, "UTF-8"));
        }
        // �ر�����,�ͷ���Դ
        httpclient.getConnectionManager().shutdown();
```

# ���ؽ��ʾ��

```
{
    "error_code": 0,
    "reason": "��ѯ�ɹ�",
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

# api���ߣ�

api���Թ��ߣ� api��Ӧ���ѯ���ߣ������ѯ���ߣ�ָ���ѯ���ߣ�������ݴ������ѯ����

# FAQ��



