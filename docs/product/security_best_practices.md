# 环信即时通讯 IM 安全最佳实践

<Toc />

安全合规对于即时通讯技术至关重要，为了提供安全可靠的云服务，环信即时通讯 IM 遵循不同国家、地区和行业的合规要求。环信即时通讯 IM 采用多种安全措施，防御即时通讯场景中的常见攻击。本文介绍环信即时通讯 IM 采用的一些安全最佳实践以及为开发者提供的安全工具。

环信用户隐私协议见：[环信用户隐私协议](https://www.easemob.com/protocol)。
| 安全措施     | 默认启用 | 建议场景                                          |
|:-------------|:---------|:--------------------------------------------------|
| 数据中心隔离 | 是       | 所有即时通讯场景。                                  |
| Token 鉴权   | 是       | 所有即时通讯应用都必须使用用户身份的 token 进行鉴权。 |
| 数据传输加密 | 是       | 所有即时通讯场景。                                  |
| 数据存储加密 | 是       | 所有即时通讯场景。                                  |

## 数据中心隔离

为了满足不同国家和地区的法律和规定，环信即时通讯 IM 支持服务区域隔离，以保证指定区域内的用户隐私数据不跨境。

环信即时通讯 IM 在如下区域设立数据中心，数据中心支持区域访问：

| 数据中心 | 地点           | 服务区域 |
|:---------|:---------------|:---------|
| 新加坡   | 新加坡         | 东南亚   |
| 中国大陆 | 北京           | 中国大陆 |
| 欧洲     | 法兰克福，德国 | 欧洲     |
| 北美     | 弗吉尼亚，美国 | 北美     |

使用环信即时通讯 IM 服务时，需要指定数据中心。选择数据中心后，REST 和 SDK API 对于消息服务器的请求都将指向对应的数据中心。

数据中心一经选定不可更改。环信即时通讯 IM 不支持跨区域的数据迁移服务。所有数据均会保存在指定的数据中心。

## Token 鉴权

环信即时通讯 IM 使用 token 进行最终用户身份验证。Token 是一个访问密钥，开发者可以设置 token 的有效期。它由应用后端生成，包含环信即时通讯 IM 项目的 App ID、项目 APP 证书、用户 ID 等重要信息。它允许最终用户在用户通过应用程序正确验证后访问环信即时通讯 IM 服务。

## 数据传输和存储

用户和环信即时通讯 IM 服务器的通信进行了传输加密，比如：环信即时通讯 IM 私有传输协议，Transport Layer Security (TLS) 和 Web Socket Secure (WSS)。使用环信即时通讯 IM 产生的用户数据和消息将存储在指定的区域的数据中心。我们仅在为您提供服务期间保留您的信息，保留时间不超过满足相关使用目的所必须的时间。

| 数据类型                                 | 数据分类 | 存储时间                                                                              |
|:-----------------------------------------|:---------|:--------------------------------------------------------------------------------------|
| Console 注册数据                          | 客户信息 | 直至客户删除账号或服务停用 6 个月。                                                     |
| 消息（包括历史消息、漫游消息、离线消息） | 用户信息 | 根据消息云存储时长进行保存。<br> 专业版 7 天、旗舰版 90 天、尊享版 180 天。 |
| 消息附件                                 | 用户信息 | 7 天。                                                                                   |
| 消息回调                                 | 用户信息 | 3 天。                                                                                   |
| 用户资料托管                             | 用户信息 | 直到客户删除或服务停用 6 个月。                                                         |
| 监控数据                                 | 运营数据 | 7 天。                                                                                      |