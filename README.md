

# Rules For Quantumult X

此项目基于 [sve1r](https://github.com/sve1r)/**[Rules-For-Quantumult-X](https://github.com/sve1r/Rules-For-Quantumult-X)** 、 [GeQ1an](https://github.com/GeQ1an)/**[Rules](https://github.com/GeQ1an/Rules)** （已删库）和 [Oxin92o](https://github.com/Oxin92o)/**[QuantumultX](https://github.com/Oxin92o/QuantumultX)** 的预配置文件重新整合及调整制作

 **仓库内容来源于网络中 如有侵权或未标明出处请预留issue**

Readme 修改自 [sve1r](https://github.com/sve1r)/**[Rules-For-Quantumult-X](https://github.com/sve1r/Rules-For-Quantumult-X)**

-----

# **🉑 简要说明**

### `♾ Rules 和 Rewrite 部分`

- 国内直连、海外加速
- Apple 服务(可选择性)加速
- 海外媒体（部分）服务指定节点
- 拦截运营商劫持
- 拦截臭名昭著的欺诈网站（如**思杰马克丁**伪造的一系列软件官网、MacKeeper等）
- 拦截应用广告
  ⚠️ 网页广告请使用 Safari 内容拦截器如 [ADGuard](https://apps.apple.com/app/apple-store/id1047223162) 或集成去广告功能浏览器

### `🔙 BackCN 部分`

- 国内媒体服务解锁
- 拦截应用广告
  ⚠️ 网页广告请使用 Safari 内容拦截器如 [ADGuard](https://itunes.apple.com/app/apple-store/id1047223162?mt=8) 或集成去广告功能浏览器

### `🌐 公共 DNS 推荐`

    - https://doh.pub/dns-query
    - 119.29.29.29 [腾讯DnsPod+]
    - 182.254.116.116
    - 223.5.5.5 [阿里云公共DNS]
    - 223.6.6.6

# **1️⃣使用指南**
>详细的带图指南请参考 @Shawn 提供的 [Quantumult X 不完全指南](https://www.notion.so/Quantumult-X-1d32ddc6e61c4892ad2ec5ea47f00917#bb2dce7c01114955bbdbbd222f2a5fcf)
### 1.配置要求
 - 列表内规则仅适用于 Quantumult X
 - 请将规则添加至 **分流** 列表中
 - 请使用规则的 **raw 链接**

### 2.安装步骤

1. 设置预配置 config
```
例如

  https://raw.githubusercontent.com/MironChen/proxy-rules/master/SabrinaQuanxConf.conf
```

2. 选择你想要使用的规则（本仓库附带两个 config 文件，可按需选择
3. 获取列表的 RAW 链接

```
例如：
  
  https://raw.githubusercontent.com/MironChen/proxy-rules/master/Rules/SabrinaQuanxConf/AdBlock.list
  此为浏览器地址栏中获取到的链接
```
4. 搭建 **[gh-proxy](https://github.com/hunshcn/gh-proxy)**
5. 使用 **gh-proxy CDN** 替换 RAW 链接,以避免更新配置时出错的相关问题

```
  假设你在 ph-proxy 的链接为 https://example.com
  
  如需使用 https://raw.githubusercontent.com/MironChen/proxy-rules/master/Rules/SabrinaQuanxConf/AdBlock.list 
  
  则在 https://raw.githubusercontent.com 添加 https://example.com/ (原链接的 https:// 可删除)
  
  替换后链接为 https://example.com/raw.githubusercontent.com/MironChen/proxy-rules/master/Rules/SabrinaQuanxConf/AdBlock.list
```



### 3.推荐排序（使用 sve1r.conf）

> 推荐使用的规则排序如下
```
1. Unbreak.list - 用于修正 PROXY 和 REJECT 行为
2. Advertising.list - 广告、行为分析、隐私追踪（macOS 不建议开启）
3. Hijacking.list - 劫持（运营商、臭名昭著的诈骗网站或恶意应用）
4. ForeignMedia.list - 国际流媒体
5. DomesticMedia.list - 国内流媒体（可不加）
6. Global.list - 国际网站/应用
7. Apple.list - Apple 服务（可不加）
9. China.list - 国内网站/应用
```

**说明**

- 如若**不需要**观看哔哩哔哩、爱奇艺面向港澳台的限定内容可不加「DomesticMedia.list」。
- 如若**不需要**代理 Apple 服务可不加「Apple.list」，若加入必须在「Global.list」和「China.list」之间。
- 如需细化流媒体如「Youtube.list」需要加在「ForeignMedia.list」之前。
- 如需应用类的如「Telegram.list、Google.list、PayPal.list」需要加在「Global.list」之前。

一般情况下默认引入上述 8 个（如不需要 DomesticMedia 和 Apple 可减至 6 个）即可，那么为什么还有更多的如「Youtube.list、Netflix.list、Spotify.list、Mail.list」？

1. 对于一些「进阶玩家」来说其拥有专用于观看流媒体的线路，比如观看限定区域的 Netflix、Hulu、HBO 等，所以引入相关 .list 建立一个策略组设置相应服务区节点线路。但对于普通用户来说，那些「Youtube.list、Hulu.list」来说都是集成在「ForeignMedia.list」中**不需要**额外引入。
2. 对于一些「机场」来说为了避免有恶意用户利用节点线路滥发垃圾邮件，所以对服务器相关邮件端口进行了屏蔽，这时候可以引入「Mail.list」指定一个可收发邮件对节点。
3. 对于一些「进阶玩家」来说其拥有高速的新加坡节点线路，为了提升 Telegram 使用体验所以会引入「Telegram.list」指定一些节点。

综上所述、以此类推，独立的 .list 一般都集成在了默认的 6 条 .list 文件中，如果你没有进阶的定制化需求是**不 需 要**引入那么多的，根据需求使用才是 Ruleset/Filter 的灵活用法，规则不是越多越好。



# **2️⃣常见问题**

> 0.Final 有什么作用？该怎样使用？

⚠️ 注意：在日常使用之中，我们推荐使用 [Final，Proxy] 模式，除非有着特殊需求。

换种方式而言，就是除了配置文件中选定规则以外的所有请求，都通过代理访问。

- GeoIP 规则已经可以解决绝大多数的境内网站直连。
- 而剩下未能被匹配的规则使用 Final 就好。

> 1.遇到连接公共场所 Wi-Fi 时验证页面无法显示？

请暂时关闭待验证成功后再开启，或者如校园网运营商客户端的可将相关域名或 IP 地址手动加入至 【分流】中。

> 2.打开「淘宝」等阿里系应用时遇到「访问被拒绝」、「请检查是否使用了代理」等提示

部分「阿里云」节点会导致此问题，请尝试使用其他节点。

> 3.关于 Speedtest 想直连/代理？

规则对于 Speedtest 不是绝对的直连也不是绝对的代理，对于国内测速点是直连，对于国外测速点是代理。

默认打开 Speedtest 会自动选择适用于代理服务器节点的国外测速节点，若要进行国内网速测试手动修改「测速点」搜索你所在城市或省会的拼音然后选择运营商即可。



# **3⃣️如何参与本项目**

>贡献使开源社区成为一个学习、激励和创造的绝佳场所。你所作的任何贡献都是**非常感谢**的。
如果你对规则有更好的建议欢迎你提交更改。你可以按如下步骤：

1. Fork 此仓库
2. 单独建立一个分支 (`git checkout -b feature/AmazingFeature`)
3. 提交规则的变更 (`git commit -m 'Add some AmazingFeature'`)
4. 将规则推送 (`git push origin feature/AmazingFeature`)
5. 提交合并申请 (Click `New Pull Request`)



# **4⃣️来源与鸣谢**
- [@sve1r](https://github.com/sve1r)
- [@GeQ1an](https://github.com/GeQ1an)/**[Rules](https://github.com/GeQ1an/Rules)**
- [@Oxin92o](https://github.com/Oxin92o)
- [@NobyDa](https://github.com/NobyDa/Scipts)
- [@anti-AD V4](https://github.com/privacy-protection-tools/anti-AD)
- [@ConnersHua](https://github.com/ConnersHua)
- [@lhie1](https://github.com/lhie1)
- Lison Bin
- [@linjiacheng](https://github.com/linjiacheng)
- @Booui
- @liceva
- [@JO2EY](https://github.com/JO2EY) 
- [@Choler](https://github.com/Choler)
- [@xream](https://github.com/xream)
- [@gkeyes](https://github.com/gkeyes)
- [@LeeeMooo](https://github.com/LeeeMooo)
- [@uranuswch](https://github.com/uranuswch)

# **5⃣️许可与说明**

- 此项目基于 [sve1r](https://github.com/sve1r)/**[Rules-For-Quantumult-X](https://github.com/sve1r/Rules-For-Quantumult-X)** 、 [GeQ1an](https://github.com/GeQ1an)/**[Rules](https://github.com/GeQ1an/Rules)** （已删库）和 [Oxin92o](https://github.com/Oxin92o)/**[QuantumultX](https://github.com/Oxin92o/QuantumultX)** 的预配置文件重新整合及调整制作
- 本项目的所有文件，README 等资源基于一个 [MIT License](LICENSE) 发布，你可以拷贝、再发行本项目的内容, 但是你将必须：
  - 使用**完全相同**的条款和格式发布。
  - 请注明原作者信息以及协议声明。
  - 同时请勿**将本项目用于商业用途**，**任何盈利活动都属于商业用途**。
- 本项目的所有代码除另有说明外，均基于MIT License发布。
- 此处的文字仅用于说明，条款以LICENSE文件中的内容为准。
- 请在遵守当地相关法律法规的前提下使用本项目，我们不为使用此项目内容出现问题负任何责任。



