# GetLiveChannelHistory {#reference_kjz_yld_xdb .reference}

GetLiveChannelHistory接口用来获取指定LiveChannel的推流记录。

## 请求语法 {#section_wtq_bmd_xdb .section}

```
GET /ChannelName?live&comp=history HTTP/1.1
Date: GMT date
Host: BucketName.oss-cn-hangzhou.aliyuncs.com
Authorization: SignatureValue
```

## 响应元素 {#section_kln_dmd_xdb .section}

|名称|类型|描述|
|:-|:-|:-|
|LiveChannelHistory|容器|保存GetLiveChannelHistory返回结果的容器。子节点：LiveRecord

父节点：无

|
|LiveRecord|容器|保存一次推流记录信息的容器。子节点：StartTime，EndTime，RemoteAddr

父节点：LiveChannelHistory

|
|StartTime|字符串|推流开始时间，使用ISO8601格式表示。子节点：无

父节点：LiveRecord

|
|EndTime|字符串|推流结束时间，使用ISO8601格式表示。子节点：无

父节点：LiveRecord

|
|RemoteAddr|字符串|推流客户端的ip地址。子节点：无

父节点：LiveRecord

|

## 细节分析 {#section_t2r_lmd_xdb .section}

目前最多会返回指定LiveChannel最近的10次推流记录。

## 示例 {#section_znp_mmd_xdb .section}

**请求示例**

```
GET /test-channel?live&comp=history HTTP/1.1
Date: Thu, 25 Aug 2016 07:00:12 GMT
Host: test-bucket.oss-cn-hangzhou.aliyuncs.com
Authorization: OSS YJjHKOKWDWINLKXv:pqgDBP8JXTXAytBoXpvNoZfo68k=
```

**返回实例**

```
HTTP/1.1 200
content-length: 1892
server: AliyunOSS
connection: close
x-oss-request-id: 57BE977CB92475920B0022FB
date: Thu, 25 Aug 2016 07:00:12 GMT
content-type: application/xml
<?xml version="1.0" encoding="UTF-8"?>
<LiveChannelHistory>
  <LiveRecord>
    <StartTime>2016-07-30T01:53:21.000Z</StartTime>
    <EndTime>2016-07-30T01:53:31.000Z</EndTime>
    <RemoteAddr>10.101.194.148:56861</RemoteAddr>
  </LiveRecord>
  <LiveRecord>
    <StartTime>2016-07-30T01:53:35.000Z</StartTime>
    <EndTime>2016-07-30T01:53:45.000Z</EndTime>
    <RemoteAddr>10.101.194.148:57126</RemoteAddr>
  </LiveRecord>
  <LiveRecord>
    <StartTime>2016-07-30T01:53:49.000Z</StartTime>
    <EndTime>2016-07-30T01:53:59.000Z</EndTime>
    <RemoteAddr>10.101.194.148:57577</RemoteAddr>
  </LiveRecord>
  <LiveRecord>
    <StartTime>2016-07-30T01:54:04.000Z</StartTime>
    <EndTime>2016-07-30T01:54:14.000Z</EndTime>
    <RemoteAddr>10.101.194.148:57632</RemoteAddr>
  </LiveRecord>
</LiveChannelHistory>
```

