---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 93db9ab1c8d70306fbf7243ac045ff0aa455dac6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597867"
---
# Get-Process

## 摘要
获取在本地计算机上运行的进程。

## SYNTAX

### Name（默认值）

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### ID

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### InputObject

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## DESCRIPTION

`Get-Process`Cmdlet 将获取本地或远程计算机上的进程。

如果没有参数，此 cmdlet 将获取本地计算机上的所有进程。 还可以通过进程名称或进程 ID (PID) 指定特定进程，或将进程对象通过管道传递给此 cmdlet。

默认情况下，此 cmdlet 将返回一个进程对象，该对象包含有关进程的详细信息，并支持使你能够启动和停止进程的方法。 你还可以使用 cmdlet 的参数 `Get-Process` 来获取进程中运行的程序的文件版本信息，并获取进程加载的模块。

## 示例

### 示例1：获取本地计算机上所有活动进程的列表

```powershell
Get-Process
```

此命令将获取在本地计算机上运行的所有活动进程的列表。 有关每列的定义，请参阅 [注释](#notes) 部分。

### 示例2：获取有关一个或多个进程的所有可用数据

```powershell
Get-Process winword, explorer | Format-List *
```

此命令获取计算机上的有关 Winword 和 Explorer 进程的所有可用的数据。 它使用 **Name** 参数来指定进程，但它省略了可选的参数名称。 管道运算符将 `|` 数据传递给 `Format-List` cmdlet，后者显示 `*` Winword 和资源管理器进程对象的所有可用属性。

也可通过其进程 ID 来标识这些进程。 例如：`Get-Process -Id 664, 2060`。

### 示例3：获取工作集大于指定大小的所有进程

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

此命令获取所有工作集大于 20 MB 的进程。 它使用 `Get-Process` cmdlet 来获取所有正在运行的进程。 管道运算符将 `|` 进程对象传递给 `Where-Object` cmdlet，该 cmdlet 只选择其值大于20000000字节的工作集属性的对象。 

集 **是进程** 对象的许多属性之一。 若要查看所有属性，请键入 `Get-Process | Get-Member` 。 默认情况下，所有数量属性的值以字节为单位，尽管默认显示以千字节和兆字节为单位列出这些值。

### 示例4：根据优先级列出计算机上的进程

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

这些命令基于其优先级类在计算机上列出进程。 第一个命令获取计算机上的所有进程，然后将其存储在 `$A` 变量中。

第二个命令将存储在变量中的 **进程** 对象通过管道传递 `$A` 给 `Get-Process` cmdlet，然后传递给 `Format-Table` cmdlet，后者使用 **优先级** 视图设置进程的格式。

**优先级** 视图和其他视图在 PowerShell home directory () 中的 types.ps1xml 格式文件中定义 `$pshome` 。

### 示例5：向标准 Get-Process 输出显示添加属性

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

此示例从本地计算机和远程计算机 (S1) 中检索进程。 检索到的进程将通过管道传递给 `Format-Table` 将 **MachineName** 属性添加到标准 `Get-Process` 输出显示的命令。

### 示例6：获取进程的版本信息

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

此命令使用 **FileVersionInfo** 参数获取 pwsh.exe 文件的版本信息，该文件是 PowerShell 进程的主模块。

若要在 Windows Vista 和更高版本的 Windows 上运行此命令，你必须以 "以管理员身份运行" 选项打开 PowerShell。

### 示例7：获取用指定进程加载的模块

```powershell
Get-Process SQL* -Module
```

此命令使用 **Module** 参数来获取已由进程加载的模块。
此命令获取名称以 SQL 开头的进程的模块。

若要在 Windows Vista 和更高版本的 Windows 上对你不拥有的进程运行此命令，必须通过 "以管理员身份运行" 选项启动 PowerShell。

### 示例8：查找进程的所有者

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

此命令演示如何查找进程的所有者。
在 Windows 上， **: includeusername** 参数需要提升的用户权限 (以管理员身份运行) 。
输出显示所有者为 Domain01\user01。

### 示例9：使用自动变量标识托管当前会话的进程

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

这些命令演示如何使用 `$PID` 自动变量来标识承载当前 PowerShell 会话的进程。 可以使用此方法将宿主进程与可能要停止或关闭的其他 PowerShell 进程区分开来。

第一个命令获取当前会话中的所有 PowerShell 进程。

第二个命令获取托管当前会话的 PowerShell 进程。

### 示例10：获取具有主窗口标题的所有进程，并在表中显示这些进程

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

此命令获取具有主窗口标题的所有进程，并在表中显示这些进程及其进程 ID 和进程名称。

**MainWindowTitle** 属性只是返回的 **进程** 对象的许多有用属性之一 `Get-Process` 。 若要查看所有属性，请通过管道将命令结果传递 `Get-Process` 给 `Get-Member` cmdlet `Get-Process | Get-Member` 。

## PARAMETERS

### -FileVersionInfo

指示此 cmdlet 获取进程中运行的程序的文件版本信息。

在 Windows Vista 和更高版本的 Windows 上，必须使用 "以管理员身份运行" 选项打开 PowerShell，才能对你不具有所有权的进程使用此参数。

若要获取远程计算机上某个进程的文件版本信息，请使用 `Invoke-Command` cmdlet。

使用此参数等效于获取每个进程对象的 **Mainmodule.fileversioninfo FileVersionInfo** 属性。 使用此参数时，将 `Get-Process` 返回 **FileVersionInfo** 对象 **FileVersionInfo**，而不是进程对象。 因此，不能通过管道将命令输出传递到需要进程对象的 cmdlet，例如 `Stop-Process` 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

通过进程 ID (PID) 指定一个或多个进程。 若要指定多个 ID，请使用逗号分隔 ID。 若要查找进程的 PID，请键入 `Get-Process`。

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -: Includeusername

指示随命令的结果一起返回 **进程** 对象的用户名值。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定一个或多个进程对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Module

指示此 cmdlet 获取由进程加载的模块。

在 Windows Vista 和更高版本的 Windows 上，必须使用 "以 **管理员身份运行** " 选项打开 PowerShell，才能对你不具有所有权的进程使用此参数。

若要获取远程计算机上由进程加载的模块，请使用 `Invoke-Command` cmdlet。

此参数等效于获取每个进程对象的 **模块** 属性。 使用此参数时，此 cmdlet 将返回 **system.diagnostics.processmodule** 对象 **system.diagnostics.processmodule**，而不是进程对象。 因此，不能通过管道将命令输出传递到需要进程对象的 cmdlet，例如 `Stop-Process` 。

在同一命令中同时使用 *Module* 和 **FileVersionInfo** 参数时，此 Cmdlet 将返回一个 **FileVersionInfo** 对象，其中包含有关所有模块的文件版本的信息。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

通过进程名称指定一个或多个进程。 可以键入多个进程名称（以逗号分隔），并可以使用通配符。 参数名（“Name”）为可选项。

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 输入

### System.Diagnostics.Process

可以将进程对象通过管道传递给此 cmdlet。

## 输出

### "FileVersionInfo"、"System.diagnostics.processmodule" 和 "

默认情况下，此 cmdlet 将返回一个 **system.object** 对象。 如果使用 **FileVersionInfo** 参数，它将返回 **FileVersionInfo** 对象。 如果使用 **Module** 参数（不带 **FileVersionInfo** 参数），则它将返回 **system.diagnostics.processmodule** 对象。

## 注释

- 还可以通过其内置别名、ps 和 gps 来引用此 cmdlet。 有关详细信息，请参阅 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。
- 在运行64位版本的 Windows 的计算机上，64位版本的 PowerShell 仅获取64位进程模块，而版本的 PowerShell 32 的版本仅适用于32位进程模块。
- 可以在 PowerShell 中使用 Windows Management Instrumentation (WMI) Win32_Process 对象的属性和方法。 有关信息，请参阅 `Get-WmiObject` 和 WMI SDK。
- 进程的默认显示为包括以下列的表。 有关进程对象的所有属性的说明，请参阅 [处理属性](/dotnet/api/system.diagnostics.process)。
  - Handles：进程打开的句柄数。
  - NPM (K) ：进程正在使用的非分页内存量（kb）。
  - PM (K) ：进程正在使用的可分页内存量（kb）。
  - WS (K) ：进程工作集的大小（以 kb 为单位）。
    工作集包括进程最近引用的内存的页面。
  - VM (M) ：进程正在使用的虚拟内存量（以 mb 为单位）。
    虚拟内存包括磁盘上分页文件中的存储。
  - CPU () ：进程使用的处理器时间，以秒为单位。
  - ID：进程的进程 ID (PID) 。
  - ProcessName：进程的名称。 有关与进程相关的概念的解释，请参阅帮助和支持中心中的词汇表以及任务管理器帮助。
- 你还可以使用中提供的进程的内置替代视图 `Format-Table` ，例如 **StartTime** 和 **Priority**，还可以设计你自己的视图。

## 相关链接

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
