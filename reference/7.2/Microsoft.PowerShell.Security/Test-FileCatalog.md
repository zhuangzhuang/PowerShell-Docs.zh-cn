---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 0a990b1c0c46cda06c5239a4c8fde55b29296376
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/15/2020
ms.locfileid: "99597243"
---
# Test-FileCatalog

## 摘要
`Test-FileCatalog` 验证)  ( 的目录文件中包含的哈希是否与实际文件的哈希值相匹配，以便验证其真实性。

此 cmdlet 仅在 Windows 上受支持。

## SYNTAX

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Test-FileCatalog` 通过将目录文件)  ( 的文件哈希与磁盘上实际文件的哈希进行比较来验证文件的真实性。 如果它检测到任何不匹配，它将以 ValidationFailed 的形式返回状态。 用户可通过使用 -Detailed 参数检索所有这些信息。 它还在签名属性中显示目录的签名状态，该状态等效于对 `Get-AuthenticodeSignature` 目录文件调用 cmdlet。 用户也可以使用 -FilesToSkip 参数在验证过程中跳过任何文件。

此 cmdlet 仅在 Windows 上受支持。

## 示例

### 示例1：创建和验证文件目录

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### 示例2：使用详细输出验证文件目录

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## PARAMETERS

### -CatalogFilePath

目录文件的路径 ( .cat) ，其中包含要用于验证的哈希值。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

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

### -Detailed

返回更详细的信息 `CatalogInformation` ，其中包含经过测试的文件、其预期/实际哈希以及目录文件（如果已签名）的 Authenticode 签名。

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

### -FilesToSkip

不应在验证过程中测试的路径的数组。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

应该针对目录文件验证的一个或一组文件。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf

显示运行该 cmdlet 时会发生什么情况。 此 cmdlet 未运行。

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

### DirectoryInfo []，System.string []

管道接受一个字符串或 `DirectoryInfo` 对象的数组，这些字符串或对象表示需要验证的文件的路径。

## 输出

### System.web. CatalogValidationStatus

包含或的值的默认返回类型 `Valid` `ValidationFailed` 。

### System.web. CatalogInformation

当使用时返回更详细的对象 `-Detailed` ，该对象可用于分析可能已通过或可能未通过验证的特定文件，这是预期的哈希值与发现的，以及在目录中使用的算法。

## 注释

此 cmdlet 仅在 Windows 平台上可用。

## 相关链接

[New-FileCatalog](New-FileCatalog.md)

[立即](/powershell/module/PowerShellGet)
