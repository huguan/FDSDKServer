# 互冠聚合FDSDK服务端文档
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://raw.githubusercontent.com/huguan/FDSDKServer/master/LICENSE)&nbsp;

##简介


* 本文档提供用户验证会话接口说明，CP接收发货通知说明
* 接口文档中涉及的AppID,AppKey开发者后台进行申请. 由于涉及到加密通信, 开发者必须严格对AppKey进行保密。
* 接口文档中所有的签名编码都为UTF-8。
* 只允许申请的业务使用，严禁申请方做二次开发提供给未授权方使用。如发现违反以上声明，将追究擅自使用人的责任。
* 本文档涉及的技术均采用主流的Web开发技术, 相关技术(如JSON)等若不清楚, 可通过互联网搜索即可了解. 本文档不做单独解释。
* 文档所有接口仅支持POST方式；返回信息全部为JSON结构。
* 聚合sdk提供的是对各个渠道sdk接口的整合封装与转发，若有渠道方禁止接入第三方接口，CP方应详询渠道方及承担相应责任。

##用户验证
####接口地址
<table>
    <thead>
        <tr>
            <th>地址类型</th>
            <th>地址</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>正式地址</td>
            <td>http://anysdk.huguangame.com/verify.php</td>
        </tr>
    </tbody>
</table>

####请求参数
<table>
    <thead>
        <tr>
            <th>参数名</th>
            <th>参数规格</th>
            <th>必填</th>
            <th>说明</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>appID</td>
            <td>Int</td>
            <td>是</td>
            <td>应用ID</td>
        </tr>
        <tr>
            <td>userId</td>
            <td>String</td>
            <td>是</td>
            <td>客户端SDK返回的userId</td>
        </tr>
        <tr>
            <td>token</td>
            <td>String</td>
            <td>是</td>
            <td>客户端SDK返回的登录令牌</td>
        </tr>
        <tr>
            <td>sign</td>
            <td>String</td>
            <td>是</td>
            <td>签名</td>
        </tr>
    </tbody>
</table>

####签名方式<br>
sign = MD5(appID + token + appKey)


####返回值
<table>
    <thead>
        <tr>
            <th>参数名</th>
            <th>参数规格</th>
            <th>必填</th>
            <th>说明</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>errorCode</td>
            <td>Int</td>
            <td>是</td>
            <td>错误码（参考附录表）</td>
        </tr>
        <tr>
            <td>data</td>
            <td>json</td>
            <td>是</td>
            <td>验证信息</td>
        </tr>
        <tr>
            <td rowspan="4">
            </td>
            <td colspan="1">
                参数名
            </td>
            <td colspan="1">
                类型
            </td>
            <td colspan="1">
                说明
            </td>
        </tr>
        <tr>
            <td>
               id
            </td>
            <td>
                Stirng
            </td>
            <td>
                用户id
            </td>
        </tr>
        <tr>
            <td>
               account
            </td>
            <td>
                String
            </td>
            <td>
                用户唯一id（即  account）
            </td>
        </tr>
        <tr>
            <td colspan="3">
               验证不正确时，data没数据，只有errorCode
            </td>
        </tr>
        
        
    </tbody>
</table>

####返回值示例
```
//JSON:
{    
    "errorCode": 0,
    "data":
    {
        "id": "1"
        "account": "1"
    }
}
```

##发货通知接口
####接口地址
<table>
    <thead>
        <tr>
            <th>地址类型</th>
            <th>地址</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>正式地址</td>
            <td>CP在开发者后台配置的通知地址，必须以http:// 开头,可以使用域名（或IP地址）+ 端口形式</td>
        </tr>
    </tbody>
</table>


####请求参数
<table>
    <thead>
        <tr>
            <th>参数名</th>
            <th>参数规格</th>
            <th>必填</th>
            <th>说明</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>productID</td>
            <td>string</td>
            <td>是</td>
            <td>商品id</td>
        </tr>
        <tr>
            <td>productName</td>
            <td>string</td>
            <td>是</td>
            <td>商品名称</td>
        </tr>
        <tr>
            <td>orderNum</td>
            <td>string</td>
            <td>是</td>
            <td>SDK系统内部订单号</td>
        </tr>
        <tr>
            <td>roleId</td>
            <td>string</td>
            <td>是</td>
            <td>游戏玩家roleId</td>
        </tr>
        <tr>
            <td>serverID</td>
            <td>string</td>
            <td>是</td>
            <td>游戏服务器Id</td>
        </tr>
        <tr>
            <td>channelID</td>
            <td>string</td>
            <td>是</td>
            <td>渠道编号</td>
        </tr>
        <tr>
            <td>userID</td>
            <td>string</td>
            <td>是</td>
            <td>SDK帐号id</td>
        </tr>
        <tr>
            <td>addTime</td>
            <td>string</td>
            <td>是</td>
            <td>订单生成时间，格式：yyyy-MM-ddHH:mm:ss </td>
        </tr>
        <tr>
            <td>endTime</td>
            <td>string</td>
            <td>是</td>
            <td>订单完成时间，格式：yyyy-MM-ddHH:mm:ss</td>
        </tr>
        <tr>
            <td>money</td>
            <td>string</td>
            <td>是</td>
            <td>金额(单位：分)</td>
        </tr>
        <tr>
            <td>extension</td>
            <td>string</td>
            <td>是</td>
            <td>CP扩展信息，客户端SDK传入，原样返回</td>
        </tr>
        <tr>
            <td>sign</td>
            <td>String</td>
            <td>是</td>
            <td>签名</td>
        </tr>
    </tbody>
</table>

####签名方式
MD5(productID + roleId + orderNum + endTime + appKey)

####返回值示例
```
请求成功返回字符串: SUCCESS
请求错误返回字符串: FAIL
```

####说明
各个渠道对充值回调有不同的处理，只有CP返回SUCCESS时，渠道方才认为充值回调成功。若未收到CP的成功回复，渠道方可能会尝试继续发送回调请求，CP方要自行判断重复请求。


##附录
<table>
    <thead>
        <tr>
            <th>错误码</th>
            <th>含义</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0</td>
            <td>成功</td>
        </tr>
        <tr>
            <td>1</td>
            <td>参数不对</td>
        </tr>
        <tr>
            <td>2</td>
            <td>签名错误</td>
        </tr>
        <tr>
            <td>3</td>
            <td>渠道编号不存在</td>
        </tr>
        <tr>
            <td>4</td>
            <td>渠道SDK请求出错</td>
        </tr>
        <tr>
            <td>5</td>
            <td>http方法不正确</td>
        </tr>
        <tr>
            <td>6</td>
            <td>渠道关闭</td>
        </tr>
        <tr>
            <td>7</td>
            <td>渠道SDK版本过旧</td>
        </tr>
        <tr>
            <td>8</td>
            <td>渠道SDK参数未设置</td>
        </tr>
        <tr>
            <td>9</td>
            <td>渠道SDK参数错误</td>
        </tr>
        <tr>
            <td>10</td>
            <td>验证超时</td>
        </tr>
        <tr>
            <td>11</td>
            <td>TOKEN验证不通过</td>
        </tr>
         <tr>
            <td>12</td>
            <td>玩家不存在</td>
        </tr>
        <tr>
            <td>13</td>
            <td>玩家未登录</td>
        </tr>
    </tbody>
</table>


许可证
==============
HGSDK 使用 MIT 许可证，详情见 LICENSE 文件。
