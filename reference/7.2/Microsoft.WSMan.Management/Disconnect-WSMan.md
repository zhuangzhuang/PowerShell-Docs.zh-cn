---
external help file: Microsoft.WSMan.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disconnect-wsman?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-WSMan
ms.openlocfilehash: 948b870948f51bd51424beaeca45ed2b2d195891
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596435"
---
# Disconnect-WSMan

## 摘要
断开客户端与远程计算机上的 WinRM 服务的连接。

## SYNTAX

```
Disconnect-WSMan [[-ComputerName] <String>] [<CommonParameters>]
```

## DESCRIPTION
**断开连接-WSMan** cmdlet 会断开客户端与远程计算机上的 WinRM 服务的连接。
如果将 WS-Management 会话保存在变量中，则会话对象将保留在该变量中，但 WS-Management 会话的状态将会关闭。
你可以在 WSMan 提供程序的上下文中使用此 cmdlet 来断开客户端与远程计算机上的 WinRM 服务的连接。
但是，你还可以在更改为 WSMan 提供程序之前，使用此 cmdlet 断开与远程计算机上的 WinRM 服务的连接。

有关如何连接到远程计算机上的 WinRM 服务的详细信息，请参阅 Connect-WSMan。

## 示例

### 示例1：删除与远程计算机的连接

```
PS C:\> Disconnect-WSMan -computer server01
PS C:\> cd WSMan:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
```

此命令删除与名为 server01 的远程计算机的连接。

通常在 WSMan 提供程序的上下文中，使用此 cmdlet 断开与远程计算机（在本例中为 server01 计算机）的连接。
但是，你还可以在更改为 WSMan 提供程序之前，使用 **Disconnect-WSMan** 删除与远程计算机的连接。
这些连接不会显示在 ComputerName 列表中。

## PARAMETERS

### -ComputerName
指定要对其运行管理操作的计算机。
该值可以是完全限定的域名、NetBIOS 名称或 IP 地址。
使用本地计算机名称、localhost 或点 (.) 指定本地计算机。
默认值为本地计算机。
当远程计算机与用户位于不同的域时，必须使用完全限定的域名。
可以通过管道将此参数的值传递给 cmdle。

不能从本地主机断开连接。
也就是说，不能断开与本地计算机的默认连接。
但是，如果您创建了与本地计算机的单独连接，例如，使用计算机名称。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
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

### 无
此 cmdlet 将不生成任何输出。

## 注释

## 相关链接

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

