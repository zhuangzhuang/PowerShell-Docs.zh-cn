---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: aa83b6318b8e3b07d17cbb3e511bc7ab4aa9a774
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598855"
---
# Get-PSDrive

## 摘要
获取当前会话中的驱动器。

## SYNTAX

### Name（默认值）

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### LiteralName

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## DESCRIPTION

`Get-PSDrive`Cmdlet 将获取当前会话中的驱动器。 可以获取会话中的特定驱动器或所有驱动器。

此 cmdlet 将获取以下类型的驱动器：

- 计算机上的 Windows 逻辑驱动器，包括映射到网络共享的驱动器。
- PowerShell 提供程序公开的驱动器 (如证书：、Function：和 Alias：驱动器) 以及由 Windows PowerShell Registry 提供程序公开的 HKLM：和 HKCU：驱动器。
- 通过使用 cmdlet 创建的会话指定的临时驱动器和永久的映射网络驱动器。

从 Windows PowerShell 3.0 开始，cmdlet 的 **持久** 参数 `New-PSDrive` 可以创建在本地计算机上保存并可用于其他会话的映射网络驱动器。 有关详细信息，请参阅 New-PSDrive。

此外，从 Windows PowerShell 3.0 开始，当外部驱动器连接到计算机时，Windows PowerShell 自动将 PSDrive 添加到代表新驱动器的文件系统中。
你无需重启 Windows PowerShell。 简单来说，当从计算机断开连接外部驱动器时，Windows PowerShell 会自动删除代表删除的驱动器的 PSDrive。

## 示例

### 示例1：获取当前会话中的驱动器

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

此命令获取当前会话中的驱动器。

输出显示硬盘驱动器 (C： ) 、CD-ROM 驱动器 (D： ) ，以及由 Windows PowerShell 提供程序公开的驱动器 (Alias：、Cert：、Env：、Function：、HKCU：、HKLM：和 Variable： ) 。

### 示例2：获取计算机上的驱动器

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

此命令获取计算机上的 D: 驱动器。 请注意，该命令中的驱动器号后面不带冒号。

### 示例3：获取 Windows PowerShell 文件系统提供程序支持的所有驱动器

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

此命令获取 Windows PowerShell FileSystem 提供程序支持的所有驱动器。 这包括固定驱动器、逻辑分区、映射网络驱动器和使用 New-PSDrive cmdlet 创建的临时驱动器。

### 示例4：检查驱动器是否正在用作 Windows PowerShell 驱动器名称

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

此命令检查 X 驱动器是否已作为 Windows PowerShell 驱动器名称使用。
如果不是，则该命令使用 `New-PSDrive` cmdlet 创建一个映射到 HKLM： \ SOFTWARE 注册表项的临时驱动器。

### 示例5：比较文件的类型系统驱动器

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

此示例将显示的文件系统驱动器的类型 `Get-PSDrive` 与使用其他方法显示的文件系统驱动器进行比较。 此示例演示了在 Windows PowerShell 中显示驱动器的不同方式，并显示了使用 New-PSDrive cmdlet 创建的特定于会话的驱动器只能在 Windows PowerShell 中访问。

第一个命令使用 `Get-PSDrive` 来获取会话中的所有文件系统驱动器。 这包括固定驱动器 (C：和 D： ) 、映射的网络驱动器 (G：通过使用的 **保持** 参数创建的 G： ) `New-PSDrive` ，以及使用 `New-PSDrive` 不带 **持久性** 参数创建的 PowerShell 驱动器 (T： ) 。

**Net use** 命令显示 Windows 映射网络驱动器，在这种情况下，它只显示 G 驱动器。 它不显示创建的 X：驱动器 `New-PSDrive` 。 它显示 G：驱动器还映射到 \\ \\ 音乐 \\ GratefulDead。

第三条命令使用 Microsoft .NET Framework **System.IO.DriveInfo** 类的 **GetDrives** 方法。 此命令获取 Windows 文件系统驱动器，包括驱动器 G：，但不会获取创建的驱动器 `New-PSDrive` 。

第四条命令使用 `Get-CimInstance` cmdlet 来获取 **Win32_LogicalDisk** 类的实例。 它将返回 A：、C：、D：、E：和 G：驱动器，但不返回创建的驱动器 `New-PSDrive` 。

最后一条命令使用 `Get-CimInstance` cmdlet 来显示 **Win32_NetworkConnection** 类的实例。 与 **net use** 类似，它仅返回由创建的永久性 G：驱动器 `New-PSDrive` 。

## PARAMETERS

### -LiteralName

指定驱动器的名称。

**LiteralName** 的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果名称包括转义符，请将其括在单引号中。 单引号会告知 Windows PowerShell 不要将所有字符都解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

以字符串数组的形式指定此 cmdlet 在操作中获取的驱动器的名称或名称。
键入驱动器名称或驱动器号，不带冒号 (:)。

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

指定为 Windows PowerShell 提供程序形式的字符串数组。 此 cmdlet 仅获取此提供程序支持的驱动器。 键入提供程序的名称，如 FileSystem、Registry 或 Certificate。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Scope

指定此 cmdlet 获取驱动器的范围。

此参数的可接受值为：

- 全球
- 本地
- Script
- 一个相对于当前作用域的数字 (0 到作用域数，其中0是当前作用域，1是其父) 。 默认值为“Local”。

有关详细信息，请参阅 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能通过管道将对象传递给此 cmdlet。

## 输出

### System.Management.Automation.PSDriveInfo

此 cmdlet 将返回表示会话中的驱动器的对象。

## 注释

* 此 cmdlet 用于处理由任何提供程序公开的数据。 若要列出会话中的可用提供程序，请使用 `Get-PSProvider` cmdlet。 有关详细信息，请参阅 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。
* 使用 New-PSDrive cmdlet 的 **Persist** 参数创建的映射网络驱动器是特定于用户帐户的。 在以 "以管理员身份运行" 选项启动的会话中创建的映射网络驱动器，或具有其他用户的凭据的会话在没有显式凭据或当前用户凭据启动的会话中不可见。

## 相关链接

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)

