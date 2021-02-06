---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 7a0c25197ba00fb05089f855592e7744ef10e9b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595390"
---
# Export-Clixml

## 摘要
创建一个或多个对象的基于 XML 的表示形式，并将其存储在文件中。

## SYNTAX

### ByPath（默认值）

```
Export-Clixml [-Depth <Int32>] [-Path] <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml [-Depth <Int32>] -LiteralPath <String> -InputObject <PSObject> [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Export-Clixml`Cmdlet (CLI) 基于 XML 的对象或对象的表示形式创建公共语言基础结构，并将其存储在文件中。 然后，可以使用 `Import-Clixml` cmdlet 基于该文件的内容重新创建已保存的对象。
有关 CLI 的详细信息，请参阅 [语言独立性](/dotnet/standard/language-independence)。

此 cmdlet 类似于 `ConvertTo-Xml` ，不同之处在于将 `Export-Clixml` 生成的 XML 存储在文件中。 `ConvertTo-XML` 返回 XML，因此你可以继续在 PowerShell 中处理它。

Windows 计算机上的一个有价值的用途 `Export-Clixml` 是将凭据和安全字符串作为 XML 安全地导出。 有关示例，请参阅示例3。

## 示例

### 示例1：将字符串导出到 XML 文件

此示例将创建一个 XML 文件，该文件存储在当前目录中， **这是一个测试** 字符串的表示形式。

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

该字符串 `This is a test` 沿管道向下发送。 `Export-Clixml` 使用 **Path** 参数 `sample.xml` 在当前目录中创建一个名为的 XML 文件。

### 示例2：将对象导出到 XML 文件

此示例演示如何将对象导出到 XML 文件，然后通过从该文件导入 XML 来创建对象。

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

`Get-Acl`Cmdlet 将获取该文件的安全描述符 `Test.txt` 。 它将对象向下发送到管道，以将安全描述符传递给 `Export-Clixml` 。 对象的基于 XML 的表示形式存储在名为的文件中 `FileACL.xml` 。

`Import-Clixml`Cmdlet 可从该文件中的 XML 创建对象 `FileACL.xml` 。 然后，它将对象保存在 `$fileacl` 变量中。

### 示例3：在 Windows 上加密已导出的凭据对象

在此示例中，给定通过运行 cmdlet 存储在变量中的凭据 `$Credential` `Get-Credential` ，可以运行 `Export-Clixml` cmdlet 将凭据保存到磁盘。

> [!IMPORTANT]
> `Export-Clixml` 仅导出 Windows 上的加密凭据。 在非 Windows 操作系统（如 macOS 和 Linux）上，凭据将导出为作为 Unicode 字符数组存储的纯文本。 这会提供一些模糊处理，但不提供加密。

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdlet 使用 Windows[数据保护 API](/previous-versions/windows/apps/hh464970(v=win.10))加密凭据对象。 加密可确保只有该计算机上的用户帐户才能解密 credential 对象的内容。
导出的 `CLIXML` 文件不能用于其他计算机或其他用户。

在此示例中，存储凭据的文件由表示 `TestScript.ps1.credential` 。 将 **TestScript** 替换为要在其中加载凭据的脚本的名称。

将凭据对象向下发送到管道 `Export-Clixml` ，并将其保存到在 `$Credxmlpath` 第一个命令中指定的路径。

若要将凭据自动导入脚本，请运行最后两个命令。 运行 `Import-Clixml` 将受保护的凭据对象导入脚本。 此导入消除了在脚本中公开纯文本密码的风险。

### 示例4：在 Linux 或 macOS 上导出 credential 对象

在此示例中，我们使用 cmdlet 在变量中创建 **PSCredential** `$Credential` `Get-Credential` 。 然后，使用将 `Export-Clixml` 凭据保存到磁盘。

> [!IMPORTANT]
> `Export-Clixml` 仅导出 Windows 上的加密凭据。 在非 Windows 操作系统（如 macOS 和 Linux）上，凭据将导出为作为 Unicode 字符数组存储的纯文本。 这会提供一些模糊处理，但不提供加密。

```powershell
PS> $Credential = Get-Credential

PowerShell credential request
Enter your credentials.
User: User1
Password for user User1: ********

PS> $Credential | Export-Clixml ./cred2.xml
PS> Get-Content ./cred2.xml

...
    <Props>
      <S N="UserName">User1</S>
      <SS N="Password">700061007300730077006f0072006400</SS>
    </Props>
...

PS> 'password' | Format-Hex -Encoding unicode

   Label: String (System.String) <52D60C91>

          Offset Bytes                                           Ascii
                 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
          ------ ----------------------------------------------- -----
0000000000000000 70 00 61 00 73 00 73 00 77 00 6F 00 72 00 64 00 p a s s w o r d
```

`Get-Content`在此示例中，的输出已截断，以重点关注 XML 文件中的凭据信息。 请注意，密码的纯文本值作为 Unicode 字符数组存储在 XML 文件中，如经过验证 `Format-Hex` 。 因此，对该值进行编码，但不对其进行加密。

## PARAMETERS

### -Confirm

提示你在运行 cmdlet 之前进行确认。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Depth

指定 XML 表示形式中所包含的包含对象的级别数。 默认值是 `2`。

对于文件中的对象类型，可以重写默认值 `Types.ps1xml` 。 有关详细信息，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
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

> [!NOTE]
> 不建议使用 **utf-7** _ _。 在 PowerShell 7.1 中，如果 `utf7` 为 _ *Encoding** 参数指定，则会写入警告。

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

强制运行命令而不要求用户确认。

使该 cmdlet 清除输出文件的只读属性（如有必要）。 该 cmdlet 将在命令完成时尝试重置只读属性。

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

### -InputObject

指定要转换的对象。 输入一个包含对象的变量，或键入可获取对象的命令或表达式。 还可以通过管道将对象传递给 `Export-Clixml` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

指定指向将存储对象的 XML 表示形式的文件的路径。 与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

指示该 cmdlet 不会覆盖现有文件的内容。 默认情况下，如果指定路径中存在文件，则 `Export-Clixml` 将覆盖该文件而不发出警告。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定指向将存储对象的 XML 表示形式的文件的路径。

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 cmdlet 未运行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以将任何对象通过管道进行管道 `Export-Clixml` 。

## 输出

### System.IO.FileInfo

`Export-Clixml` 创建包含 XML 的文件。

## 注释

## 相关链接

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[导出-Csv](Export-Csv.md)

[Import-Clixml](Import-Clixml.md)

[Join-Path](../Microsoft.PowerShell.Management/Join-Path.md)

[Securely Store Credentials on Disk](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)（将凭据安全存储到磁盘）

[Use PowerShell to Pass Credentials to Legacy Systems](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)（使用 PowerShell 将凭据传递到旧系统）

[Windows.Security.Cryptography.DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
