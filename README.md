# SSR机场搭建教程 科学上网不是问题

讲解下怎样使用Linux VPS搭建SSR和BBR加速，并提供Windows/IOS/MAC/Android的SSR客户端实现油管等外网访问，希望可以帮助到使用Linux VPS搭建SSR实现外网访问的朋友。

Linux VPS搭建SSR步骤概览
要实现Linux VPS搭建SSR主要需要实现以下步骤：

1. 购买Linux VPS
1. 远程连接Linux VPS 搭建SSR
1. 下载SSR的对应的客户端，配置SSR
1. 搭建BBR加速，使网络更快

下面我就分步骤讲解下Linux VPS搭建SSR的流程。

## 购买Linux VPS

首先确认不要使用任何其他的上网工具，网络是什么IP就是什么IP，不然可能需要人工审核，导致Hostwinds VPS 购买显示 "Pending" 状态， 不能即时创建服务激活。

1、通过Hostwinds 优惠链接进入Hostwinds 首页，选择“VPS”下的"Linux Managed"，这里是最便宜的(注意千万不要选择页面上Get Hosted那个，那个是虚拟空间，不是VPS!!!)。Managed VPS要比Unmanaged VPS快很多，也更稳定。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Home-Page-1.jpg)

2、进入VPS选择页面后，根据自己的需要的配置选择套餐，一般我们选择最低配置就够用了，Managed比Unmanaged速度更快，更稳定，建议选择“Managed”，当然你觉得价格贵，不用速度快的，可以选择“UnManaged”，然后点击“Order”按钮进入信息填写页面（一般选择最低配置就可以了），如下所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Plan-Select-2.jpg)

3、进入信息填写页面后首先填写账号信息，一般是新用户我们填写左边的姓、名、邮箱、密码，然后点击“Submit”进入下一步，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Account-Information.jpg)

4、页面跳转后填写用户信息，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Client-Information.jpg)

5、然后选择购买时间、数据中心 、操作系统，红色部分需要自己选择，绿色一般我们默认，可以按月购买，但是建议第一次购买时间选择长一点，这样优惠要大很多，不然后面续费优惠力度就没有这么大了。 如下图所示（根据你选择的Managed和Unmanaged价格有所不同，其他按照下面的选择就可以了）：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Package-Information-new.jpg)

6、默认是自动云备份的，如果不需要去掉勾选， 如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Services-Select.jpg)

7、然后选择付款方式，一般我们选择支付宝进行付款 （只有国内IP访问的时候才有支付宝付款方式），如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Account-Payment-Information.jpg)

8、最后确认价格（不同时期可能价格有些许不同，如果通过前面优惠链接点击购买会有优惠），勾选同意协议，然后点击“Complete Order”按钮进行下单， 如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Order-Confirm-new-1.jpg)

9、下单完成后订单结果如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-07-25/Hostwinds-Order-Result.png)
