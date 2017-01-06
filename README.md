# FDSDKServer
[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://raw.githubusercontent.com/seven/FDSDKServer/master/LICENSE)&nbsp;

互冠聚合SDK服务端文档


##简介

* 介绍
** 本文档提供用户验证会话接口说明，CP接收发货通知说明
* 声明
** 接口文档中涉及的AppID,AppKey开发者后台进行申请. 由于涉及到加密通信, 开发者必须严格对AppKey进行保密。
** 接口文档中所有的签名编码都为UTF-8。
** 只允许申请的业务使用，严禁申请方做二次开发提供给未授权方使用。如发现违反以上声明，将追究擅自使用人的责任。
** 本文档涉及的技术均采用主流的Web开发技术, 相关技术(如JSON)等若不清楚, 可通过互联网搜索即可了解. 本文档不做单独解释。
** 文档所有接口仅支持POST方式；返回信息全部为JSON结构。
** 聚合sdk提供的是对各个渠道sdk接口的整合封装与转发，若有渠道方禁止接入第三方接口，CP方应详询渠道方及承担相应责任。