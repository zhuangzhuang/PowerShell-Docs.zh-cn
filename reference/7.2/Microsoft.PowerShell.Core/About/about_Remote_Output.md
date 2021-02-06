---
description: 描述如何解释和格式化远程命令的输出。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595805"
---
# <a name="about-remote-output"></a>关于远程输出

## <a name="short-description"></a>简短说明
描述如何解释和格式化远程命令的输出。

## <a name="long-description"></a>详细说明

在远程计算机上运行的命令的输出可能类似于在本地计算机上运行的同一个命令的输出，但存在一些重要的差异。

本主题说明如何解释、格式化和显示在远程计算机上运行的命令的输出。

## <a name="displaying-the-computer-name"></a>显示计算机名称

使用 Invoke-Command cmdlet 在远程计算机上运行命令时，该命令将返回一个对象，该对象包含生成数据的计算机的名称。 远程计算机名称存储在 PSComputerName 属性中。

对于许多命令，默认情况下会显示 PSComputerName。 例如，以下命令在两台远程计算机 Server01 和 Server02 上运行 Get-Culture 命令。 输出如下所示，其中包含运行命令的远程计算机的名称。

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

您可以使用 Invoke-Command 的 HideComputerName 参数来隐藏 PSComputerName 属性。 此参数专为从一台远程计算机收集数据的命令而设计。

以下命令在 Server01 远程计算机上运行 Get-Culture 命令。 它使用 HideComputerName 参数来隐藏 PSComputerName 属性和相关属性。

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

如果默认情况下不显示 PSComputerName 属性，还可以显示该属性。

例如，以下命令使用 Format-Table cmdlet 将 PSComputerName 属性添加到远程 Get-Date 命令的输出中。

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a>显示 MACHINENAME 属性

多个 cmdlet （包括获取进程、获取服务和获取事件日志）都具有一个用于获取远程计算机上的对象的 ComputerName 参数。
这些 cmdlet 不使用 PowerShell 远程处理，因此即使在未配置为在 Windows PowerShell 中进行远程处理的计算机上，也可以使用它们。

这些 cmdlet 返回的对象在 MachineName 属性中存储远程计算机的名称。  (这些对象没有 PSComputerName 属性。 ) 

例如，此命令将获取 Server01 和 Server02 远程计算机上的 PowerShell 进程。 默认显示不包括 MachineName 属性。

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

可以使用 Format-Table cmdlet 显示进程对象的 MachineName 属性。

例如，以下命令将进程保存在 $p 变量中，然后使用管道运算符 (|) 将 $p 中的进程发送到 Format-Table 命令。 该命令使用 Format-Table 的属性参数在显示中包括 MachineName 属性。

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

下面更复杂的命令将 MachineName 属性添加到默认进程显示。 它使用哈希表来指定计算属性。 幸运的是，您不必理解它来使用它。

 (请注意，反撇号 ['] 是继续符。 ) 

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a>反序列化对象

当运行生成输出的远程命令时，命令输出会通过网络传输回本地计算机。

由于大多数实时 Microsoft .NET 框架对象 (例如 PowerShell cmdlet 返回) 的对象无法通过网络进行传输，因此活动对象将 "序列化"。 换句话说，活动对象将转换为对象及其属性的 XML 表示形式。 然后，基于 XML 的序列化对象通过网络传输。

在本地计算机上，PowerShell 接收基于 XML 的序列化对象，并通过将基于 XML 的对象转换为标准 .NET Framework 对象来进行 "反序列化"。

但是，反序列化的对象不是活动对象。 它是对象在序列化时的快照，它包含属性，但没有方法。 可以在 PowerShell 中使用和管理这些对象，这些对象包括在管道中传递它们、显示所选属性以及设置它们的格式。

大多数反序列化对象会自动设置格式，以供 Types.ps1xml 或 Format.ps1xml 文件中的项显示。 但是，本地计算机可能没有对远程计算机上生成的所有反序列化对象的格式设置文件。 如果未设置对象的格式，则每个对象的所有属性都将显示在控制台中的流列表中。

如果未自动设置对象的格式，则可以使用格式设置 cmdlet （如 Format-Table 或格式列表）来设置所选属性的格式并显示这些属性。 或者，可以使用 Out-GridView cmdlet 显示表中的对象。

此外，如果你在远程计算机上运行的命令所使用的 cmdlet 不在本地计算机上，则该命令返回的对象的格式可能不正确，因为你的计算机上没有这些对象的格式设置文件。 若要从另一台计算机获取格式设置数据，请使用 Get-FormatData 和 Export-FormatData cmdlet。

某些对象类型（如 DirectoryInfo 对象和 Guid）在收到时转换回活动对象。 这些对象不需要任何特殊的处理或格式。

## <a name="ordering-the-results"></a>对结果进行排序

Cmdlet 的 ComputerName 参数中计算机名称的顺序决定了 PowerShell 连接到远程计算机的顺序。 但是，结果以本地计算机接收它们的顺序显示，这可能是不同的顺序。

若要更改结果的顺序，请使用 Sort-Object cmdlet。 可以按 PSComputerName 或 MachineName 属性进行排序。 您还可以对对象的另一个属性进行排序，以使不同计算机的结果交错。

## <a name="see-also"></a>另请参阅

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Get-Process](xref:Microsoft.PowerShell.Management.Get-Process)

[Get-Service](xref:Microsoft.PowerShell.Management.Get-Service)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

