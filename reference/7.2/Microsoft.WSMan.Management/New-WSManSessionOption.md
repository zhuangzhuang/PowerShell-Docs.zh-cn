---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: e7d7f132eb82dc1a709a88cbdef525aa83d867e4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603391"
---
# New-WSManSessionOption

## 摘要
创建要用作 WS-Management cmdlet 的输入参数的会话选项哈希表。

## SYNTAX

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## DESCRIPTION
**New-wsmansessionoption** cmdlet 创建可传递到 wsman Cmdlet 的 WSMan 会话选项哈希表：

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## 示例

### 示例1：创建使用连接选项的连接

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

此示例使用由 **new-wsmansessionoption** 定义的连接选项创建与远程 server01 计算机的连接。

第一个命令使用 **new-wsmansessionoption** 将一组连接设置选项存储在 $a 变量中。
在此情况下，这些会话选项将连接超时设置为 30 秒（30,000 毫秒）。

第二个命令使用 *SessionOption* 参数将存储在 $a 变量中的凭据传递到 **连接-WSMan**。
然后，使用指定的会话选项 **连接-WSMan** 连接到远程 server01 计算机。

**连接-wsman** 通常用于 wsman 提供程序的上下文中，用于连接到远程计算机（在本例中为 server01 计算机）。
但是，你可以在更改为 WSMan 提供程序之前，使用该 cmdlet 建立与远程计算机的连接。
这些连接将出现在 **ComputerName** 列表中。

## PARAMETERS

### -NoEncryption
指示连接不将加密用于通过 HTTP 进行的远程操作。

默认情况下，不会启用未加密的流量。
它必须在本地配置中启用。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout
指定 WS-Management 操作的超时时间（以毫秒为单位）。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType
指定代理服务器定位所依据的机制。
此参数的可接受值为：

- ProxyIEConfig.
为当前用户使用 Internet Explorer 代理配置。
- ProxyWinHttpConfig.
WSMan 客户端使用 ProxyCfg.exe 实用程序为 WinHTTP 配置的代理设置。
- ProxyAutoDetect.
强制自动检测代理服务器。
- ProxyNoProxyServer.
“不使用代理服务器”。
在本地解析所有主机名。

默认值为 ProxyIEConfig。

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
指定要在代理中使用的身份验证方法。
此参数的可接受值为：

- 基本。
Basic 是一种将用户名和密码以明文形式发送到服务器或代理的方案。
- 摘要。
Digest 是一种质询响应方案，该方案将服务器指定的数据字符串用于质询。
- Negotiate。
Negotiate 是一种质询响应方案，该方案与服务器或代理协商以确定要用于身份验证的方案。
例如，Kerberos 协议和 NTLM。

默认值为 "协商"。

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
指定有权通过中间 Web 代理获得访问权限的用户帐户。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck
指定当通过 HTTPS 进行连接时，客户端不会验证服务器证书是否由受信任的证书颁发机构签名 (CA) 。
仅当远程计算机受另一种方法的信任时（例如，如果远程计算机是物理安全和隔离的网络的一部分，或者远程计算机在 WS-Management 配置中列为受信任主机），则使用此选项。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCNCheck
指定服务器的证书公用名 (CN) 不必与服务器的主机名匹配。
这仅用于使用 HTTPS 的远程操作。
此选项应仅用于受信任的计算机。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipRevocationCheck
指示连接不验证服务器证书上的吊销状态。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SPNPort
指定要追加到远程服务器的连接服务主体名称 (SPN) 的端口号。
当身份验证机制是 Kerberos 或 Negotiate 时，使用 SPN。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16
指示连接以 UTF16 格式而不是 UTF8 格式对请求进行编码。
默认值为 UTF8 编码。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

## 输出

### SessionOption

## 注释

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

