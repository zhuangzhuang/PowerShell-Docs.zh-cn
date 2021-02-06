---
description: 描述如何使用方法对 PowerShell 中的对象执行操作。
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 35eaafcec5d645be6fe88f506bc0971344406273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595837"
---
# <a name="about-methods"></a>关于方法

## <a name="short-description"></a>简短说明
描述如何使用方法对 PowerShell 中的对象执行操作。

## <a name="long-description"></a>长说明

PowerShell 使用对象来表示数据存储区中的项或计算机的状态。 例如，FileInfo 对象表示文件系统驱动器中的文件，ProcessInfo 对象表示计算机上的进程。

对象具有属性，这些属性存储有关对象的数据，以及用于更改对象的方法。

"方法" 是指定可对对象执行的操作的一组指令。 例如， `FileInfo` 对象包括 `CopyTo` 复制该对象所表示的文件的方法 `FileInfo` 。

若要获取任何对象的方法，请使用 `Get-Member` cmdlet。 使用值为 "Method" 的 **MemberType** 属性。 以下命令获取进程对象的方法。

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

若要执行或 "调用" 对象的方法，请键入点 (. ) 、方法名称和一组括号 " ( # A3"。 如果该方法具有参数，请将参数值放在括号内。 每个方法调用都需要括号，即使没有参数时也是如此。 如果该方法采用多个参数，则应使用逗号分隔它们。

例如，以下命令将调用进程的 Kill 方法，以结束计算机上的记事本进程。

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

可以通过组合以上语句来缩短此示例。

```powershell
(Get-Process Notepad).Kill()
```

`Get-Process`命令括在括号中，以确保在调用 Kill 方法之前运行该命令。 `Kill`然后，在返回的对象上调用方法 `Process` 。

另一种非常有用的方法是 `Replace` 字符串的方法。 `Replace`方法将替换字符串中的文本。 在下面的示例中，点 (。 ) 可以紧跟在字符串的右引号之后。

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

如前面的示例所示，您可以对通过使用命令、变量中的对象或导致对象 (如引号) 中的字符串的任何内容的对象调用方法。

从 PowerShell 4.0 开始，支持通过使用动态方法名称进行方法调用。

### <a name="learning-about-methods"></a>了解方法

若要查找对象的方法的定义，请参阅对象类型的 "帮助" 主题，并查找其 "方法" 页。 例如，下面的页描述[进程对象的处理方法。](/dotnet/api/system.diagnostics.process#methods)

若要确定方法的参数，请查看方法定义，它类似于 PowerShell cmdlet 的语法关系图。

方法定义可能有一个或多个方法签名，如 PowerShell cmdlet 的参数集。 签名显示了用于调用方法的所有有效命令格式。

例如，类的 `CopyTo` 方法 `FileInfo` 包含以下两个方法签名：

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

第一种方法签名采用目标文件名 (，路径) 。 下面的示例使用第一 `CopyTo` 种方法将 `Final.txt` 文件复制到 `C:\Bin` 目录。

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> 与 PowerShell 的 _参数_ 模式不同，对象方法以 _表达式_ 模式执行，后者是对生成 PowerShell 的 .net framework 的传递。 _表达式_ 模式中的 **bareword** 参数 (不允许使用不带引号的字符串) 。 使用路径作为参数，而将路径用作参数时，可以看到这种差异。 可以在[about_Parsing](about_Parsing.md)中详细了解分析模式

第二个方法签名采用目标文件名和确定是否应覆盖目标文件（如果该文件已存在）的布尔值。

下面的示例使用第二 `CopyTo` 种方法将 `Final.txt` 文件复制到 `C:\Bin` 目录，并覆盖现有文件。

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a>标量对象和集合的方法

一个特定类型 ( "标量" ) 对象的方法通常不同于同一类型的对象集合的方法。

例如，每个进程都有一 `Kill` 种方法，但进程集合没有 Kill 方法。

从 PowerShell 3.0 开始，PowerShell 将尝试防止标量对象和集合的不同方法导致的脚本错误。

如果提交集合，但请求仅存在于单个 ( "标量" ) 对象中的方法，则 PowerShell 将对集合中的每个对象调用方法。

如果方法存在于单个对象和集合上，则只调用集合的方法。

此功能也适用于标量对象和集合的属性。 有关详细信息，请参阅 [about_Properties](about_Properties.md)。

### <a name="examples"></a>示例

下面的示例在对象集合中运行单个进程对象的 **Kill** 方法。

第一条命令启动记事本进程的三个实例。 `Get-Process` 获取记事本进程的所有三个实例，并将它们保存在 `$p` 变量中。

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

下一个命令对变量中的所有三个进程运行 **Kill** 方法 `$p` 。 即使进程集合没有方法，此命令也有效 `Kill` 。

```powershell
$p.Kill()
Get-Process Notepad
```

`Get-Process`命令确认 `Kill` 方法是否有效。

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

此示例在功能上等效于使用 `Foreach-Object` cmdlet 对集合中的每个对象运行方法。

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a>ForEach 和 Where 方法

从 PowerShell 4.0 开始，支持使用方法语法进行集合筛选。 这允许在处理集合和时使用两种新 `ForEach` 方法 `Where` 。

可阅读 [about_arrays](about_arrays.md) 了解有关这些方法的详细信息

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a>当存在多个重载时调用特定方法

调用 .NET 方法时，请考虑以下方案。 如果某个方法接受一个对象，但通过使用更具体的类型的接口具有重载，则 PowerShell 将选择接受该对象的方法，除非你将其显式转换为该接口。

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

在此示例中，选择的是更少的 `object` **Bar** 方法重载。

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

在此示例中，我们将方法强制转换为接口 **IFoo** ，以选择更具体的 **Bar** 方法重载。

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a>另请参阅

[about_Objects](about_Objects.md)

[about_Properties](about_Properties.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

