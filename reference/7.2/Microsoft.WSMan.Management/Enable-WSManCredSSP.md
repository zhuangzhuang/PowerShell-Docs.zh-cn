---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: bacafee683fa47d7be331b4e44d2ab75be5bdb23
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597264"
---
# Enable-WSManCredSSP

## 摘要
在计算机上启用凭据安全支持提供程序 (CredSSP) 身份验证。

## SYNTAX

### 全部

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## DESCRIPTION

`Enable-WSManCredSSP`Cmdlet 可在客户端或服务器计算机上启用 CredSSP 身份验证。
当使用 CredSSP 身份验证时，用户凭据将传递给要进行身份验证的远程计算机。 此类型的身份验证旨在用于从一个远程会话创建另一个远程会话的命令。 例如，若要在远程计算机上运行后台作业，可以使用此类型的身份验证。

`Enable-WSManCredSSP` 可以在 **客户端** 或 **服务器** 上启用 CredSSP。 若要在客户端上启用 CredSSP，请在 **Role** 参数中指定 **client** 。 客户端在实现服务器身份验证时将显式凭据委派给服务器。 若要在服务器上启用 CredSSP，请在 **Role** 参数中指定 **server** 。 服务器充当客户端的代理。 有关更多详细信息，请参阅参数部分中的 **Role** 。

> [!CAUTION]
> CredSSP 身份验证将用户凭据从本地计算机委派给远程计算机。 此做法增加了远程操作的安全风险。 如果远程计算机的安全受到威胁，则在向该计算机传递凭据时，可使用这些凭据来控制网络会话。

## 示例

### 示例 1：委派客户端凭据

此示例允许使用完全限定的域名将客户端凭据委派给计算机。

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 示例 2：将客户端凭据委派给域中的所有计算机

此示例允许将客户端凭据委派给 **fabrikam.com** 域中的所有计算机。 星号 (`*`) 通配符指定所有计算机。

> [!NOTE]
> 使用带有 **DelegateComputer** 参数的通配符可在超过所需的计算机上启用 CredSSP。

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### 示例 3：将客户端凭据委派给多台计算机

此示例允许将客户端凭据委派给多台计算机。

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

`$servers`变量包含服务器名称的列表。 `Enable-WSManCredSSP` 使用 **Role** 参数指定 **客户端** 角色。 **DelegateComputer** 从变量获取计算机名称 `$servers` 。

### 示例 4：允许计算机充当代理

此示例允许计算机充当另一台计算机的委托。 `Enable-WSManCredSSP`前面的示例中所示的 cmdlet 仅在客户端上启用 CredSSP 身份验证，并指定可代表其执行操作的远程计算机。 为了使远程计算机充当客户端的代理，WSMan 的 **Service** 节点中的 CredSSP 项必须设置为 true。 此示例将 WSMan 的 **Service** 节点中的 CredSSP 项设置为 true。

```powershell
Enable-WSManCredSSP -Role "Server"
```

### 示例 5：允许计算机通过使用 Set-Item 充当代理

此示例允许一台计算机充当另一台计算机的代理。 `Enable-WSManCredSSP`前面的示例中所示的命令仅在客户端计算机上启用 CredSSP 身份验证，并指定可代表客户端计算机执行的远程计算机。 若要使远程计算机充当客户端计算机的代理，WSMan 提供程序的 Service 目录中的 CredSSP 项必须设置为 true。

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` 创建与远程计算机的连接 server02。 `Set-Item` 使用 **Path** 参数指定 **WSMan** 提供程序的位置。 **Value** 参数将 **服务** 设置设置为 true。

## PARAMETERS

### -DelegateComputer

指定要向其委派客户端凭据的服务器。 最佳做法是使用完全限定的域名。

允许使用通配符，但可以在需要的计算机上启用 CredSSP。

如果 **Role** 参数为 **Client**，则必须指定此参数。 如果 **Role** 是 **Server**，请不要指定此参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

强制运行命令而不要求用户确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Role

指定将 CredSSP 启用为客户端还是服务器。 此参数的可接受值为： **Client** 和 **Server**。

如果指定 " **客户端**"，则会执行以下操作。 这些设置允许客户端在实现服务器身份验证时将显式凭据委派给服务器。

- 启用客户端上的 CredSSP。
- 将 WS-Management 设置设置 `\<localhost|computername\>\Client\Auth\CredSSP` 为 true。
- 将 Windows CredSSP 策略 **AllowFreshCredentials** 设置为客户端上的 **WSMan/Delegate** 。

如果指定 **服务器**，则执行以下操作。 此策略设置允许服务器充当客户端的代理。

- 启用服务器上的 CredSSP。
- 将 WS-Management 设置设置 `\<localhost|computername\>\Service\Auth\CredSSP` 为 true。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

此 cmdlet 不接受任何输入。

## 输出

### System.Xml.XmlElement

如果成功启用 CredSSP 身份验证，此 cmdlet 将生成一个 **XMLElement** 对象。

## 注释

若要禁用 CredSSP 身份验证，请使用 `Disable-WSManCredSSP` cmdlet。

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Disconnect-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

