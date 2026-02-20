+++
date = '2026-02-21T00:11:29+08:00'
draft: false
title = 'Clash的最佳实践配置'
+++

[Clash for Windows 使用教程](https://help.mints7.cc/windows-jiao-cheng/clash-jiao-cheng)

## **关于一些客户端作者停止更新**

这些客户端停止更新了, 对我们的使用是否有影响呢? 想要知道这个问题的答案, 首先我们先明白一个概念，Clash Verge(开源)、Clash for Windows、Clash X Pro这一类图形化的软件，**都是一个壳**，用于对接核心的功能, 停止更新的只是这个**壳**。

**常见的核心**有Clash Premium、Clash Meta(开源)

因为Clash Verge和他能切换的内核Clash Meta**都是开源的**，所以我们应该优先选这个搭配，下文中也会使用。

那我们还能够继续使用他们吗?

**当然可以**，解释如下

1. 就像你在使用一个收音机_(Clash Verge)_，你不会因为收音机的制造商_(作者) _倒闭了_(停止更新)_，而立刻扔掉你的收音机

2) 收音机的所有零件图纸是公开_(开源) _的，你不用担心他可能植入一些不好的后台程序

3. 收音机的外壳按钮_(Clash Verge)_ ，是让我们更轻松的控制收音机里面的主板元件_(Clash Meta核心) _去执行它们的任务，只要这个 外壳按钮_(Clash Verge)__ _控制 收音机主板_(Clash Meta核心)__ _的方式没有太大问题，那我们就可以用

4) 外壳停止更新，意味着收音机外壳不会增加新的按钮

5. 核心停止更新，意味着收音机主板不会更新功能，仅此而已

6) 收音机能播放声音_(开启魔法)_，是因为你输入了正确的FM频率_(订阅链接)。_只要电台_(机场) _还在广播_(服务)_，只要你的壳和核还在，就不影响你播放声音_(开启魔法)_

最后，我们要明确一点，**下文中涉及到隐私保护的操作并不是绝对的安全**，就像是想要知道你在家里做什么，可以在楼下垃圾桶翻你的扔的垃圾进行推测，可以望远镜监视你，可以把你家天花板炸了或者用大炮强行冲进来看。网络监控也一样，就看你在网络上的行为，值不值得人家用那些高阶手段了，总不能因为挖掘机一铲子能把防盗门破了我就不装防盗门了。

## **目前可用的开源Clash Verge客户端**

现在有不少基于Clash Verge继续开发维护的客户端

* [clash-verge-rev (推荐)](https://github.com/clash-verge-rev/clash-verge-rev/releases) 后面的文章中会基于这个客户端进行演示

- [Clash 喵帕斯](https://github.com/keiko233/clash-nyanpasu/releases)

* [Clash Meta组织维护的Clash Verge](https://github.com/MetaCubeX/clash-verge/releases)

- [Clash Verge 1.3.8原版](https://github.com/zzzgydi/clash-verge/releases)

为什么是这个软件?

多端兼容性出色——Clash Verge 支持 Windows、macOS、Linux。如果按照下方的教程进行操作，最终将得到一个新的订阅链接，而 iOS 上的软件 Stash 恰好完全兼容该链接中的内容。Clash Verge 与 Stash 的组合可以覆盖几乎所有主流设备，而下方的最佳实践操作，只需执行一次，就可以在众多设备上应用。

应用软件现代化——在确保易用性的前提下，采用较新技术，实现了许多其他客户端不具备的新特性和优秀功能。

## **太长不看版本**

1. 订阅转换**(必做)**

2) 开TUN模式，关代理(可选)

3. 关闭浏览器安全DNS地址，设置TUN模式的DNS地址(可选，如果操作了2，则此项必做)

4) 关闭多宿主DNS解析，系统DNS设置自动，关闭浏览器QUIC(Windows可选)

5. 设置本地中国IP数据库(可选)

## **解决订阅分流规则问题**

拿到了订阅链接，第一步要做的应该就是订阅转换，将他的分流规则完善 (因为给你提供订阅的服务商，自带的分流规则往往就几百条，很不健全，很多人开着Clash但New Bing却用不了就是个很好的例子)

在线订阅转换**不仅仅是将**Shadowsocks、V2ray、Trojan 订阅链接转换为 Clash 、Stash、V2ray、Quantumult X、Surge 等软件使用的订阅格式，他还**支持非常多的**[**进阶操作**](https://github.com/tindy2013/subconverter/blob/master/README-cn.md)，不过在本文仅以**够用**为目标，而不是把这个东西玩出花来。

在线订阅转换网站虽然好用，但也有一定的隐私风险，需要注意，建议会技术的朋友自己搭建在线订阅转换平台。

### **订阅转换网站**

我搭建的订阅转换网站, 下文将使用该网站作为示例

进入: <https://sub.lainbo.com/>

### **需要操作的步骤**

#### 订阅转换

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-06-15-mjzcdtjb.png?x-oss-process=style/bf)

#### 新增订阅配置

左上角点击新建 -> 选择Remote类型 -> 将上面转换好的订阅地址黏贴到订阅链接处 -> 填好自定义信息 -> 点击保存

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-peqaymst.png?x-oss-process=style/bf)

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-cstlfric.png?x-oss-process=style/bf)

一般这样就已经可以比较完美的使用了，并且拥有我写的远程配置文件中的一些额外功能

#### **判断是否成功套用了规则文件**

拉取订阅后, 节点中应该会出现“🌿自动选择”、“🇭🇰香港自动”、“🇨🇳台湾自动”、“🇸🇬狮城自动”、“🇺🇸美国自动”、“🇯🇵日本自动”这几个自动节点。能看到这几个自动节点, 那你就成功在自己的订阅上套用了我的规则。

推荐在没有特殊需求的时候选择用这几个自动节点, 自动节点会帮你使用对应国家/地区节点中, 延迟最低的节点。

#### **关于远程配置**

这个远程配置是什么，能赋予你的订阅什么功能，你可以打开[「远程配置」原文的链接](https://u.lainbo.com/clash-config)，顶部有注释

## **解决DNS泄露问题**

DNS 泄露指的是在使用 VPN 或其他隐私服务的情况下，用户的真实 IP 地址通过 DNS 请求被发送到了 ISP（如联通，移动）的 DNS 服务器，而不是通过 VPN 设置的安全、匿名的 DNS 服务器。如果在 [DNS Leak Test](https://browserleaks.com/dns) 、[ipleak](https://ipleak.net/)这种网站的列表中看到了中国国旗，就要意识到**可能**发生了DNS泄露。

如果真的泄露了有什么问题呢 ? 我也不知道可能导致什么，或许你可能收到下图这样的消息

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-06-15-gthvijxi.png?x-oss-process=style/bf)

我觉得还是尽量不要让他们知道这件事。虽然没有人知道具体的探测机制是什么，但很可能是从网络层面获取的。在一般的家庭网络拓扑中，[wireshark](https://www.wireshark.org/)可以看到什么内容，运营商就能看见什么内容，所以你使用114.114.114.114、223.5.5.5这样的DNS解析去访问了什么网站是很清晰的。

这就要衍生出第一个使用技巧——**Clash开启TUN模式，关闭系统代理去使用**

与普通的系统代理模式区别在于，TUN模式下Clash会创建一张虚拟网卡，从网络层面接管所有的网络流量。

普通的系统代理模式，是作为一个软件的权限去接管别的软件的网络，总有一些无法接管的应用，比如游戏，比如命令行。所以我们应该开启TUN模式，关闭系统代理，让网卡做这件事，而不是让软件做这件事

#### **操作一 (开启TUN模式)**

1. 首先切换Clash Verge的内核，选开源的Clash Meta内核，然后重启整个Clash Verge确保生效

   1. _(Clash Meta在后期可能在不同的客户端名称有所不同, 如果看到内核名字是_`Mihomo`_ 版本号是1.x.x的也是Meta)![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-06-15-joiamdit.png?x-oss-process=style/bf)_

2) 安装服务并且开启Tun模式，按下方图中的数字序号**顺序点击**

   1. ![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-06-15-oltnshra.png?x-oss-process=style/bf)

   2. 如果服务模式无法安装

   3. _Win可以尝试在系统命令行(PowerShell)中执行_`sc delete clash_verge_service`_ 来删除之前的Clash Verge服务，这可能是你之前安装过Clash Verge，但是卸载的时候没有写在这服务模式，导致新的安装不上_

   4. _Mac/Linux请在设置的_`Clash内核`_点开齿轮图标⚙️，点"授权”_

   5. _其他疑难杂症参考_[_https://github.com/clash-verge-rev/clash-verge-rev/issues/125_](https://github.com/clash-verge-rev/clash-verge-rev/issues/125)

但是当我们开启了TUN，再去查看泄露时，发现还是有中国服务器(Windows系统可能出现)。这是由于fake-ip模式将DNS请求**同时**发送给了本地的物理网卡和Clash虚拟网卡，我们希望只发送给Clash的网卡，因为Clash创建的虚拟网卡会按我们的要求做事，本地真实的网卡不会。

#### **操作二 (调整组策略 Mac跳过)**

要解决这个问题也很简单，问题出现的原因是Windows系统默认使用多宿主DNS解析，会使用所有的网卡发起请求，我们只需要在组策略(Windows家庭版无该功能)中关闭这个功能即可(Win+R，输入`gpedit.msc` 点确定)。

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-06-15-rxicqqyk.png?x-oss-process=style/bf)

至此，我们解决了Clash在Windows下可能发生的DNS泄露问题(主要靠分流规则起作用)。

但并不能保证ipleak检测不到，因为这个网站并不被墙。虽然我可以将ipleak加入规则中，但这样做就是掩耳盗铃。只要确保某些黑名单网站不被漏掉，不会收到上面那种短信，我认为就可以了。

#### **操作三 (使用一个稳定的的DNS)**

DNS这部分有人会教使用运营商的DNS，**运营商的DNS只适合小白用户，因为他可能连反诈**，所以建议使用国内大厂的。

1. 关闭浏览器的QUIC, 中国大陆的isp是限速udp的, 所以导致QUIC这个优秀的协议, 到了中国大陆的网络下成了个负面增益效果。

   1. `about://flags/#enable-quic` 设置为`Disabled` (点下方弹出的重启浏览器生效)

2) 关闭浏览器中的“安全DNS”

   1. Chrome: `chrome://settings/security`

      * 【使用安全DNS】_(新版Chrome中叫做【对您访问的网站的名称进行加密】)_，关闭

   2. Edge: `edge://settings/privacy`

      * 找到【安全性】 -【使用安全的 DNS 指定如何查找网站的网络地址】，关闭

3. 在Clash Verge的新版本中，会自带【全局扩展配置】和【全局扩展脚本】两项配置，一般我们将配置写入到【全局扩展脚本】中即可。\
   ![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-kfhctxuy.png?x-oss-process=style/bf)

   1. 你需要将下方的配置黏贴到【全局扩展脚本】内，点击保存

```javascript
function main(content) {
  const isObject = (value) => {
    return value !== null && typeof value === 'object'
  }

  const mergeConfig = (existingConfig, newConfig) => {
    if (!isObject(existingConfig)) {
      existingConfig = {}
    }
    if (!isObject(newConfig)) {
      return existingConfig
    }
    return { ...existingConfig, ...newConfig }
  }

  const cnDnsList = [
    'https://223.5.5.5/dns-query',
    'https://223.6.6.6/dns-query',
  ]
  const trustDnsList = [
    'quic://dns.cooluc.com',
    'https://doh.apad.pro/dns-query',
    'https://1.0.0.1/dns-query',
  ]
  const notionDns = 'tls://dns.jerryw.cn'
  const notionUrls = [
    'http-inputs-notion.splunkcloud.com',
    '+.notion-static.com',
    '+.notion.com',
    '+.notion.new',
    '+.notion.site',
    '+.notion.so',
  ]
  const combinedUrls = notionUrls.join(',');
  const dnsOptions = {
    'enable': true,
    'prefer-h3': true, // 如果DNS服务器支持DoH3会优先使用h3
    'default-nameserver': cnDnsList, // 用于解析其他DNS服务器、和节点的域名, 必须为IP, 可为加密DNS。注意这个只用来解析节点和其他的dns，其他网络请求不归他管
    'nameserver': trustDnsList, // 其他网络请求都归他管
    
    // 这个用于覆盖上面的 nameserver
    'nameserver-policy': {
      [combinedUrls]: notionDns,
      'geosite:geolocation-!cn': trustDnsList,
      // 如果你有一些内网使用的DNS，应该定义在这里，多个域名用英文逗号分割
      // '+.公司域名.com, www.4399.com, +.baidu.com': '10.0.0.1'
    },
  }

  // GitHub加速前缀
  const githubPrefix = 'https://fastgh.lainbo.com/'

  // GEO数据GitHub资源原始下载地址
  const rawGeoxURLs = {
    geoip: 'https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/geoip-lite.dat',
    geosite: 'https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/geosite.dat',
    mmdb: 'https://github.com/MetaCubeX/meta-rules-dat/releases/download/latest/country-lite.mmdb',
  }

  // 生成带有加速前缀的GEO数据资源对象
  const accelURLs = Object.fromEntries(
    Object.entries(rawGeoxURLs).map(([key, githubUrl]) => [key, `${githubPrefix}${githubUrl}`]),
  )

  const otherOptions = {
    'unified-delay': true,
    'tcp-concurrent': true,
    'profile': {
      'store-selected': true,
      'store-fake-ip': true,
    },
    'sniffer': {
      enable: true,
      sniff: {
        TLS: {
          ports: [443, 8443],
        },
        HTTP: {
          'ports': [80, '8080-8880'],
          'override-destination': true,
        },
      },
    },
    'geodata-mode': true,
    'geox-url': accelURLs,
  }
  content.dns = mergeConfig(content.dns, dnsOptions)
  return { ...content, ...otherOptions }
}
```

启用后再次点击`重新激活订阅`按钮, 确保正确的应用了设置 (这里的任何代码变动, 都需要点击这个按钮手动刷新运行时的配置)

这段代码的作用是

* 使用阿里和DNSPod(腾讯的DNS)的`DoT`来解析节点、DNS服务器

- 使用无污染的DNS服务器解析其他网站

* 使用非营利组织的DoT解析Notion网站

- tun模式堆栈使用自适应模式

* 更换延迟计算方式,去除握手等额外延迟

- 开启TCP并发的支持

* 开启域名嗅探, 准确还原域名, 进行域名分流

- 设置geodata的下载源为国内加速下载源

如果你完全按照上面的步骤设置好了，再看看[DNS Leak Test](https://browserleaks.com/dns) 、[ipleak](https://ipleak.net/) ，你会发现大部分的解析结果都是来自国外的Cloudflare和Google的DNS, 这是节点服务器不管拿到了你传过去的真ip还是假ip地址, 他都会再去请求一次Cloudflare/Google的DNS服务, 确保解析的正确性。但是重要的是没有中国大陆的DNS服务器了，如果还是有，那你应该往当前设备的更上层寻找问题所在，比如路由器的设置等。

## **解决GEOIP, CN问题**

目前市面上绝大多数的代理工具都依赖于 GeoIP2 数据库判断地址所属地。它们的规则结尾部分一般都会有一条类似 `GEOIP, CN`，用来查询目的 IP 地址是否属于中国大陆，从而判断是否直连。

这些代理工具通常使用的 GeoIP2 数据库是来自于 MaxMind 的 [GeoLite2](https://dev.maxmind.com/geoip/geoip2/geolite2/) 免费数据库。这个数据库目前存在一下几个问题：

* 获取不便：从 2019 年 12 月 30 日起，必须注册后才能下载

- 数据量大：数据库庞大，包含全球的 IP 地址段，约 10 MB

* 准确度低：对中国大陆的 IP 地址判定不准，如：香港阿里云的 IP 被判定为新加坡、中国大陆等。

庞大的数据量对于大多数中国大陆的用户来说是没有意义的，因为只仅需要去判断 IP 的地理位置是否属于中国大陆境内，其他国家的 IP 一律代理/直连。过多的数据量会增加载入时间，降低查询效率。

我们在之前创建的Script中已经包含了下载更精简合适中国大陆的IP数据库链接, 现在只需要手动操作下载和替换即可。

1. 点击Clash Verge Rev的设置菜单, 找到「更新GeoData」, 点击进行更新, 他会在后台进行下载和本地的文件替换, 通常在10秒内完成。

2) 验证是否下载完成: 右键托盘中的Clash Verge图标，【打开目录】-【应用目录】, 找到geoip.dat文件, 查看其文件体积, 如果是几百KB则成功, 如果是好几MB则未成功或未下载完成(几百KB下载要不了多久, 太久没有效果可能需要你使用下方的操作去重启Clash客户端重试)。

3. 下载完成后右键托盘中的Clash Verge图标，【更多】-【重启应用】确保数据库被正确应用

## **我希望xxx.com不要走代理, 如何做?**

注：此处为操作更简单的【界面化操作方式】，你也可进入Clash verge rev 官网选择【脚本配置化方式】进行使用\
\
【右键订阅配置】-> 【点击编辑规则】-> 【按照下方说明填写规则】 -> 【关闭重新开启TUN模式开关】

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-ovwhwjnc.png?x-oss-process=style/bf)

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-cprlnzmf.png?x-oss-process=style/bf)

![](https://photo0919.oss-cn-hangzhou.aliyuncs.com/img/2024-11-18-dpmfrzos.png?x-oss-process=style/bf)

- - -

至此，就完成了我认为的Clash的最佳实践配置。

远程配置的维护我会持续进行，希望文章的内容能对你有所帮助。

本文转载于：https://lainbo.com/article/clash-config

仅作为备份查看，更多内容请查看原作者博客。

