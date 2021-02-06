---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-PSSession
ms.openlocfilehash: 334746589ed991ea817929eb31100f92c2dfda1f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603794"
---
# Export-PSSession

## 摘要

导出另一个会话中的命令，并将其保存在 PowerShell 模块中。

## SYNTAX

### 全部

```
Export-PSSession [-OutputModule] <String> [-Force] [-Encoding <Encoding>]
 [[-CommandName] <String[]>] [-AllowClobber] [-ArgumentList <Object[]>]
 [-CommandType <CommandTypes>] [-Module <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-FormatTypeName] <String[]>] [-Certificate <X509Certificate2>] [-Session] <PSSession>
 [<CommonParameters>]
```

## DESCRIPTION

此 `Export-PSSession` cmdlet 从本地或远程计算机上 (PSSession) 的其他 PowerShell 会话中获取 cmdlet、函数、别名和其他命令类型，并将它们保存在 PowerShell 模块中。 若要将该模块中的命令添加到当前会话中，请使用 `Import-Module` cmdlet。

与 `Import-PSSession` （不同于）将命令从另一个 PSSession 导入到当前会话中， `Export-PSSession` 将命令保存在模块中。 这些命令不会被导入到当前会话中。

若要导出命令，请使用 `New-PSSession` cmdlet 创建具有要导出的命令的 PSSession。 然后使用 `Export-PSSession` cmdlet 导出命令。

若要防止命令名称冲突，则的默认值 `Export-PSSession` 是导出所有命令，当前会话中存在的命令除外。 可以使用 **CommandName** 参数来指定要导出的命令。

`Export-PSSession`Cmdlet 使用 PowerShell 的隐式远程处理功能。 将命令导入到当前会话中时，它们将在原始会话或原始计算机上的类似会话中隐式运行。

## 示例

### 示例1：从 PSSession 导出命令

此示例将从本地计算机创建新的 PSSession 到 Server01 计算机。 除当前会话中存在的命令外，所有命令都导出到本地计算机上名为 Server01 的模块中。 导出包括这些命令的格式设置数据。

```powershell
$S = New-PSSession -ComputerName Server01
Export-PSSession -Session $S -OutputModule Server01
```

`New-PSSession`命令在 Server01 计算机上创建 PSSession。 PSSession 存储在 `$S` 变量中。 此 `Export-PSSession` 命令会将 `$S` 变量的命令和格式数据导出到 Server01 模块中。

### 示例2：导出 Get 和 Set 命令

此示例从服务器导出所有 `Get` 和 `Set` 命令。

```powershell
$S = New-PSSession -ConnectionUri https://exchange.microsoft.com/mailbox -Credential exchangeadmin01@hotmail.com -Authentication Negotiate
Export-PSSession -Session $S -Module exch* -CommandName Get-*, Set-* -FormatTypeName * -OutputModule $PSHOME\Modules\Exchange -Encoding ASCII
```

这些命令将 `Get` 和 `Set` 命令从远程计算机上的 Microsoft exchange Server 管理单元导出到本地计算机上的目录中的 exchange 模块 `$PSHOME\Modules` 。
将模块放在 `$PSHOME\Modules` 目录中后，计算机的所有用户都可以访问它。

### 示例3：从远程计算机导出命令

此示例从远程计算机上的 PSSession 导出 cmdlet，并将它们保存在本地计算机上的模块中。 将模块中的 cmdlet 添加到当前会话，以便可以使用它们。

```powershell
$S = New-PSSession -ComputerName Server01 -Credential Server01\User01
Export-PSSession -Session $S -OutputModule TestCmdlets -Type Cmdlet -CommandName *test* -FormatTypeName *
Remove-PSSession $S
Import-Module TestCmdlets
Get-Help Test*
Test-Files
```

此 `New-PSSession` 命令在 Server01 计算机上创建 PSSession，并将其保存在 `$S` 变量中。 `Export-PSSession`命令将名称以 Test 开头的 cmdlet 从中的 PSSession 导出 `$S` 到本地计算机上的 TestCmdlets 模块。

`Remove-PSSession`Cmdlet `$S` 从当前会话中删除 PSSession。 此命令显示 PSSession 不需要处于活动状态即可使用从会话中导入的命令。 `Import-Module`Cmdlet 将 TestCmdlets 模块中的 cmdlet 添加到当前会话。 可随时在任何会话中运行该命令。

`Get-Help`Cmdlet 将获取名称以 "Test" 开头的 cmdlet 的帮助。 将模块中的命令添加到当前会话后，可以使用 `Get-Help` 和 `Get-Command` cmdlet 来了解导入的命令。 `Test-Files`Cmdlet 从 Server01 计算机导出并添加到会话中。 该 `Test-Files` cmdlet 在从中导入该命令的计算机上的远程会话中运行。 PowerShell 将从 TestCmdlets 模块中存储的信息创建一个会话。

### 示例4：在当前会话中导出和寄存器命令

此示例将存储在变量中的命令导出到当前会话中。

```powershell
Export-PSSession -Session $S -AllowClobber -OutputModule AllCommands
```

此 `Export-PSSession` 命令会将变量中 PSSession 的所有命令和格式数据导出 `$S` 到当前会话中。 **AllowClobber** 参数包含的命令与当前会话中的命令具有相同的名称。

### 示例5：从关闭的 PSSession 导出命令

此示例演示如何在关闭创建导出的命令的 PSSession 后，通过特殊选项运行导出的命令。

如果在导入模块时原始远程会话已关闭，则该模块将使用连接到原始计算机的任何打开的远程会话。 如果源计算机没有当前会话，则该模块将重新建立会话。

若要在远程会话中使用特殊选项运行导出的命令，您必须在导入模块之前，使用这些选项创建远程会话。 将 `New-PSSession` cmdlet 与 **SessionOption** 参数一起使用

```powershell
$Options = New-PSSessionOption -NoMachineProfile
$S = New-PSSession -ComputerName Server01 -SessionOption $Options
Export-PSSession -Session $S -OutputModule Server01
Remove-PSSession $S
New-PSSession -ComputerName Server01 -SessionOption $Options
Import-Module Server01
```

`New-PSSessionOption`Cmdlet 将创建一个 **PSSessionOption** 对象，并将该对象保存在 `$Options` 变量中。 `New-PSSession`命令在 Server01 计算机上创建 PSSession。
**SessionOption** 参数使用存储在中的对象 `$Options` 。 会话存储在 `$S` 变量中。

`Export-PSSession`Cmdlet 可将中的 PSSession 的命令导出 `$S` 到 Server01 模块中。
`Remove-PSSession`Cmdlet 将删除该变量中的 PSSession `$S` 。

`New-PSSession`Cmdlet 将创建一个连接到 Server01 计算机的新 PSSession。 **SessionOption** 参数使用存储在中的对象 `$Options` 。 `Import-Module`Cmdlet 从 Server01 模块导入命令。 模块中的命令在 Server01 计算机上的 PSSession 中运行。

## PARAMETERS

### -AllowClobber

导出指定命令，即使它们与当前会话中的命令同名。

如果导出与当前会话中的命令同名的命令，则导出的命令会隐藏或替换原始命令。 有关详细信息，请参阅 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。

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

### -ArgumentList

将使用指定的参数（参数值）所得到的命令的变体导出。

例如，若要导出证书中的命令的变体 `Get-Item` (Cert： ) 驱动器 `$S` ，请键入 `Export-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificate

指定客户端证书，该证书用于对创建的模块中 ( * .Format.ps1xml) 或脚本模块文件 ( hbase-runner.psm1) 进行签名 `Export-PSSession` 。 输入一个包含证书的变量，或可获取该证书的命令或表达式。

若要查找证书，请使用 `Get-PfxCertificate` cmdlet，或使用 `Get-ChildItem` 证书 (Cert： ) 驱动器中的 cmdlet。 如果证书无效或不具有足够的权限，则该命令将失败。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

仅将具有指定名称或名称模式的命令导出。 允许使用通配符。 使用 **CommandName** 或其 **别名。**

默认情况下， `Export-PSSession` 从 PSSession 导出所有命令，但与当前会话中的命令同名的命令除外。 这可以防止当前会话中的命令隐藏或替换命令。 若要导出所有命令（甚至是那些隐藏或替换其他命令的命令），请使用 **AllowClobber** 参数。

如果使用 **CommandName** 参数，则将不导出命令的格式设置文件，除非使用 **FormatTypeName** 参数。 同样，如果使用 **FormatTypeName** 参数，则不会导出任何命令，除非使用 **CommandName** 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: True
```

### -CommandType

仅导出指定类型的命令对象。 使用 **CommandType** 或其别名 **Type**。

此参数可接受的值如下所示：

- A. 当前会话中的所有 PowerShell 别名。
- 全部。 所有命令类型。 它等效于 `Get-Command -Name *` 。
- 应用程序。 Path 环境变量中列出的路径中的 PowerShell 文件以外的所有文件 (`$env:path`) ，包括 .txt、.exe 和 .dll 文件。
- Cmdlet. 当前会话中的 cmdlet。 Cmdlet 为默认值。
- 配置。 PowerShell 配置。 有关详细信息，请参阅 [about_Session_Configurations](../Microsoft.PowerShell.Core/About/about_Session_Configurations.md)。
- ExternalScript. Path 环境变量中列出的路径中的所有 ps1 文件 (`$env:path`) 。
- Filter 和 Function。 所有 PowerShell 函数。
- 脚本。 当前会话中的脚本块。
- Workflow. PowerShell 工作流。 有关详细信息，请参阅 [about_Workflows](/powershell/module/PSWorkflow/About/about_Workflows)。

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, All, Application, Cmdlet, Configuration, ExternalScript, Filter, Function, Script, Workflow

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

指定目标文件的编码类型。 默认值是 `utf8NoBOM`。

此参数可接受的值如下所示：

- `ascii`：使用 ASCII (7 位) 字符集的编码。
- `bigendianunicode`：使用大字节序字节顺序对 UTF-16 格式进行编码。
- `bigendianutf32`：使用大字节序字节顺序编码为32格式。
- `oem`：使用 MS-DOS 和控制台程序的默认编码。
- `unicode`：使用小 endian 字节顺序对 UTF-16 格式进行编码。
- `utf7`：以 UTF-7 格式进行编码。
- `utf8`：以 UTF-8 格式进行编码。
- `utf8BOM`：以 UTF-8 格式编码 (BOM) 
- `utf8NoBOM`：以 UTF-8 格式编码，而不包含字节顺序标记 (BOM) 
- `utf32`：以32格式编码。

从 PowerShell 6.2 开始， **Encoding** 参数还允许已注册代码页的数字 id (如 `-Encoding 1251` (如) 所注册代码页的) 或字符串名称 `-Encoding "windows-1251"` 。 有关详细信息，请参阅 .NET 文档中的[编码。](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

即使该文件具有只读属性，也会覆盖一个或多个现有输出文件。

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

### -FormatTypeName

仅导出指定 Microsoft .NET Framework 类型的格式指令。 输入类型名称。 默认情况下， `Export-PSSession` 将导出所有不在 **system.web** 命名空间中的 .NET Framework 类型的格式说明。

此参数的值必须是要 `Get-FormatData` 从其导入命令的会话中的命令返回的类型的名称。 若要获取远程会话中的所有格式设置数据，请键入 `*` 。

如果使用 **FormatTypeName** 参数，则不会导出任何命令，除非使用 **CommandName** 参数。

如果使用 **CommandName** 参数，则将不导出命令的格式设置文件，除非使用 **FormatTypeName** 参数。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

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
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

仅导出指定 PowerShell 管理单元和模块中的命令。 输入管理单元和模块的名称。 不允许使用通配符。

有关详细信息，请参阅 `Import-Module` 和 [about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: All commands in the session.
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputModule

指定由创建的模块的可选路径和名称 `Export-PSSession` 。 默认路径为 `$home\Documents\WindowsPowerShell\Modules`。 此参数是必需的。

如果已存在模块子目录或创建的任何文件 `Export-PSSession` ，则该命令将失败。 若要覆盖现有文件，请使用 **Force** 参数。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, ModuleName

Required: True
Position: 1
Default value: $home\Documents\WindowsPowerShell\Modules
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定要从中导出命令的 PSSession。 输入包含会话对象的变量或获取会话对象的命令（如 `Get-PSSession` 命令）。 此参数是必需的。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

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

不能通过管道将对象传递给 `Export-PSSession` 。

## 输出

### System.IO.FileInfo

`Export-PSSession` 返回包含它所创建的模块的文件列表。

## 注释

`Export-PSSession` 依赖于 PowerShell 远程处理基础结构。 若要使用此 cmdlet，必须对计算机进行相应配置以进行远程处理。 有关详细信息，请参阅 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)。

不能使用 `Export-PSSession` 导出 PowerShell 提供程序。

导出的命令在从中导出这些命令的 PSSession 中隐式运行。 远程运行命令的详细信息完全由 PowerShell 处理。 可以像运行本地命令那样运行导出的命令。

`Export-ModuleMember` 捕获并保存有关它所导出的模块中的 PSSession 的信息。 如果在导入模块时从中导出命令的 PSSession 已关闭，并且同一台计算机上没有活动的 Pssession，则该模块中的命令将尝试重新创建 PSSession。 如果重新创建 PSSession 的尝试失败，则导出的命令将不会运行。

`Export-ModuleMember`在模块中捕获和保存的会话信息不包括会话选项，如您在首选项变量中指定的， `$PSSessionOption` 或者使用 `New-PSSession` 、 `Enter-PSSession` 或 cmdlet 的 SessionOption 参数 `Invoke-Command` 。 如果在导入模块时原始 PSSession 已关闭，则该模块将使用同一台计算机上的另一个 PSSession（如果存在）。 若要启用导入的命令以在正确配置的会话中运行，请在导入模块之前使用所需选项来创建 PSSession。

若要查找要导出的命令，请 `Export-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中运行命令。 若要获取和保存命令的格式设置数据，请使用 `Get-FormatData` 和 `Export-FormatData` cmdlet。 `Invoke-Command` `Get-Command` `Get-FormatData` `Export-FormatData` 运行命令时，可能会看到来自、、和的错误消息 `Export-PSSession` 。 此外， `Export-PSSession` 不能从不包括 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 cmdlet 的会话中导出命令 `Get-Help` 。

`Export-PSSession` 使用 `Write-Progress` cmdlet 显示该命令的进度。 该命令正在运行时，你可能会看到进度条。

导出的命令与其他远程命令具有相同的限制（包括无法启动具有用户界面的程序，如记事本）。

因为 PowerShell 配置文件不在 Pssession 中运行，所以配置文件添加到会话中的命令不能用于 `Export-PSSession` 。 若要从配置文件中导出命令，请在 `Invoke-Command` 导出命令之前使用命令手动运行该配置文件。

创建的模块 `Export-PSSession` 可能包含格式设置文件，即使该命令不导入格式数据也是如此。 如果该命令不导入格式数据，则创建的任何格式设置文件都不包含格式数据。

## 相关链接

[about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)

[about_PSSessions](../Microsoft.PowerShell.Core/About/about_PSSessions.md)

[about_PSSnapins](/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1)

[about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)

[Import-Module](../Microsoft.PowerShell.Core/Import-Module.md)

[Import-PSSession](Import-PSSession.md)

[Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-PSSessionOption](../Microsoft.PowerShell.Core/New-PSSessionOption.md)

[Remove-PSSession](../Microsoft.PowerShell.Core/Remove-PSSession.md)
