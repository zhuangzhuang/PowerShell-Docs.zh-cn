---
description: 允许你指示在会话中使用的命名空间。
Locale: en-US
ms.date: 01/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: 2ada269fd0ce6b34a5f7faccfddf47a799301eb9
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "98619935"
---
# <a name="about-using"></a>关于使用

## <a name="short-description"></a>简短说明
允许你指示在会话中使用的命名空间。

## <a name="long-description"></a>详细说明

`using`语句允许您指定在会话中使用的命名空间。 添加命名空间可简化 .NET 类和成员的使用，并允许你从脚本模块和程序集导入类。

`using`语句必须位于脚本或模块中的任何其他语句之前。 该语句前面不能有取消注释语句，包括参数。

`using`语句不能包含任何变量。

`using`语句不应与 `using:` 变量的作用域修饰符混淆。 有关详细信息，请参阅 [about_Remote_Variables](about_Remote_Variables.md)。

## <a name="namespace-syntax"></a>命名空间语法

指定要从中解析类型的 .NET 命名空间：

```
using namespace <.NET-namespace>
```

通过指定命名空间，可以更容易地按简称引用类型。

## <a name="module-syntax"></a>模块语法

从 PowerShell 模块加载类：

```
using module <module-name>
```

的值 `<module-name>` 可以是模块名称、完整的模块规范或模块文件的路径。

当 `<module-name>` 是路径时，路径可以是完全限定路径或相对路径。 相对路径是相对于包含 using 语句的脚本进行解析的。

> [!NOTE]
> 当相对路径包含正斜杠 () 时 `/` ，PowerShell 会将路径视为相对于当前位置，而不是相对于脚本位置。 此 bug 已在 PowerShell 7.1 中解决。

当 `<module-name>` 是名称或模块规范时，PowerShell 将在 **PSModulePath** 中搜索指定的模块。

模块规范是一个包含以下键的哈希表。

- `ModuleName` - **必需** 指定模块名称。
- `GUID` - **可选** 指定模块的 GUID。
- 还 **需要** 指定以下三个键中的一个。 这些密钥不能一起使用。
  - `ModuleVersion` -指定模块的最低可接受版本。
  - `RequiredVersion` -指定模块的准确的必需版本。
  - `MaximumVersion` -指定模块可接受的最大版本。

`using module`语句从根模块导入类 (`ModuleToProcess` 脚本模块或二进制模块的) 。 它不会始终导入嵌套模块中定义的类，也不会将类中定义的类中定义的类始终导入到模块中。 要提供给模块外用户的类应在根模块中定义。

在开发脚本模块的过程中，通常会对代码进行更改，并使用 Force 参数加载模块的新版本 `Import-Module` 。  这仅适用于根模块中的函数更改。 `Import-Module` 不会重新加载任何嵌套模块。 此外，无法加载任何更新的类。

若要确保您运行的是最新版本，必须使用 cmdlet 卸载该模块 `Remove-Module` 。 `Remove-Module` 删除根模块、所有嵌套的模块以及模块中定义的任何类。 然后，可以使用和语句重载该模块和类 `Import-Module` `using module` 。

## <a name="assembly-syntax"></a>程序集语法

若要预加载 .NET 程序集中的类型：

```
using assembly <.NET-assembly-path>
```

加载程序集时，将从该程序集将 .NET 类型预加载到脚本中的分析时。 这允许你创建新的 PowerShell 类，它们使用预先加载的程序集中的类型。

如果未创建新的 PowerShell 类，请改用 `Add-Type` cmdlet。 有关详细信息，请参阅 [添加类型](xref:Microsoft.PowerShell.Utility.Add-Type)。

## <a name="examples"></a>示例

### <a name="example-1---add-namespaces-for-typename-resolution"></a>示例 1-为 typename 解析添加命名空间

下面的脚本获取 "Hello World" 字符串的加密哈希。

请注意 `using namespace System.Text` 和如何 `using namespace System.IO` 简化对中 `[UnicodeEncoding]` `System.Text` 和和的引用 `[Stream]` `[MemoryStream]` `System.IO` 。

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a>示例 2-从脚本模块加载类

在此示例中，有一个名为 **CardGames** 的 PowerShell 脚本模块，用于定义以下类：

- **CardGames**
- **CardGames 卡**

`Import-Module``#requires`语句仅导入模块定义的模块函数、别名和变量。 不导入类。 `using module`命令导入模块，同时加载类定义。

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>示例 3-从程序集加载类

此示例将加载一个程序集，以便可以使用该程序集的类来创建新的 PowerShell 类。 下面的脚本创建一个派生自 **DirectoryContext** 类的新 PowerShell 类。

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```
