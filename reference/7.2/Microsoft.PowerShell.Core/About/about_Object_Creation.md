---
description: 说明如何在 PowerShell 中创建对象。
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 72c0d763fe7f3838c8b2ca68930521e24d0e6139
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595841"
---
# <a name="about-object-creation"></a>关于对象创建

## <a name="short-description"></a>简短说明

说明如何在 PowerShell 中创建对象。

## <a name="long-description"></a>长说明

可以在 PowerShell 中创建对象，并使用在命令和脚本中创建的对象。

有多种方法可以创建对象，此列表并不是明确的：

- [New-object](xref:Microsoft.PowerShell.Utility.New-Object)：创建 .NET Framework 对象或 COM 对象的实例。
- [导入-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv) /
  [Convertfrom-csv](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv)：从定义为逗号分隔值的项 (**PSCustomObject**) 创建自定义对象。
- [Convertfrom-csv-json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json)：创建 (Json) JavaScript 对象表示法中定义的自定义对象。
- [Convertfrom-csv-convertfrom-stringdata](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)：创建定义为键值对的自定义对象。
- [添加类型](xref:Microsoft.PowerShell.Utility.Add-Type)：允许你在 PowerShell 会话中定义可使用实例化的类 `New-Object` 。
- [New-Module](xref:Microsoft.PowerShell.Core.New-Module)： **AsCustomObject** 参数创建使用脚本块定义的自定义对象。
- [添加成员](xref:Microsoft.PowerShell.Utility.Add-Member)：向现有对象添加属性。 您可以使用 `Add-Member` 创建一个简单类型的自定义对象，例如 `[System.Int32]` 。
- [选择-对象](xref:Microsoft.PowerShell.Utility.Select-Object)：选择对象的属性。 您可以使用 `Select-Object` 来对已实例化的对象创建自定义和计算属性。

本文介绍了以下附加方法：

- 通过使用静态方法调用类型的构造函数 `new()`
- 通过 typecasting 属性名称和属性值的哈希表

## <a name="static-new-method"></a>静态 new ( # A1 方法

所有 .NET 类型都有一 `new()` 种方法，使您可以更轻松地构造实例。 你还可以查看给定类型的所有可用构造函数。

若要查看类型的构造函数，请在 `new` 类型名称后指定方法名称，然后按 `<ENTER>` 。

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

现在，可以通过指定适当的构造函数来创建一个 **system.web。**

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

您可以使用以下示例来确定当前加载哪些 .NET 类型以供您实例化。

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

使用方法创建的对象 `new()` 可能与 PowerShell cmdlet 创建的相同类型的对象具有不同的属性。 PowerShell cmdlet、提供程序和扩展类型系统可以将额外的属性添加到实例中。

例如，PowerShell 中的 FileSystem 提供程序将六个 **NoteProperty** 值添加到返回的 **DirectoryInfo** 对象 `Get-Item` 。

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

直接创建 **DirectoryInfo** 对象时，该对象没有这6个 **NoteProperty** 值。

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

有关扩展类型系统的详细信息，请参阅 [about_Types.ps1xml](about_Types.ps1xml.md)。

此功能已添加到 PowerShell 5。0

## <a name="create-objects-from-hash-tables"></a>从哈希表创建对象

可以从属性和属性值的哈希表创建对象。

语法如下：

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

此方法仅适用于具有无参数构造函数的类。 对象属性必须是公共且可设置的。

此功能是在 PowerShell 版本3.0 中添加的。

## <a name="create-custom-objects-from-hash-tables"></a>从哈希表创建自定义对象

自定义对象非常有用，使用哈希表方法可以轻松地创建自定义对象。 **PSCustomObject** 类专门为此目的而设计。

自定义对象是一种从函数或脚本返回自定义输出的极好方法。 这更适用于返回无法重新格式化的格式化输出和其他命令的管道。

中的命令 `Test-Object function` 设置一些变量值，然后使用这些值创建自定义对象。 可以在 cmdlet 帮助主题的 "示例" 部分中查看使用此对象 `Update-Help` 。

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

此函数的输出在默认情况下是格式化为表的自定义对象集合。

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

用户可以如同标准对象一样管理自定义对象的属性。

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a>从哈希表创建非自定义对象

还可以使用哈希表为非自定义类创建对象。 为非自定义类创建对象时，命名空间限定的类型名称是必需的，不过您可以省略任何初始 **系统** 命名空间组件。

例如，以下命令会创建一个会话选项对象。

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

哈希表功能的要求尤其是无参数构造函数要求，消除了许多现有的类。 但是，大多数 PowerShell _选项_ 类旨在使用此功能和其他非常有用的类，例如 **ProcessStartInfo** 类。

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

设置参数值时，也可以使用哈希表功能。 例如，的 **SessionOption** 参数的值 `New-PSSession` 。
cmdlet 可以是哈希表。

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a>泛型对象

你还可以在 PowerShell 中创建泛型对象。 泛型是为所存储或使用的一个或多个类型具有占位符（类型形参）的类、结构、接口和方法。

下面的示例创建一个 **字典** 对象。

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

有关泛型的详细信息，请参阅 [.net 中的泛型](/dotnet/standard/generics)。

## <a name="see-also"></a>请参阅

[about_Objects](about_Objects.md)

[about_Methods](about_Methods.md)

[about_Properties](about_Properties.md)

[about_pipelines](about_Pipelines.md)

[about_Types.ps1xml](about_Types.ps1xml.md)
