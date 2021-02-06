---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: 742ef9b19294b93be9a2b7dce58bad913d8fd27b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597272"
---
# Get-WinEvent

## 摘要
获取本地和远程计算机上的事件日志和事件跟踪日志文件中的事件。

## SYNTAX

### GetLogSet（默认值）

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### FileSet

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## DESCRIPTION

该 `Get-WinEvent` cmdlet 将从事件日志中获取事件，包括经典日志，例如 **系统** 和 **应用程序** 日志。 该 cmdlet 将从 Windows Vista 中引入的 Windows 事件日志技术生成的事件日志中获取数据。 日志文件中的事件和 **Windows (ETW) 的事件跟踪** 生成的事件。 默认情况下，按 `Get-WinEvent` 从最新到最旧的顺序返回事件信息。

`Get-WinEvent` 列出事件日志和事件日志提供程序。 若要中断该命令，请按<kbd>CTRL</kbd> + <kbd>C</kbd>。 可以从所选的日志或从所选的事件提供程序生成的日志中获取事件。 还可以将来自多个源的事件组合到单个命令中。
`Get-WinEvent` 允许使用 XPath 查询、结构化 XML 查询和哈希表查询来筛选事件。

如果你未以管理员身份运行 PowerShell，你可能会看到错误消息，指出无法检索有关日志的信息。

## 示例

### 示例1：从本地计算机获取所有日志

此命令获取本地计算机上的所有事件日志。 日志按获取顺序列出 `Get-WinEvent` 。 先检索传统日志，然后再检索新的 Windows 事件日志。
日志的 **RecordCount** 可以为空，也可以为零。

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListLog** 参数使用) 通配符 (星号 `*` 来显示有关每个日志的信息。

### 示例2：获取经典安装日志

此命令将获取一个 **system.diagnostics.eventing.reader.eventlogconfiguration** 对象，该对象表示经典 **安装** 日志。 对象包含有关日志的信息，如文件大小、提供程序、文件路径以及是否已启用日志。

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

`Get-WinEvent`Cmdlet 使用 **ListLog** 参数来指定 **安装** 日志。 对象通过管道向下发送到 `Format-List` cmdlet。 `Format-List` 使用带有星号 () 通配符的 **property** 参数 `*` 来显示每个属性。

### 示例3：从服务器获取事件日志

此命令仅获取包含事件的本地计算机上的事件日志。 日志的 **RecordCount** 可以为 null 或零。 该示例使用 `$_` 变量。 有关详细信息，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)。

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListLog** 参数使用) 通配符 (星号 `*` 来显示有关每个日志的信息。 **ComputerName** 参数指定从本地计算机 **localhost** 获取日志。 对象通过管道向下发送到 `Where-Object` cmdlet。 `Where-Object` 使用 `$_.RecordCount` 只返回包含数据的日志。 `$_` 一个变量，表示管道中的当前对象。 **RecordCount** 是具有非 null 值的对象的属性。

### 示例4：从多个服务器获取事件日志

此示例将获取表示三台计算机上的 **应用程序** 事件日志的对象： Server01、Server02 和 Server03。 使用 **ForEach** 关键字的原因是 **ComputerName** 参数只接受一个值。 有关详细信息，请参阅 [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)。

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

变量 `$S` 存储名称三台服务器： **Server01**、 **Server02** 和 **Server03**。 **ForEach** 语句使用循环来处理每个服务器 `($Server in $S)` 。 大括号中的脚本块 (`{ }`) 运行 `Get-WinEvent` 命令。 **ListLog** 参数指定 **应用程序** 日志。 **ComputerName** 参数使用变量 `$Server` 来获取每个服务器的日志信息。

对象通过管道向下发送到 `Select-Object` cmdlet。 `Select-Object` 获取属性 **LogMode**、 **MaximumSizeInBytes**、 **RecordCount**、 **LogName**，并使用计算表达式显示使用该变量的 **ComputerName** `$Server` 。 对象通过管道向下发送到 `Format-Table` cmdlet，以在 PowerShell 控制台中显示输出。 **AutoSize** 参数设置输出的格式以适合屏幕大小。

### 示例5：获取事件日志提供程序和日志名称

此命令获取事件日志提供程序及其写入的日志。

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListProvider** 参数使用) 通配符 (星号 `*` 来显示每个提供程序的相关信息。 在输出中，该 **名称** 是提供程序，而 **LogLinks** 是提供程序写入的日志。

### 示例6：获取写入特定日志的所有事件日志提供程序

此命令将获取所有写入 **应用程序** 日志的提供程序。

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListLog** 参数使用 **应用程序** 获取该日志的对象。 **ProviderNames** 是对象的一个属性，它显示写入 **应用程序** 日志的提供程序。

### 示例7：获取包含特定字符串的事件日志提供程序名称

此命令将获取名称中包含提供程序名称中特定字符串的事件日志提供程序。

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListProvider** 参数使用) 通配符 (星号 `*` 来查找提供程序名称中任意位置的 **策略**。

### 示例8：获取事件提供程序生成的事件 Id

此命令列出 **Microsoft microsoft-windows-grouppolicy** 事件提供程序生成的事件 id 以及事件说明。

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **ListProvider** 参数指定提供程序 **microsoft-windows-grouppolicy**。 表达式括在括号中，并使用 **Events** 属性来获取对象。 对象通过管道向下发送到 `Format-Table` cmdlet。 `Format-Table` 显示事件对象的 **Id** 和 **说明** 。

### 示例9：从事件对象属性中获取日志信息

此示例演示如何使用事件对象属性获取有关日志内容的信息。
事件对象存储在变量中，然后按 **事件 Id** 和 **级别** 进行分组和计数。

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

`Get-WinEvent`Cmdlet 使用 **LogName** 参数指定 **Windows PowerShell** 事件日志。 事件对象存储在 `$Event` 变量中。 的 " **计数** " 属性 `$Event` 显示已记录事件的总数。

该 `$Event` 变量将通过管道向下发送到 `Group-Object` cmdlet。 `Group-Object` 使用 **Property** 参数来指定 **Id** 属性，并按事件 Id 值对对象进行计数。 **NoElement** 参数从对象输出中删除其他属性。 分组对象会按管道向下发送到 `Sort-Object` cmdlet。 `Sort-Object` 使用 **属性** 参数按 **计数** 对对象进行排序。 **降序** 参数按计数显示输出，从最高到最低。 在输出中， **Count** 列包含每个事件的总数。 " **名称** " 列包含分组事件 Id 号。

该 `$Event` 变量将通过管道向下发送到 `Group-Object` cmdlet。 `Group-Object` 使用 **Property** 参数指定 **LevelDisplayName** 属性，并按 **LevelDisplayName** 对对象计数。 对象按级别（如 **警告** 和 **信息**）分组。
**NoElement** 参数从输出中删除其他属性。 在输出中， **Count** 列包含每个事件的总数。 " **名称** " 列包含分组的 **LevelDisplayName**。

### 示例10：获取名称中包含指定字符串的错误事件

此示例使用以逗号分隔的日志名称字符串。 输出按级别进行分组，如 "错误" 或 "警告" 和 "日志名称"。

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **LogName** 参数使用逗号分隔的字符串，其中星号 (`*`) 通配符指定日志名称。 对象通过管道向下发送到 `Group-Object` cmdlet。 `Group-Object` 使用 **Property** 参数按 **LevelDisplayName** 和 **LogName** 对对象进行分组。 **NoElement** 参数从输出中删除其他属性。 分组对象会按管道向下发送到 `Format-Table` cmdlet。 `Format-Table` 使用 **AutoSize** 参数设置列的格式。 " **计数** " 列包含每个事件的总数。 " **名称** " 列包含分组的 **LevelDisplayName** 和 **LogName**。

### 示例11：从存档的事件日志中获取事件

`Get-WinEvent` 可以从已保存的日志文件中获取事件信息。 此示例使用存储在本地计算机上的存档 PowerShell 日志。

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **Path** 参数指定目录和文件名。

### 示例12：从存档的事件日志获取特定数量的事件

这些命令从已存档的事件日志中获取特定数量的事件。 `Get-WinEvent` 具有可获取最大事件数或最早事件数的参数。 此示例使用存储在 **C:\Test\PowerShellCore 操作** 中的存档 PowerShell 日志。

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

该 `Get-WinEvent` cmdlet 将获取计算机中的日志信息。 **Path** 参数指定目录和文件名。 **MaxEvents** 参数指定将显示从最新到最旧的100记录。

### 示例13： Windows 事件跟踪

Windows (ETW 事件跟踪) 事件发生时将事件写入日志。 事件按从旧到新的顺序存储。 存档的 ETW 文件保存为 `.etl` **TraceLog**。
事件按其写入日志的顺序列出，因此 *最早* 的参数是必需的。

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

该 `Get-WinEvent` cmdlet 将从存档的文件中获取日志信息。 **Path** 参数指定目录和文件名。 **最早** 的参数用于按写入事件的顺序（最旧到最新）输出事件。 对象沿着管道向下发送到 cmdlet， `Sort-Object` `Sort-Object` 按 **TimeCreated** 属性的值以降序对对象进行排序。 将对象向下发送到 `Select-Object` 显示100最新事件的 cmdlet。

### 示例14：从事件跟踪日志获取事件

此示例演示如何从事件跟踪日志文件 (`.etl`) 和存档的 Windows PowerShell 日志文件 () 获取事件 `.evtx` 。 可以将多个文件类型组合到单个命令中。
由于这些文件包含相同类型的 **.NET Framework** 对象 **system.diagnostics.eventing.reader.eventlogrecord**，因此可以用相同的属性对其进行筛选。 命令需要 **最早** 的参数，因为它是从文件中读取 `.etl` ，但 **最早** 的参数适用于每个文件。

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

该 `Get-WinEvent` cmdlet 将从存档的文件中获取日志信息。 **Path** 参数使用以逗号分隔的列表来指定每个文件的目录和文件名。 **最早** 的参数用于按写入事件的顺序（最旧到最新）输出事件。 对象通过管道向下发送到 `Where-Object` cmdlet。 `Where-Object` 使用脚本块查找 **Id** 为 **403** 的事件。 `$_`变量表示管道中的当前对象， **Id** 是事件 id 属性。

### 示例15：筛选事件日志结果

此示例演示了用于筛选和选择事件日志中的事件的多种方法。 所有这些命令都从 **Windows PowerShell** 事件日志中获取过去24小时内发生的事件。
筛选器方法比使用 cmdlet 更为有效 `Where-Object` 。 在检索对象时应用筛选器。 `Where-Object` 检索所有对象，然后将筛选器应用于所有对象。

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### 示例16：使用 FilterHashtable 从应用程序日志获取事件

此示例使用 **FilterHashtable** 参数从 **应用程序** 日志获取事件。 哈希表使用 **键/值** 对。 有关 **FilterHashtable** 参数的详细信息，请参阅 [通过 FilterHashtable 创建 Get-WinEvent 查询](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)。
有关哈希表的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)。

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

该 `Get-Date` cmdlet 使用 **AddDays** 方法获取当前日期的两天前的日期。 Date 对象存储在 `$Date` 变量中。

`Get-WinEvent`Cmdlet 将获取日志信息。 **FilterHashtable** 参数用于筛选输出。 **LogName** 项将值指定为 **应用程序** 日志。 **StartTime** 键使用变量中存储的值 `$Date` 。 **Id** 键使用事件 Id 值 **1003**。

### 示例17：使用 FilterHashtable 获取应用程序错误

此示例使用 **FilterHashtable** 参数查找在过去一周内发生的 Internet Explorer 应用程序错误。

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

该 `Get-Date` cmdlet 使用 **AddDays** 方法获取当前日期的七天前的日期。 Date 对象存储在 `$StartTime` 变量中。

`Get-WinEvent`Cmdlet 将获取日志信息。 **FilterHashtable** 参数用于筛选输出。 **LogName** 项将值指定为 **应用程序** 日志。 **ProviderName** 密钥使用值 "**应用程序错误**"，这是事件的 **源**。 **数据** 键使用值 **iexplore.exe** **StartTime** 键使用变量中存储的值 `$StartTime` 。

### 示例18：使用 SuppressHashFilter 筛选应用程序错误

与上面的示例16一样，此示例使用 **FilterHashtable** 参数从 **应用程序** 日志获取事件。 但是，我们添加了 **SuppressHashFilter** 项来筛选出 **信息** 级别事件。

```powershell
$Date = (Get-Date).AddDays(-2)
$filter = @{
  LogName='Application'
  StartTime=$Date
  SuppressHashFilter=@{Level=4}
}
Get-WinEvent -FilterHashtable $filter
```

在此示例中， `Get-WinEvent` 将从 **应用程序** 日志中获取过去两天的所有事件，但 **级别** 为 4 (信息) 的事件除外。

## PARAMETERS

### -ComputerName

指定此 cmdlet 从事件日志获取事件的计算机的名称。 键入计算机 (FQDN) 的 NetBIOS 名称、IP 地址或完全限定的域名。 默认值为本地计算机 **localhost**。 此参数一次只能接受一个计算机名称。

若要从远程计算机获取事件日志，请将事件日志服务的防火墙端口配置为允许远程访问。

此 cmdlet 不依赖于 PowerShell 远程处理。 即使你的计算机未配置为运行远程命令，你也可以使用 **ComputerName** 参数。

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

指定有权执行此操作的用户帐户。 默认值为当前用户。

键入用户名，如 **User01** 或 **Domain01\User01**。 或者输入 **PSCredential** 对象，例如由 cmdlet 生成的对象 `Get-Credential` 。 如果键入用户名，则将提示你输入密码。 如果只键入参数名称，系统会提示输入用户名和密码。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

以哈希表格式指定查询，以从一个或多个事件日志中选择事件。 该查询包含具有一个或多个 **键/值** 对的哈希表。

哈希表查询具有以下规则：

- 键和值不区分大小写。
- 通配符仅在与 **LogName** 和 **ProviderName** 键关联的值中有效。
- 每个密钥只能在每个哈希表中列出一次。
- **路径** 值采用 `.etl` 、 `.evt` 和日志文件的路径 `.evtx` 。
- 可以在同一个查询中使用 **LogName**、 **Path** 和 **ProviderName** 键。
- **UserID** 键可以采用有效的安全标识符 (SID) 或可用于构造有效的 **NTAccount 对象** 的域帐户名。
- **数据** 值采用未命名字段中的事件数据。 例如，经典事件日志中的事件。
- `<named-data>` key 表示命名事件数据字段。

当 `Get-WinEvent` 无法解释 **键/值** 对时，它会将密钥解释为事件中事件数据的区分大小写的名称。

有效的 `Get-WinEvent` **键/值** 对如下所示：

- **LogName**=`<String[]>`
- **ProviderName**=`<String[]>`
- **通道**=`<String[]>`
- **字**=`<Long[]>`
- **识别**=`<Int32[]>`
- **调配**=`<Int32[]>`
- **时间**=`<DateTime>`
- **结束**=`<DateTime>`
- **Id**=`<SID>`
- **数据**=`<String[]>`
- `<named-data>`=`<String[]>`
- **SuppressHashFilter**=`<Hashtable>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

指定一个结构化 XML 查询，此 cmdlet 从一个或多个事件日志中选择事件。

若要生成有效的 XML 查询，请使用 Windows 事件查看器中的 " **创建自定义视图** " 和 " **筛选当前日志** " 功能。 使用对话框中的项创建查询，然后单击 XML 选项卡以查看 XML 格式的查询。 可以将该 XML 从 XML 选项卡复制到 **FilterXml** 参数的值中。 有关事件查看器功能的详细信息，请参阅“事件查看器帮助”。

使用 XML 查询来创建包含多个 XPath 语句的复杂查询。 XML 格式还允许使用 **禁止显示** 查询中的事件的 xml 元素。 有关事件日志查询的 XML 架构的详细信息，请参阅 " [查询架构](/windows/win32/wes/queryschema-schema) " 和 " [事件选择](/previous-versions/aa385231(v=vs.85))" 中的 "xml 事件查询" 部分。

你还可以使用 **FilterHashtable** 参数创建一个 **抑制** 元素。

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

指定 XPath 查询，此 cmdlet 从一个或多个日志中选择事件。

有关 XPath 语言的详细信息，请参阅 " [Xpath 参考](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100)) " 和 " [事件选择](/previous-versions/aa385231(v=vs.85))" 的 "选择筛选器" 部分。

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

获取调试和分析日志以及其他事件日志。 当名称参数的值包含通配符时，需要使用 **Force** 参数才能获取调试或分析日志。

默认情况下， `Get-WinEvent` 除非您指定了调试或分析日志的全名，否则 cmdlet 会排除这些日志。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

指定事件日志。 在以逗号分隔的列表中输入事件日志名称。 允许使用通配符。 若要获取所有日志，请使用星号 (`*`) 通配符。

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

指定此 cmdlet 获取的事件日志提供程序。 事件日志提供程序是可将事件写入事件日志的一种程序或服务。

在以逗号分隔的列表中输入提供程序名称。 允许使用通配符。 若要获取计算机上所有事件日志的提供程序，请使用星号 (`*`) 通配符。

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

指定此 cmdlet 从中获取事件的事件日志。 在以逗号分隔的列表中输入事件日志名称。 允许使用通配符。 你还可以将日志名称通过管道传递给 `Get-WinEvent` cmdlet。

> [!NOTE]
> PowerShell 不会限制你可以请求的日志量。 但是，该 `Get-WinEvent` cmdlet 将查询限制为256的 WINDOWS API。 这可能会导致很难一次筛选所有日志。 可以通过使用 `foreach` 循环遍历每个日志来解决此操作，如下所示： `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -MaxEvents

指定返回的最大事件数。 输入一个整数，例如100。 默认设置为返回日志或文件中的所有事件。

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Oldest

指示此 cmdlet 按最早顺序获取事件。 默认情况下，事件按从新到旧的顺序返回。

若要从 `.etl` 和 `.evt` 文件以及从调试和分析日志中获取事件，此参数是必需的。 在这些文件中，事件按从旧到新的顺序记录，并且只能按从旧到新的顺序返回。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定此 cmdlet 从中获取事件的事件日志文件的路径。 在以逗号分隔的列表中输入日志文件的路径，或使用通配符来创建文件路径模式。

`Get-WinEvent` 支持具有 `.evt` 、 `.evtx` 和 `.etl` 文件扩展名的文件。 可以在同一命令中包括来自不同文件和文件类型的事件。

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

指定为字符串数组，此 cmdlet 从中获取事件的事件日志提供程序。 在以逗号分隔的列表中输入提供程序名称，或使用通配符来创建提供程序名称模式。

事件日志提供程序是可将事件写入事件日志的一种程序或服务。 它不是 PowerShell 提供程序。

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.string、System.Xml.XmlDocument、System.object

可以通过管道将 **LogName** (string) 、 **FilterXML** 查询或 **FilterHashtable** 查询进行管道 `Get-WinEvent` 。

## 输出

### System.Diagnostics.Eventing.Reader.EventLogConfiguration、System.Diagnostics.Eventing.Reader.EventLogRecord、System.Diagnostics.Eventing.Reader.ProviderMetadata

对于 **ListLog** 参数，将 `Get-WinEvent` 返回 **system.diagnostics.eventing.reader.eventlogconfiguration** 对象。

对于 **ListProvider** 参数，将 `Get-WinEvent` 返回 **ProviderMetadata** 对象。

对于所有其他参数， `Get-WinEvent` 返回 **system.diagnostics.eventing.reader.eventlogrecord** 对象。

## 注释

`Get-WinEvent` 旨在替换 `Get-EventLog` 运行 Windows Vista 和更高版本 windows 的计算机上的 cmdlet。 `Get-EventLog` 仅在经典事件日志中获取事件。 为实现后向兼容性保留了 `Get-EventLog`。

`Get-WinEvent` `Get-EventLog` Windows PE)  (windows 预安装环境不支持和 cmdlet。

## 相关链接

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[使用 FilterHashtable 创建 Get-WinEvent 查询](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Group-Object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sort-Object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

