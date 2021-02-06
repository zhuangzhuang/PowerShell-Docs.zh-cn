---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 0802e025f2bedce0ec312df9878c9524558930cb
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2020
ms.locfileid: "99603818"
---
# Get-Module

## 摘要
列出在当前会话中导入的模块或可以从 PSModulePath 导入的模块。

## SYNTAX

### 加载 (默认值) 

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### 可用

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### PsSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### CimSession

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-Module`Cmdlet 列出已导入或可导入到 powershell 会话中的 powershell 模块。 如果没有参数， `Get-Module` 将获取已导入到当前会话中的模块。 **ListAvailable** 参数用于列出可以从在 PSModulePath 环境变量中指定的路径导入的模块 (`$env:PSModulePath`) 。

返回的 module 对象 `Get-Module` 包含有关模块的重要信息。 还可以通过管道将模块对象传递给其他 cmdlet，如 `Import-Module` 和 `Remove-Module` cmdlet。

`Get-Module` 列出模块，但不导入它们。 从 Windows PowerShell 3.0 开始，当你使用模块中的命令时，将自动导入模块，但命令不会 `Get-Module` 触发自动导入。 你还可以使用 cmdlet 将模块导入到会话中 `Import-Module` 。

从 Windows PowerShell 3.0 开始，可以从远程会话中获取模块，然后将其导入到本地会话中。 此策略使用 PowerShell 的隐式远程处理功能，等效于使用 `Import-PSSession` cmdlet。 当你在从另一个会话导入的模块中使用命令时，这些命令将在远程会话中隐式运行。 此功能使你可以从本地会话管理远程计算机。

此外，从 Windows PowerShell 3.0 开始，你可以使用 `Get-Module` 和 `Import-Module` 来获取和导入通用信息模型 (CIM) 模块。 CIM 模块在 Cmdlet 定义 XML (CDXML) 文件中定义 cmdlet。 此功能允许你使用在非托管代码程序集中实现的 cmdlet，如用 c + + 编写的程序集。

隐式远程处理可用于管理启用了 PowerShell 远程处理的远程计算机。
在远程计算机上创建 **PSSession** ，然后使用的 **pssession** 参数 `Get-Module` 获取远程会话中的 PowerShell 模块。 从远程会话导入模块时，导入的命令将在远程计算机上的会话中运行。

你可以使用类似的策略来管理未启用 PowerShell 远程处理的计算机。
其中包括未运行 Windows 操作系统的计算机，以及安装了 PowerShell 但未启用 PowerShell 远程处理的计算机。

首先，在远程计算机上创建 CIM 会话。 CIM 会话是指与远程计算机上的 WMI) Windows Management Instrumentation (的连接。 然后，使用的 **CIMSession** 参数 `Get-Module` 从 cim 会话中获取 cim 模块。 使用 cmdlet 导入 CIM 模块， `Import-Module` 然后运行导入的命令时，命令将在远程计算机上隐式运行。 你可以将此 WMI 和 CIM 策略用于管理远程计算机。

## 示例

### 示例1：获取导入到当前会话中的模块

```powershell
Get-Module
```

此命令将获取已导入当前会话的模块。

### 示例2：获取已安装模块和可用模块

```powershell
Get-Module -ListAvailable
```

此命令将获取已安装在计算机上的且可导入当前会话的模块。

`Get-Module` 查找 **$env:P smodulepath** 环境变量指定的路径中的可用模块。 有关 **PSModulePath** 的详细信息，请参阅 [about_Modules](About/about_Modules.md) 和 [about_Environment_Variables](About/about_Environment_Variables.md)。

### 示例3：获取所有导出的文件

```powershell
Get-Module -ListAvailable -All
```

此命令将获取所有可用模块的所有导出的文件。

### 示例4：按其完全限定名称获取模块

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

此命令通过使用 **FullyQualifiedName** 参数指定模块的完全限定名称来 **获取该模块。** 然后，该命令通过管道将结果传递 `Format-Table` 给 cmdlet，以将结果的格式设置为表，并将其 **名称** 和 **版本** 作为列标题。

### 示例5：获取模块的属性

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

此命令获取返回的 **PSModuleInfo** 对象的属性 `Get-Module` 。 每个模块文件都有一个对应对象。

可以使用属性来对模块对象进行格式设置和筛选。 有关属性的详细信息，请参阅 [PSModuleInfo properties](/dotnet/api/system.management.automation.psmoduleinfo)。

输出包含 Windows PowerShell 3.0 中引入的新属性（如 **Author** 和 **公司名称**）。

### 示例6：按名称对所有模块分组

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

此命令将获取所有模块文件（已导入并可用），然后按模块名称对其进行分组。 这使你能够查看每个脚本将要导出的模块文件。

### 示例7：显示模块清单的内容

这些命令显示 Windows PowerShell **BitsTransfer** 模块的模块清单的内容。

模块不需要具有清单文件。 如果它们具有清单文件，则需要清单文件才能包含版本号。 但是，清单文件通常可提供有关模块、模块要求和模块内容的有用信息。

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

第一个命令将获取表示 BitsTransfer 模块的 PSModuleInfo 对象。 它将对象保存在 `$m` 变量中。

第二个命令使用 `Get-Content` cmdlet 获取指定路径中的清单文件的内容。 它使用点表示法来获取存储在该对象的 Path 属性中的清单文件的路径。 输出显示了模块清单中的内容。

### 示例8：列出模块目录中的文件

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

此命令将列出模块的目录中的文件。 这是另一种用于在导入模块之前确定模块中的内容的方法。 某些模块可能具有帮助文件或描述该模板的自述文件。

### 示例9：获取安装在计算机上的模块

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

这些命令将获取安装在 Server01 计算机上的模块。

第一个命令使用 `New-PSSession` cmdlet 在 Server01 计算机上创建 **PSSession** 。 该命令将 **PSSession** 保存在 $s 的变量中。

第二个命令使用的 **pssession** 和 **ListAvailable** 参数 `Get-Module` 来获取该变量的 **pssession** 中的模块 `$s` 。

如果通过管道将模块从其他会话传递到 `Import-Module` cmdlet，请 `Import-Module` 使用隐式远程处理功能将模块导入到当前会话中。 这等效于使用 `Import-PSSession` cmdlet。 可以在当前会话中使用模块中的 cmdlet，但使用这些 cmdlet 的命令实际在远程会话中运行。 有关详细信息，请参阅 [`Import-Module`](Import-Module.md) 和 [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md)。

### 示例10：管理未运行 Windows 操作系统的计算机

此示例中的命令使你能够管理未运行 Windows 操作系统的远程计算机的存储系统。
在此示例中，由于计算机的管理员已安装模块发现 WMI 提供程序，因此 CIM 命令可以使用专门用于该提供程序的默认值。

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

第一个命令使用 `New-CimSession` cmdlet 在 RSDGF03 远程计算机上创建会话。 该会话将连接到远程计算机上的 WMI。 此命令将 CIM 会话保存在 `$cs` 变量中。

第二个命令使用变量中的 CIM 会话在 `$cs` `Get-Module` RSDGF03 计算机上运行命令。 该命令使用 Name 参数指定 Storage 模块。 该命令使用管道运算符 (|) 将存储模块发送到 `Import-Module` cmdlet，后者将其导入到本地会话中。

第三个命令在 `Get-Command` `Get-Disk` 存储模块的命令中运行 cmdlet。
将 CIM 模块导入到本地会话中时，PowerShell 会将表示 CIM 模块的 CDXML 文件转换为 PowerShell 脚本，这些脚本在本地会话中显示为函数。

第四个命令运行 `Get-Disk` 命令。 尽管该命令是在本地会话中键入的，但它实际在导入它的远程计算机上隐式运行。 该命令将获取远程计算机中的对象，并将它们返回到本地会话。

## PARAMETERS

### -All

指示此 cmdlet 获取每个模块文件夹中的所有模块（包括嵌套模块、清单 ( psd1) 文件、脚本模块 () 文件）和二进制模块 ( 文件。 如果没有此参数， `Get-Module` 则仅获取每个模块文件夹中的默认模块。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimNamespace

指定可公开 CIM 模块的备用 CIM 提供程序的命名空间。 默认值是模块发现 WMI 提供程序的命名空间。

使用此参数从未运行 Windows 操作系统的计算机和设备获取 CIM 模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimResourceUri

指定 CIM 模块的备用位置。 默认值是远程计算机上模块发现 WMI 提供程序的资源 URI。

使用此参数从未运行 Windows 操作系统的计算机和设备获取 CIM 模块。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession

指定远程计算机上的 CIM 会话。 输入包含 CIM 会话的变量或获取 CIM 会话的命令（如 [CimSession](/powershell/module/cimcmdlets/get-cimsession) 命令）。

`Get-Module` 使用 CIM 会话连接从远程计算机获取模块。 使用 cmdlet 导入模块 `Import-Module` 并在当前会话中使用导入模块中的命令时，命令实际上在远程计算机上运行。

你可以使用此参数从未运行 Windows 操作系统的计算机和设备中获取模块，并使用具有 PowerShell 但未启用 PowerShell 远程处理的计算机。

**CimSession** 参数可获取 **CIMSession** 中的所有模块。 但是，你只能导入基于 CIM 和基于 Cmdlet 定义 XML (CDXML) 的模块。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedName

指定名称以 **ModuleSpecification** 对象的形式指定的模块。 请参阅 ModuleSpecification 构造函数的 "备注" 部分 [ (哈希表) ](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)。

例如， **FullyQualifiedModule** 参数接受以下任何一种格式指定的模块名称：

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 和 **ModuleVersion** 是必需的，但 **Guid** 是可选的。 不能在与 **Module** 参数相同的命令中指定 **FullyQualifiedModule** 参数。 这两个参数是互斥的。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

指示此 cmdlet 获取所有已安装的模块。 `Get-Module` 获取 **PSModulePath** 环境变量中列出的路径中的模块。 如果没有此参数，则 `Get-Module` 仅获取在 **PSModulePath** 环境变量中列出的、在当前会话中加载的模块。 **ListAvailable** 不会返回未在 **PSModulePath** 环境变量中找到的模块的相关信息，即使在当前会话中加载了这些模块也是如此。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定此 cmdlet 获取的模块的名称或名称模式。 允许使用通配符。 还可以通过管道将名称传递给 `Get-Module` 。 不能在与 **Name** 参数相同的命令中指定 **FullyQualifiedName** 参数。

**名称** 不能接受模块 GUID 作为值。
若要通过指定 GUID 来返回模块，请改用 **FullyQualifiedName** 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -PSEdition

获取支持指定的 PowerShell 版本的模块。

此参数的可接受值为：

- 桌面型
- 核心

Get-Module cmdlet 检查 **PSModuleInfo** 对象的 **CompatiblePSEditions** 属性中是否存在指定的值，并仅返回已设置了该属性的模块。

> [!NOTE]
>
> - **桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
> - **核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSSession

获取 (**PSSession**) 的指定用户管理的 PowerShell 会话中的模块。 输入包含会话的变量、获取会话的命令（如 `Get-PSSession` 命令）或创建会话的命令（如 `New-PSSession` 命令）。

如果会话连接到远程计算机，则必须指定 **ListAvailable** 参数。

`Get-Module`使用 **pssession** 参数的命令等效于使用 `Invoke-Command` cmdlet `Get-Module -ListAvailable` 在 **PSSession** 中运行命令。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -刷新

指示此 cmdlet 刷新已安装命令的缓存。 命令缓存是在会话启动时创建的。 它使 `Get-Command` cmdlet 能够从未导入到会话中的模块中获取命令。

此参数旨在用于开发和测试方案，在这些方案中，模块的内容自会话启动后已发生更改。

在命令中指定 **Refresh** 参数时，必须指定 **ListAvailable**。

已在 Windows PowerShell 3.0 中引入了此参数。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipEditionCheck

跳过对字段的检查 `CompatiblePSEditions` 。

默认情况下，Get-Module 将忽略 `%windir%\System32\WindowsPowerShell\v1.0\Modules` 未 `Core` 在字段中指定的目录中的模块 `CompatiblePSEditions` 。 设置此开关时，不会 `Core` 包含模块，因此将返回 Windows PowerShell 模块路径下与 PowerShell Core 不兼容的模块。

在 macOS 和 Linux 上，此参数不执行任何操作。

有关详细信息，请参阅 [about_PowerShell_Editions](About/about_PowerShell_Editions.md) 。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
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

### System.String

可以通过管道将模块名称传递给此 cmdlet。

## 输出

### System.Management.Automation.PSModuleInfo

此 cmdlet 返回表示模块的对象。
指定 **ListAvailable** 参数时，将 `Get-Module` 返回 **ModuleInfoGrouping** 对象，该对象是具有相同属性和方法的 **PSModuleInfo** 对象的类型。

## 注释

- 从 Windows PowerShell 3.0 开始，PowerShell 中包含的核心命令打包在模块中。 异常是 Add-pssnapin **，它是一个** 管理单元， () 。 默认情况下，仅将 **Microsoft.PowerShell.Core** 管理单元添加到会话中。 首次使用时自动导入模块，你可以使用 `Import-Module` cmdlet 将其导入。

- 在 Windows PowerShell 2.0 和在 PowerShell 的更高版本中创建旧样式会话的主机程序中，核心命令打包在 (**PSSnapins**) 的管理单元中。 **Microsoft.PowerShell.Core** 是例外情况，它始终是一个管理单元。 远程会话（如 cmdlet 启动的会话） `New-PSSession` 是包含核心管理单元的旧样式会话。

  有关 **CreateDefault2** 方法的详细信息，请参阅 [CreateDefault2 方法](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2)。

- `Get-Module` 仅在存储在 **PSModulePath** 环境变量的值中的位置获取模块 ($Env:P smodulepath) 。 `Import-Module`Cmdlet 可以将模块导入其他位置，但不能使用 `Get-Module` cmdlet 来获取它们。

- 此外，从 PowerShell 3.0 开始，新的属性已添加到返回的对象，以便在 `Get-Module` 导入模块之前更容易了解模块。 导入之前会填充所有属性。 其中包括列出模块导出的命令的 **ExportedCommands**、 **ExportedCmdlets** 和 **ExportedFunctions** 属性。

- **ListAvailable** 参数仅获取格式正确的模块，即包含至少一个文件（其基名称与模块文件夹的名称相同）的文件夹。 基名称是不带文件扩展名的名称。 如果文件夹包含具有不同名称的文件，则这些文件夹将被视为容器，而不是模块。

  若要获取作为 DLL 文件实现但未包含在模块文件夹中的模块，请同时指定 **ListAvailable** 和 **All** 参数。

- 若要使用 CIM 会话功能，远程计算机必须具有 WS-Management 远程处理和 Windows Management Instrumentation (WMI)，后者是通用信息模型 (CIM) 标准的 Microsoft 实现。 计算机必须还具有模块发现 WMI 提供程序或具有相同基本功能的备用 WMI 提供程序。

  你可以在未运行 Windows 操作系统的计算机和具有 PowerShell 但未启用 PowerShell 远程处理的 Windows 计算机上使用 CIM 会话功能。

  你还可以使用 CIM 参数从启用了 PowerShell 远程处理的计算机中获取 CIM 模块。 这包括本地计算机。 在本地计算机上创建 CIM 会话时，PowerShell 将使用 DCOM 而不是 WMI 来创建会话。

## 相关链接

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[about_Modules](About/about_Modules.md)

[Get-PSSession](Get-PSSession.md)

[Import-Module](Import-Module.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[New-PSSession](New-PSSession.md)

[Remove-Module](Remove-Module.md)

[about_PowerShell_Editions](About/about_PowerShell_Editions.md)
