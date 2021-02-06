---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595416"
---
# New-Object

## 摘要
创建 Microsoft .NET Framework 或 COM 对象的实例。

## SYNTAX

### Net（默认值）

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### Com

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## DESCRIPTION

`New-Object`Cmdlet 可创建 .NET Framework 或 COM 对象的实例。

可以指定 .NET Framework 类的类型或 COM 对象的 ProgID。 默认情况下，键入 .NET Framework 类的完全限定名后，此 cmdlet 将返回对该类的实例的引用。 若要创建 COM 对象的实例，请使用 **ComObject** 参数并将对象的 ProgID 指定为其值。

## 示例

### 示例1：创建一个 System.web 对象

此示例使用 "1.2.3.4" 字符串作为构造函数创建一个 **system.web** 对象。

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### 示例2：创建 Internet Explorer COM 对象

此示例创建表示 Internet Explorer 应用程序的 COM 对象的两个实例。 第一个实例使用 **属性** 参数 hash 表调用 **Navigate2** 方法，并将该对象的 **Visible** 属性设置为， `$True` 以使该应用程序可见。
第二个实例获取的结果与单独的命令相同。

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### 示例3：使用 Strict 参数生成非终止错误

此示例演示添加 **Strict** 参数会导致 `New-Object` cmdlet 在 COM 对象使用互操作程序集时生成非终止错误。

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### 示例4：创建 COM 对象来管理 Windows 桌面

此示例显示如何创建和使用 COM 对象来管理 Windows 桌面。

第一个命令使用 cmdlet 的 **ComObject** 参数 `New-Object` 创建具有 **Shell** 的 COM 对象。 它将生成的对象存储在 `$ObjShell` 变量中。 第二个命令将 `$ObjShell` 变量传递给 `Get-Member` cmdlet，后者显示 COM 对象的属性和方法。 在方法中，是 **ToggleDesktop** 方法。 第三个命令调用对象的 **ToggleDesktop** 方法来最小化桌面上打开的窗口。

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### 示例5：将多个自变量传递给构造函数

此示例演示如何使用采用多个参数的构造函数创建对象。 使用 **ArgumentList** 参数时，必须将参数放入数组中。

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

PowerShell 将数组的每个成员绑定到构造函数的参数。

> [!NOTE]
> 此示例使用参数展开以提高可读性。 有关详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

### 示例6：调用采用数组作为单个参数的构造函数

此示例演示如何使用构造函数创建一个对象，该对象采用作为数组或集合的参数。 数组参数必须放入到另一个数组中。

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

在此示例中，第一次尝试创建对象时失败。 PowerShell 尝试将三个成员绑定 `$array` 到构造函数的参数，但构造函数不采用三个参数。 包装 `$array` 在另一个数组中会阻止 PowerShell 尝试将的三个成员绑定 `$array` 到构造函数的参数。

## PARAMETERS

### -ArgumentList

指定要传递给 .NET Framework 类的构造函数的参数数组。 如果构造函数采用单个参数作为数组，则必须将该参数包装在另一个数组中。 例如：

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

有关 **ArgumentList** 行为的详细信息，请参阅 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)。

**ArgumentList** 的别名是 **Args**。

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComObject

指定 COM 对象的编程标识符 (ProgID)。

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Property

设置新对象的属性值并调用其方法。

输入哈希表，其中键为属性或方法的名称，值为属性值或方法参数。 `New-Object` 创建对象并设置每个属性值，并按它们在哈希表中出现的顺序调用每个方法。

如果新的对象派生自 **PSObject** 类，并且指定了对象上不存在的属性，则会 `New-Object` 将指定的属性作为 NoteProperty 添加到该对象。 如果对象不是 **PSObject**，则该命令将生成一个非终止错误。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Strict

指示当你尝试创建的 COM 对象使用互操作程序集时，该 cmdlet 将生成一个非终止错误。 此功能可将实际的 COM 对象与具有 COM 可调用包装器的 .NET Framework 对象区分开来。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

指定 .NET Framework 类的完全限定名称。 不能同时指定 **TypeName** 参数和 **ComObject** 参数。

```yaml
Type: System.String
Parameter Sets: Net
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

不能通过管道将输入传递给此 cmdlet。

## 输出

### 对象

`New-Object` 返回创建的对象。

## 注释

- `New-Object` 提供 VBScript CreateObject 函数最常使用的功能。 `Set objShell = CreateObject("Shell.Application")`可在 PowerShell 中将 VBScript 中的语句转换为 `$objShell = New-Object -COMObject "Shell.Application"` 。
- `New-Object` 通过从命令行和脚本内轻松处理 .NET Framework 的对象，扩展了 Windows 脚本宿主环境中提供的功能。

## 相关链接

[about_Object_Creation](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[Compare-Object](Compare-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Tee-Object](Tee-Object.md)

