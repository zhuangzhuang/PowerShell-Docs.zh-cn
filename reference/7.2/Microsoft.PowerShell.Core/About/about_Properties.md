---
description: 介绍如何在 PowerShell 中使用对象属性。
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: c5cc7abdd580a0fa57134f9c79616d1d8290a7e1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597026"
---
# <a name="about-properties"></a>关于属性

## <a name="short-description"></a>简短说明
介绍如何在 PowerShell 中使用对象属性。

## <a name="long-description"></a>长说明

PowerShell 使用称为对象的结构化集合来表示数据存储区中的项或计算机的状态。 通常，使用 Microsoft .NET 框架的一部分的对象，但也可以在 PowerShell 中创建自定义对象。

项与其对象之间的关联非常接近。 更改对象时，通常会更改其表示的项。 例如，在 PowerShell 中获取文件时，不会获得实际文件。 相反，您将获得一个表示该文件的 FileInfo 对象。 更改 FileInfo 对象时，文件也会发生更改。

大多数对象都具有属性。 属性是与对象关联的数据。 不同类型的对象具有不同的属性。 例如，FileInfo 对象（表示文件）有一个 **IsReadOnly** 属性，该属性包含 $True 如果该属性为只读 $False 属性，则为; 如果文件不存在，则为。
表示文件系统目录的 DirectoryInfo 对象具有一个父属性，其中包含父目录的路径。

### <a name="object-properties"></a>对象属性

若要获取对象的属性，请使用 `Get-Member` cmdlet。 例如，若要获取 **FileInfo** 对象的属性，请使用 `Get-ChildItem` cmdlet 获取表示文件的 FileInfo 对象。 然后，使用管道运算符 ( # A0) 将 **FileInfo** 对象发送到 `Get-Member` 。 下面的命令获取 PowerShell.exe 文件并将其发送到 `Get-Member` 。
\$Pshome 自动变量包含 PowerShell 安装目录的路径。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

此命令的输出列出 **FileInfo** 对象的成员。
成员同时包括属性和方法。 在 PowerShell 中工作时，可以访问对象的所有成员。

若要仅获取对象的属性而不获取方法，请使用 cmdlet 的 MemberType 参数，其 `Get-Member` 值为 "property"，如下面的示例中所示。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

找到属性后，可以在 PowerShell 命令中使用这些属性。

## <a name="property-values"></a>属性值

尽管特定类型的每个对象都具有相同的属性，但这些属性的值会描述特定的对象。 例如，每个 FileInfo 对象都有一个 CreationTime 属性，但该属性的值不同于每个文件。

获取对象的属性值的最常见方法是使用点方法。 键入对对象的引用，如包含对象的变量或获取对象的命令。 然后，键入一个点 (。 ) 后跟属性名称。

例如，下面的命令显示 PowerShell.exe 文件的 CreationTime 属性的值。 该 `Get-ChildItem` 命令返回一个 FileInfo 对象，该对象表示 PowerShell.exe 文件。 命令括在括号中，以确保在访问任何属性之前执行该命令。 `Get-ChildItem`命令后跟一个点和 CreationTime 属性的名称，如下所示：

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

你还可以将对象保存在变量中，然后使用点方法获取其属性，如以下示例中所示：

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

你还可以使用 `Select-Object` 和 `Format-List` cmdlet 显示对象的属性值。 `Select-Object``Format-List`每个都有一个 **属性** 参数。 可以使用 **Property** 参数来指定一个或多个属性及其值。 或者，可以使用通配符 (\*) 来表示所有属性。

例如，下面的命令显示 PowerShell.exe 文件的所有属性的值。

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>静态属性

可以在 PowerShell 中使用 .NET 类的静态属性。 静态属性是类的属性，这与作为对象属性的标准属性不同。

若要获取类的静态属性，请使用 Get-Member cmdlet 的静态参数。

例如，下面的命令获取类的静态属性 `System.DateTime` 。

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

若要获取静态属性的值，请使用以下语法。

```
[<ClassName>]::<Property>
```

例如，下面的命令获取类的 UtcNow 静态属性的值 `System.DateTime` 。

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>标量对象和集合的属性

特定类型的一个 ( "标量" ) 对象的属性通常不同于同一类型的对象集合的属性。
例如，每个服务都有作为 **displayname** 属性，但服务集合没有 **displayname** 属性。

以下命令将获取 "Audiosrv" 服务的 **DisplayName** 属性的值。

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

从 PowerShell 3.0 开始，PowerShell 将尝试防止标量对象和集合的属性不同的脚本错误。 同一命令返回返回的每个服务的 **DisplayName** 属性的值 `Get-Service` 。

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

提交集合时，但请求仅存在于单个 ( "标量" ) 对象上的属性时，PowerShell 将返回集合中每个对象的该属性的值。

所有集合都具有 **Count** 属性，该属性可返回集合中的对象数。

```powershell
(Get-Service).Count
```

```output
176
```

从 PowerShell 3.0 开始，如果请求零个对象或一个对象的 Count 或 Length 属性，则 PowerShell 将返回正确的值。

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

如果属性存在于单个对象和集合上，则仅返回集合的属性。

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

此功能也适用于标量对象和集合的方法。 有关详细信息，请参阅 [about_Methods](about_methods.md)。

## <a name="see-also"></a>请参阅

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

