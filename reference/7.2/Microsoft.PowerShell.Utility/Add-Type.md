---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: d55925b0580542459e62e60108f855508232f232
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597042"
---
# Add-Type

## 摘要
将 Microsoft .NET Core 类添加到 PowerShell 会话。

## SYNTAX

### FromSource (默认值) 

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## DESCRIPTION

`Add-Type`Cmdlet 可让你在 PowerShell 会话中定义 Microsoft .NET 核心类。 然后，可以使用 cmdlet 实例化对象， `New-Object` 并像使用任何 .Net Core 对象一样使用对象。 如果将命令添加 `Add-Type` 到 powershell 配置文件，则该类可用于所有 powershell 会话。

你可以通过指定现有程序集或源代码文件来指定类型，也可以指定内联源代码或保存在变量中的源代码。 甚至可以仅指定方法，并 `Add-Type` 定义和生成类。 在 Windows 上，可以使用此功能在 PowerShell 中将平台调用 (P/Invoke) 调用非托管函数。 如果指定源代码，将 `Add-Type` 编译指定的源代码，并生成包含新 .Net Core 类型的内存中程序集。

您可以使用的参数 `Add-Type` 指定替代语言和编译器，c # 是默认值、编译器选项、程序集依赖项、类命名空间、类型名称和生成的程序集。

从 PowerShell 7 开始， `Add-Type` 如果已存在具有相同名称的类型，则不会编译类型。 此外，还 `Add-Type` 会在包含的文件夹下的文件夹中查找程序集 `ref` `pwsh.dll` 。

## 示例

### 示例1：向会话添加 .NET 类型

此示例通过指定存储在变量中的源代码，将 **BasicTest** 类添加到会话中。 **BasicTest** 类用于添加整数、创建对象和将整数相乘。

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

`$Source`变量存储类的源代码。 该类型具有一个名为的静态方法 `Add` 和一个名为的非静态方法 `Multiply` 。

`Add-Type`Cmdlet 可将类添加到会话中。 由于它使用内联源代码，因此该命令使用 **TypeDefinition** 参数来指定变量中的代码 `$Source` 。

`Add` **BasicTest** 类的静态方法使用双冒号字符 (`::`) 来指定类的静态成员。 添加整数并显示总和。

`New-Object`Cmdlet 实例化 **BasicTest** 类的实例。 它将新对象保存在 `$BasicTestObject` 变量中。

`$BasicTestObject` 使用 `Multiply` 方法。 整数相乘并显示产品。

### 示例2：检查添加的类型

此示例使用 `Get-Member` cmdlet 检查在 `Add-Type` `New-Object` **示例 1** 中创建的和 cmdlet 的对象。

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

`Get-Member`Cmdlet 可获取添加到会话中的 **BasicTest** 类的类型和成员 `Add-Type` 。 该 `Get-Member` 命令显示它是一个派生自 **system.object** 类的 **RuntimeType** 对象。

`Get-Member`**静态** 参数获取 **BasicTest** 类的静态属性和方法。 输出显示此 `Add` 方法已包括在内。

`Get-Member`Cmdlet 将获取存储在变量中的对象的成员 `$BasicTestObject` 。
`$BasicTestObject` 是通过对 `New-Object` **BasicTest** 类使用 cmdlet 创建的。 输出显示变量的值 `$BasicTestObject` 是 **BasicTest** 类的一个实例，并且它包括一个名为的成员 `Multiply` 。

### 示例3：从程序集添加类型

此示例将程序集的类添加 `NJsonSchema.dll` 到当前会话中。

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location` 使用 **Path** 参数指定 `$PSHOME` 变量。 变量引用 DLL 文件所在的 PowerShell 安装目录。

`$AccType`变量存储使用 cmdlet 创建的对象 `Add-Type` 。 `Add-Type` 使用 **AssemblyName** 参数指定程序集的名称。 星号 (`*`) 通配符允许您获取正确的程序集，即使您不确定名称或其拼写时也是如此。 **PassThru** 参数生成对象，这些对象表示添加到会话中的类。

### 示例4：调用本机 Windows Api

此示例演示如何在 PowerShell 中调用本机 Windows Api。 `Add-Type` 使用平台调用 (P/Invoke) 机制从 PowerShell 调用中的函数 `User32.dll` 。 此示例仅适用于运行 Windows 操作系统的计算机。

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

`$Signature`变量存储函数的 c # 签名 `ShowWindowAsync` 。 为了确保生成的方法在 PowerShell 会话中可见， `public` 关键字已添加到标准签名中。 有关详细信息，请参阅 [ShowWindowAsync 函数](/windows/win32/api/winuser/nf-winuser-showwindowasync)。

`$ShowWindowAsync`变量存储通过 `Add-Type` **PassThru** 参数创建的对象。
`Add-Type`Cmdlet 将 `ShowWindowAsync` 函数作为静态方法添加到 PowerShell 会话。 该命令使用 **MemberDefinition** 参数来指定保存在变量中的方法定义 `$Signature` 。 该命令使用 **Name** 和 **Namespace** 参数来指定类的名称和命名空间。 **PassThru** 参数生成一个表示类型的对象。

`ShowWindowAsync`在命令中使用新的静态方法来最小化和还原 PowerShell 控制台。 此方法采用两个参数：窗口句柄和指定如何显示窗口的整数。

若要最大程度地减少 PowerShell 控制台，请 `ShowWindowAsync` 将 `Get-Process` cmdlet 与自动变量一起使用， `$PID` 以获取托管当前 PowerShell 会话的进程。 然后，它使用当前进程的 **MainWindowHandle** 属性和值 `2` （表示 `SW_MINIMIZE` 值）。

若要还原窗口，请将的 `ShowWindowAsync` 值 `4` 用于窗口位置，它表示 `SW_RESTORE` 值。

若要最大化窗口，请使用 `3` 表示的值 `SW_MAXIMIZE` 。

## PARAMETERS

### -AssemblyName

指定包含类型的程序集的名称。 `Add-Type` 采用指定程序集中的类型。 基于程序集名称创建类型时，此参数是必需的。

输入程序集的完整名称或简单名称（也称为 "部分名称"）。 在程序集名称中允许使用通配符。 如果输入简单名称或部分名称，则将 `Add-Type` 其解析为完整名称，然后使用完整名称加载程序集。

此参数不接受路径或文件名。 若要输入程序集动态链接库的路径 (DLL) 文件，请使用 **path** 参数。

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompilerOptions

指定用于源代码编译器的选项。 这些选项无需修改即可发送到编译器。

此参数允许指示编译器生成可执行文件、嵌入资源或设置命令行选项，如 `/unsafe` 选项。

不能在同一命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 参数。

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWarnings

忽略编译器警告。 使用此参数可防止将 `Add-Type` 编译器警告作为错误处理。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Language

指定在源代码中使用的语言。 此参数可接受的值为 **CSharp**。

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定包含类型的源代码文件或程序集 DLL 文件的路径。 与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。 不会将任何字符解释为通配符。 如果路径包括转义符，请将其括在单引号中。 单引号指示 PowerShell 不要将任何字符解释为转义序列。

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberDefinition

指定类的新属性或方法。 `Add-Type` 生成支持属性或方法所需的模板代码。

在 Windows 上，可以使用此功能在 PowerShell 中将平台调用 (P/Invoke) 调用非托管函数。

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定要创建的类的名称。 当从成员定义生成类型时，此参数是必需的。

类型名称和命名空间在一个会话中必须是唯一的。 不能卸载或更改类型。
若要更改类型的代码，必须更改名称或启动新的 PowerShell 会话。
否则，该命令将失败。

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定类型的命名空间。

如果此参数不包括在命令中，则会在 **将. microsoft.powershell.commands.newwebserviceproxy.autogeneratedtypes 和** 命名空间中创建该类型。 如果参数包含在包含空字符串值或值的命令中 `$Null` ，则将在全局命名空间中生成类型。

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAssembly

在该位置中为具有指定名称的程序集生成 DLL 文件。 输入可选的路径和文件名。 允许使用通配符。 默认情况下， `Add-Type` 仅在内存中生成程序集。

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -OutputType

指定输出程序集的输出类型。 默认情况下，不指定输出类型。 仅当命令中指定了输出程序集时，此参数才有效。 有关这些值的详细信息，请参阅 [OutputAssemblyType 枚举](/dotnet/api/microsoft.powershell.commands.outputassemblytype)。

此参数可接受的值如下所示：

- 控制台应用程序
- 库
- Windowsapplication.zip

> [!IMPORTANT]
> 在 PowerShell 7.1 `ConsoleApplication` 和不受支持的情况下， `WindowsApplication` 如果指定为 **OutputType** 参数的值，则 PowerShell 将引发一个终止错误。

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

返回表示已添加的类型的 **System.Runtime** 对象。 默认情况下，此 cmdlet 不会生成任何输出。

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

### -Path

指定包含类型的源代码文件或程序集 DLL 文件的路径。

如果提交源代码文件，则会在 `Add-Type` 文件中编译代码，并创建类型的内存中程序集。 **Path** 的值中指定的文件扩展名确定使用的编译器 `Add-Type` 。

如果提交程序集文件，则 `Add-Type` 从程序集中获取类型。 若要指定内存中程序集或全局程序集缓存，请使用 **AssemblyName** 参数。

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferencedAssemblies

指定类型所依赖的程序集。 默认情况下， `Add-Type` 引用 `System.dll` 和 `System.Management.Automation.dll` 。 除了引用默认程序集之外，还将引用你通过使用此参数指定的程序集。

从 PowerShell 6 开始， **ReferencedAssemblies** 不包括默认的 .net 程序集。 必须在传递给此参数的值中包含对它们的特定引用。

不能在同一命令中使用 **CompilerOptions** 和 **ReferencedAssemblies** 参数。

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeDefinition

指定包含类型定义的源代码。 以字符串或 here-string 的形式输入源代码或输入一个包含源代码的变量。 有关字符串的详细信息，请参阅 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)。

在类型定义中包括命名空间声明。 如果省略命名空间声明，则你的类型可能会与其他类型或其他类型的快捷方式同名，从而导致意外覆盖。 例如，如果定义了一个名为 **exception** 的类型，则使用 **exception** 作为 system.exception 的快捷 **方式的脚本将失败** 。

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsingNamespace

指定类所需的其他命名空间。 这非常类似于 c # 关键字 `Using` 。

默认情况下， `Add-Type` 引用 **系统** 命名空间。 如果使用 **MemberDefinition** 参数，则 `Add-Type` 默认情况下也会引用 **InteropServices** 命名空间。 除了引用默认命名空间之外，还将引用你通过使用 **UsingNamespace** 参数添加的命名空间。

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### 无

不能将对象向下发送到 `Add-Type` 。

## 输出

### None 或 system.string

当使用 **PassThru** 参数时，将 `Add-Type` 返回表示新类型的 **system.object** 对象。 否则，此 cmdlet 不会生成任何输出。

## 注释

你添加的类型仅存在当前会话中。 若要在所有会话中使用这些类型，请将它们添加到 PowerShell 配置文件中。 有关配置文件的详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。

类型名称和命名空间在一个会话中必须是唯一的。 不能卸载或更改类型。 如果需要更改类型的代码，则必须更改名称或启动新的 PowerShell 会话。
否则，该命令将失败。

在 Windows PowerShell 中 (版本5.1 及更低版本) ，你需要 `Add-Type` 对尚未加载的任何内容使用。 最常见的情况是，这适用于在全局程序集缓存 (GAC) 中找到的程序集。
在 PowerShell 6 及更高版本中，没有 GAC，因此 PowerShell 在中安装其自己的程序集 `$PSHome` 。
这些程序集是在请求时自动加载的，因此无需使用 `Add-Type` 来加载这些程序集。 但是， `Add-Type` 仍允许使用来允许脚本与任何 PowerShell 版本隐式兼容。

GAC 中的程序集可以按类型名称而不是按路径进行加载。 从任意路径加载程序集需要 `Add-Type` ，因为不能自动加载这些程序集。

## 相关链接

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Add-Member](Add-Member.md)

[New-Object](New-Object.md)

[OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[平台调用 (P/Invoke)](/dotnet/standard/native-interop/pinvoke)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
