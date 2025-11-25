---
title: EdgeOne 变成如今的样子，这为什么？我们又该怎么办？
cover: "/images/post/why-has-edgeone-become-the-way-it-is-today/cover-edgeone.png"
tags: [EdgeOne,EO,CDN,PaaS]
categories: [EdgeOne]
date: 2025-08-07
description: 在2025年因其兑换码（测速、了解边缘函数）获取免费套餐一度在中国火的一塌糊涂……
articleGPT: 2025年腾讯云EdgeOne免费套餐因被严重滥用（刷TB流量、搭建机场）导致官方持续收紧直至“玩坏”，作者痛陈经过并呼吁停止作死、有能力就付费，共同守护社区资源。
references:
  - title: 【已出新ip】关于近期EdgeOne CDN 优选方面出现的相关问题
    url: https://linux.do/t/topic/1092386
  - title: 腾讯一贯的风格，edgeone貌似不行了
    url: https://linux.do/t/topic/763579
  - title: 最近Edgeone能别用优选的尽量别用优选了 - #4，来自 SDCOM
    url: https://linux.do/t/topic/771543/4
  - title: 常见问题解答 - LINUX DO
    url: https://linux.do/faq
  - title: EdgeOne免费计划：支持初创企业，加速技术实现 - Tencent EdgeOne
    url: https://edgeone.ai/zh/document/70405?product=pricing
  - title: 免费CDN时代结束：奇安信网站卫士关闭 - 哔哩哔哩
    url: https://www.bilibili.com/opus/925948211196067856
  - title: 急报！EO优选失效！ - 青序栈
    url: https://qxzhan.cn/post/fweo.php
---
## [EdgeOne](https://edgeone.ai) —— 腾讯云推出的一款边缘安全加速平台
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在2025年因其兑换码（测速、了解边缘函数）获取**免费套餐**一度在中国火的一塌糊涂……

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;不难看出EdgeOne（以下统称EO）推出这个活动的目的——引流，这是一个再正常不过的行为，通过打折、免费吸引用户然后借此推销，然而这也**吸引**来了一部分**滥用群体**！

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;据笔者所知的是，有部分人优选后并不是拿来正常加速网页，而是用于大流量下载服务，用掉几百G甚至几TB，违背了[官方意愿](https://edgeone.ai/zh/document/70405?product=pricing)；更有甚者EO在单线程限速的情况下，还有人将其用做VPN！（考虑到隐私问题，不公开是谁）

~~插一嘴，都限速500kb了还能搭VPN用啊？不嫌卡吗？~~ 

![](/images/post/why-has-edgeone-become-the-way-it-is-today/9e57ef19fe7d5556ec5a8af504a95afe77d67d6b.png)

EO官方一开始其实够放宽松了，**只是限制了单线程速度**；EO刚出那会和CloudFlare一样——免费节点与付费节点共用，是可以将`www.tencentcloud.com`用作优选域名的。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;笔者非常**理解**为什么要去优选，无非就是想让自己网站的加载速度在快一些嘛。所以笔者也搞过EO优选域名（byoip.top）供大家使用，如果优选仅仅只是用于网站加速的话，EO是睁只眼闭只眼的态度的（前提是网站没被打）。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;后面，随着EO使用人数的增多，滥用的人也越来越多，**EO开始逐步加大限制**：
- **第一次**：区分免费节点与付费节点，强行使用报`418`
- **第二次**：部分EO中国香港的节点不给中国大陆提供服务（不是墙了，就是不对中国大陆提供服务）
- **第三次**：更多节点对中国大陆访客报`403`（到这里，旧域名还是**可以**使用香港优化节点的）
**再次加大力度**：下线部分IP（笔者已知的：43.174.242.0/22），旧域名也**无法**使用香港优化节点了……

::: details 点我查看Itdog截图
![](/images/post/why-has-edgeone-become-the-way-it-is-today/itdog.png)
::: 

### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;再这期间，还发生过一件可大可小的事情；却让我看清了一些人的“嘴脸”。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;此事为EO于**2025年10月15日**，通过短信、邮箱、站内信等方式，告知用户“对免费套餐用户下线源站防护功能”

::: details 点我查看截图
> ### 以下为举例，没有放全部出来
>![](/images/post/why-has-edgeone-become-the-way-it-is-today/a1141a141c3aff143c0e36df2fc2c559b47a3a86.png)

![](/images/post/why-has-edgeone-become-the-way-it-is-today/fuck-eo-1.png)
![](/images/post/why-has-edgeone-become-the-way-it-is-today/fuck-eo-2.png)
![](/images/post/why-has-edgeone-become-the-way-it-is-today/fuck-eo-3.png)
:::
> 笔者当时是骂了他们中的两个人，在这里我对其表示歉意……当时确实是被气到了。

**以上为真实聊天记录截图，绝无弄虚作假**  ~~我也不会伪造（~~ 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;甚至没有了解清楚“源站保护”到底是个什么东西，就直接开始骂EO；当然，有**不理性**的群U，也不乏有**理性**的群U （\*＾-＾\*）

::: details 点我查看聊天记录截图
![](/images/post/why-has-edgeone-become-the-way-it-is-today/good-eo-1.png)
![](/images/post/why-has-edgeone-become-the-way-it-is-today/good-eo-2.png)
![](/images/post/why-has-edgeone-become-the-way-it-is-today/good-eo-3.png)
![](/images/post/why-has-edgeone-become-the-way-it-is-today/good-eo-4.png)
:::

## 那我们该怎么办？
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;如果你现在还在使用EO搭建机场、跑大流量下载等服务的……停下吧。我们不能在这样下去了！不要让CloudFlare、Fastly、ESA等成为下一个**奇安信360**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在这里我也呼吁，有能力的还是尽量付费；把免费的资源让出来给那些有刚需的群U。

### 真诚、友善、团结、专业，共建你我引以为荣的 ~~&nbsp;&nbsp;社区&nbsp;&nbsp;~~ Internet。

----
全文完……<br>
~~轻点喷，梦到什么写什么的（~~ ，也请读者不要谩骂上面提到的“反面人物”，谁都有犯错的时候~