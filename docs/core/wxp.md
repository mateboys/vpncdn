> 注意
> Windows平台下请选择L2TP/IPSec连接方式


## 连接步骤

```
1.单击“开始”菜单并转到“控制面板”。

2.转到网络和 Internet部分。

3.单击网络和共享中心。

4.单击设置新连接或网络。

5.选择连接到工作场所，然后单击下一步。

6.单击使用我的 Internet 连接 (VPN)。

7.在输入VPN服务器IP地址。

8.在目的地名称字段中输入您喜欢的任何内容。

9.勾选现在不连接；只需设置它，以便我可以稍后连接复选框。

10.单击下一步。

11.在用户名字段中输入用户名。

12.在密码字段中输入密码。

13.选中记住此密码复选框。

14.单击“创建”，然后单击“关闭”。

15.返回网络和共享中心。在左侧，单击更改适配器设置。

16.右键单击新的 VPN 条目并选择Properties。

17.单击选项选项卡并取消选中包括 Windows 登录域。

18.单击安全选项卡。为 VPN 类型选择“带 IPsec 的第 2 层隧道协议 (L2TP/IPSec)” 。

19.单击允许这些协议。选中“挑战握手身份验证协议 (CHAP)”和“Microsoft CHAP 版本 2 (MS-CHAP v2)”复选框。

20.单击高级设置按钮。

21.选择使用预共享密钥进行验证，并输入密钥(PSK)。

22.单击确定关闭高级设置。

23.单击确定以保存 VPN 连接详细信息。

24.连接。

```

> 注意
> Windows平台下如果 VPN 服务器或客户端在 NAT 之后（例如家庭路由器），则需要此一次性注册表更改。

-------------------------------------------------------------------------------
## Windows修改注册表

| 错误  809  | 无法在您的计算机和 VPN 服务器之间建立网络连接，因为远程服务器没有响应。这可能是因为您的计算机和远程服务器之间的网络设备之一（例如，防火墙、NAT、路由器等）未配置为允许 VPN 连接。请联系您的管理员或您的服务提供商以确定可能导致问题的设备。                                                        |
|-----------|---------------------------------------------------------------|

>注意
>当出现错误809时，需要对windows进行修改注册表才能正确连接VPN

>仅当您使用 IPsec/L2TP 模式连接到 VPN 时，才需要更改以下注册表。IKEv2和IPsec/XAuth模式不需要它。


要修复此错误，需要一次性更改注册表，因为 VPN 服务器和/或客户端位于 NAT 之后（例如家庭路由器）。下载并运行下面的`.reg`文件(注册表修复器)并重启后即可解决，或者我们也可以使用管理员身份通过cmd或PowerShell命令行运行以下命令即可完成，效果与注册表修复器一致。完成后，您必须重新启动 PC。

<br>


- 适用于 Windows Vista、7、8.x 和 10的注册表修复器或代码：[（注册表修复器）](http://cdn.usfom.com/software/Fix_VPN_Error_809_Windows_Vista_7_8_10_Reboot_Required.reg)

```java
REG ADD HKLM\SYSTEM\CurrentControlSet\Services\PolicyAgent /v AssumeUDPEncapsulationContextOnSendRule /t REG_DWORD /d 0x2 /f
```

<br>


- 仅适用于 Windows XP的注册表修复器或代码：[（注册表修复器）](https://cdn.usfom.com/software/Fix_VPN_Error_809_Windows_XP_ONLY_Reboot_Required.reg)

```java
REG ADD HKLM\SYSTEM\CurrentControlSet\Services\IPSec /v AssumeUDPEncapsulationContextOnSendRule /t REG_DWORD /d 0x2 /f
```


> 注意
> Windows平台下请选择L2TP/IPSec连接方式
