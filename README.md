# SSR机场搭建教程 科学上网不是问题

讲解下怎样使用Linux VPS搭建SSR和BBR加速，并提供Windows/IOS/MAC/Android的SSR客户端实现油管等外网访问，希望可以帮助到使用Linux VPS搭建SSR实现外网访问的朋友。

Linux VPS搭建SSR步骤概览
要实现Linux VPS搭建SSR主要需要实现以下步骤：

1. 购买Linux VPS
1. 远程连接Linux VPS 搭建SSR
1. 下载SSR的对应的客户端，配置SSR
1. 搭建BBR加速，使网络更快

下面我就分步骤讲解下Linux VPS搭建SSR的流程。

## 1、购买Linux VPS

首先确认不要使用任何其他的上网工具，网络是什么IP就是什么IP，不然可能需要人工审核，导致Hostwinds VPS 购买显示 "Pending" 状态， 不能即时创建服务激活。

1、通过 [Hostwinds 优惠链接](https://www.hostwinds.com/3704.html) 进入Hostwinds 首页，选择“VPS”下的"Linux Managed"，这里是最便宜的(注意千万不要选择页面上Get Hosted那个，那个是虚拟空间，不是VPS!!!)。Managed VPS要比Unmanaged VPS快很多，也更稳定。

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

10. 后面支付宝付款的时候选择创建协议就可以了，如下所示：
![](https://zhidao91.oss-cn-shanghai.aliyuncs.com/Content/2020/hostwinds/p9.jpg)

## 2、Hostwinds VPS连接账号信息获取
在Hostwinds购买付款完成后，你就应该得到VPS连接的IP、用户名（Linux VPS用户名默认都是root）、密码。这个VPS连接信息你可以有两个途径获得：1、邮件发送；2、Hostwinds后台管理也是可以的。

如果注册的时候填写的邮箱是正确的，那么你就会收到类似下面这个图这样的邮件：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/1.jpg)

邮件上你可以知道IP、用户名和密码，这三个要素就是你连接VPS的信息，缺一不可。

另外如果你在邮件那里没有看到用户信息，那么在Hostwinds的后台也是有的。下面说说在管理后台怎么查看VPS账号信息。

访问[Hostwinds用户中心](https://clients.hostwinds.com/clientarea.php) ，如果你没有登录，那么就填写注册时候的邮箱和密码进行登录，就是你下单注册的时候填写的那个邮箱和密码。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/2.jpg)

登录进入后就可以看到你的VPS服务列表界面，点击你的VPS，如下所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/3.jpg)
 
然后再点击“Click Here to Manage This Server”的绿色按钮进入具体的管理界面：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/4.jpg)
进入管理页面后，就是如下所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/5.jpg)
在管理界面你可以看到当前管理这台VPS的IP、点击"View Password"按钮就可以看到密码了，如上图标记所示。而Linux VPS的用户名默认都是“root”，所以这里没有显示出来。

所以不管是通过哪种方法，你都可以得到你的VPS的IP、账号（root）、密码，有了它，下面就可以讲解怎么进行连接了。

## 3、连接Hostwinds VPS

有了上面的账号信息，我们就可以进行进行连接了。连接Linux VPS是需要连接工具的，市场上有很多，比如Xshell、Putty等。这里我推荐使用Xshell，因为它有复制、粘贴功能，操作方便一点。

Xshell你可以搜索到官网下载或者其他网友的分享，我这里白百度网盘也搞了个备份，

Xshell下载地址：https://pan.baidu.com/s/1wmuNI5SPws10vWCacMvY1w，提取码: tppw

如果你是苹果Mac电脑使用工具稍微有点不同，可以百度搜索“Mac SSH客户端SecureCRT安装破解”，不过后面讲的连接方法基本是差不多的。

把Xshell软件下载下来后解压安装好。

下面说说具体使用Xshell连接Linux VPS的图文方法。

1、打开Xshell，点击左上角“文件”-“新建”，打开连接弹出库。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-12-11/xshell-connect-linux-vps.jpg)

2、在Xshell弹出框中输入IP和端口，端口一般是22默认，然后点击确认按钮，如下图所示

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-12-11/xshell-connect-linux-vps-1.jpg)

3、然后输入用户名root，勾选记住用户名。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-12-11/xshell-connect-linux-vps-2.jpg)

4、然后输入密码，勾选记住密码，点击确定。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-12-11/xshell-connect-linux-vps-3.jpg)

完成以上步骤后就可以看到连接成功的界面，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2018-12-11/xshell-connect-linux-vps-4.jpg)

很多朋友连接的时候可能出现一句“WARNING! The remote SSH server rejected X11 forwarding request.”这样的警告信息（如下图所示），这个也是正常的，不用管它。

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/2-2021/2021-9-2/6.jpg)

所以通过上面的方法正常情况下就可以连接Hostwinds的VPS了。

PS：如果你没有连上，而是显示“显示SSH服务器拒绝了密码”错误，那么就可能是默认的密码不对，你就重置下密码就可以了，后面会介绍重置的方法。

## 密码不对导致Hostwinds VPS连接不上

如不不存在这样的情况这个步骤可以直接跳过

如果只是密码不对，显示SSH服务器拒绝了密码，如下图使用Xshell连接的显示示意图：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-7/cannot-connect-hostwinds-vps-wrong-password.jpg)

Hostwinds 采用KVM，因此生成Linux VPS的密码的自动生成的，而Hostwinds发送的邮件中的密码可能不是VPS真实的密码，这时不知道密码是多少我们可以登录后台重新设置密码。

进入前面介绍的Hostwinds后台VPS管理界面，然后点击修改密码按钮，在弹出框中重新输入密码，密码需要字母大小写、特殊符还有要一定长度：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-7/cannot-connect-hostwinds-vps-wrong-password-step3.jpg)

PS：修改后密码还没有生效，最关键的一步需要 重启服务器，才能生效，如下图所示点击重启：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-7/cannot-connect-hostwinds-vps-wrong-password-step4.jpg)

稍等几分钟等VPS重启好后，就能够使用你就可以使用你设置的密码登录 Hostwinds VPS了。

## 安装SSR

通过上面的教程连接到Linux VPS后，我们需要通过命令开始进行SSR的搭建。

粘贴下面的命令（复制下面的命令，然后在Xshell待输入内容处“鼠标右键”/“粘贴”即可）：

yum -y install wget

wget -N —no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh
chmod +x ssr.sh
bash ssr.sh

粘贴后会下载相关安装包，等待屏幕不动的时候按“回车键”，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-input.jpg)

然后等待一会儿，出现SSR安装的引导界面，输入数字1，按回车键进行SSR安装，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step1.jpg)

然后输入端口，尽量选择一个比较大的数字，避免端口冲突，建议选择8099，经验证8080、8090端口是被封了的，千万不要用这个（如果后面遇到可以登录VPS，但是ssr上不了网，可能就是端口封了，修改一下ssr端口就可以了）， 然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step2.jpg)

然后输入SSR账号的密码，随便输入一个密码，这里输入123qweasd，然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step3.jpg)

然后输入SSR账号的加密方式，随便输入10，选择aes-256-cfb的加密方式，然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step4.jpg)

然后输入SSR账号的协议插件，随便输入2，选择auth_sha1_v4的协议插件，然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step5.jpg)

然后选择是否设置协议插件兼容原版，随便输入y，表示要设置，然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step6.jpg)

然后选择混淆插件，这里选择1，然后回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step7.jpg)

然后设置限制的设备数，如果要限制就输入对于的数字，如果不限制就直接回车，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step8.jpg)

然后设置每个端口的速度，如果要限制就输入对于的数字，单位是KB/S，如果不限制就直接回车，建议不限制速度，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step9.jpg)

然后设置总的速度，如果要限制就输入对于的数字，单位是KB/S，如果不限制就直接回车，建议不限制速度，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step10.jpg)

然后会开始部署，到下图所示的位置，提示你下载文件，输入：y

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step10-1.jpg)

然后就耐心等待一会儿安装，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-commend-step11.jpg)

等安装完成之后就可以看到 SSR账号 配置信息，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/linux-vps-ssr-success-result.jpg)

按照上面的图片就可以看到设置的SSR账号信息，包括IP、端口、密码、加密方式、协议插件、混淆插件，这些信息都需要填入对应的SSR客户端。

到此已经完成SSR的服务器搭建，现在只需要一个SSR客户端就可以实现外网访问了，下面我们讲解各种客户端的连接方式。

这里只是完成SSR搭建，注意要安装后面的BBR加速看YouTube速度才会飞上去。

## 安装BBR加速

## 注意要装加速才能最快！！！

## 注意要装加速才能最快！！！

## 注意要装加速才能最快！！！

BBR是Google的一款SSR加速产品，使用下面的命令就可以实现BBR加速，只有Hostwinds等少数KVM VPS才支持BBR加速，这也是我们推荐选择Hostwinds的原因。

在xShell连接端输入，如下命令，然后回车：

yum -y install wget
wget –no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-excute.jpg)

然后按任意键进行部署

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-excute-confirm.jpg)

然后需要等待命令执行，大约5分钟，如下图所示：

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-excute-confirmed.jpg)

会在下面的图片过程中等待一会儿

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-excute-confirmed1.jpg)

最后完成后需要重启，根据提示输入：y，重启服务器即可生效

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-reboot.jpg)

如果错过了重启步骤，直接输入重启命令命令：

reboot

![](https://vps234.oss-cn-shanghai.aliyuncs.com/Content/1-2019/2019-1-6/ssr-bbr-setup-reboot-manual.jpg)

然后耐心等待，待服务器重启后即可自动开启SSR加速。(这里注意如果是centos 7系统重启后可能防火墙阻止了SSR，需要关闭防火墙，如果是centos 6就不会有这个问题，所以我们建议使用的是Hostwinds的centos 6操作系统。)

重新打开YouTube(油管)或者Google其他网站试一下，速度会快很多。
