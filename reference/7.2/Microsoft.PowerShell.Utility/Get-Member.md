---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-member?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Member
ms.openlocfilehash: 27e938b0264403d67066bb489a3b8c0870a7e661
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598248"
---
# Get-Member

## 摘要
获取对象的属性和方法。

## SYNTAX

```
Get-Member [-InputObject <PSObject>] [[-Name] <String[]>] [-MemberType <PSMemberTypes>]
 [-View <PSMemberViewTypes>] [-Static] [-Force] [<CommonParameters>]
```

## DESCRIPTION

`Get-Member`Cmdlet 将获取对象的成员、属性和方法。

若要指定对象，请使用 **InputObject** 参数或通过管道将对象传递给 `Get-Member` 。 若要获取有关静态成员的信息，类的成员而不是实例的成员，请使用 **静态** 参数。 若要仅获取特定类型的成员，例如 **NoteProperties**，请使用 **MemberType** 参数。

## 示例

### 示例1：获取进程对象的成员

此命令显示 cmdlet 生成的服务对象的属性和方法 `Get-Service` 。

由于该 `Get-Member` 命令部分没有任何参数，因此它使用参数的默认值。 默认情况下，不 `Get-Member` 会获取静态成员或内部成员。

```powershell
Get-Service | Get-Member
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, System.EventArgs)
Close                     Method        void Close()
Continue                  Method        void Continue()
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.ServiceControllerSt...
BinaryPathName            Property      System.String {get;set;}
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DelayedAutoStart          Property      System.Boolean {get;set;}
DependentServices         Property      System.ServiceProcess.ServiceController[] DependentServices {get;}
Description               Property      System.String {get;set;}
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle ServiceHandle {get;}
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] ServicesDependedOn {get;}
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType {get;}
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartType {get;}
StartupType               Property      Microsoft.PowerShell.Commands.ServiceStartupType {get;set;}
Status                    Property      System.ServiceProcess.ServiceControllerStatus Status {get;}
UserName                  Property      System.String {get;set;}
ToString                  ScriptMethod  System.Object ToString();
```

### 示例2：获取服务对象的成员

此示例获取由 cmdlet 检索的服务对象)  (属性和方法的所有成员 `Get-Service` ，包括内部成员（例如 **PSBase**、 **PSObject**）以及 **get_** 和 **set_** 方法。

```powershell
Get-Service | Get-Member -Force
(Get-Service Schedule).PSBase
```

该 `Get-Member` 命令使用 **Force** 参数将对象的内部成员和编译器生成的成员添加到显示中。 你可以以与使用对象的改写方法相同的方式使用这些属性和方法。 第二个命令显示如何显示 Schedule 服务的 PSBase 属性的值。

### 示例3：获取服务对象的扩展成员

此示例获取使用文件或 cmdlet 扩展的服务对象的方法和属性 `Types.ps1xml` `Add-Member` 。

```powershell
Get-Service | Get-Member -View Extended
```

```Output
   TypeName: System.Service.ServiceController#StartupType

Name             MemberType    Definition
----             ----------    ----------
Name             AliasProperty Name = ServiceName
RequiredServices AliasProperty RequiredServices = ServicesDependedOn
ToString         ScriptMethod  System.Object ToString();
```

该 `Get-Member` 命令使用 **View** 参数仅获取服务对象的扩展成员。 在这种情况下，扩展成员是 **Name** 属性，它是 **ServiceName** 属性的别名属性。

### 示例4：获取事件日志对象的脚本属性

此示例获取事件查看器中系统日志中的事件日志对象的脚本属性。

```powershell
Get-WinEvent -LogName System -MaxEvents 1 | Get-Member -MemberType NoteProperty
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.EventLogRecord

Name    MemberType   Definition
----    ----------   ----------
Message NoteProperty string Message=The machine-default permission settings do not grant Local ...
```

**MemberType** 参数仅获取值为的对象的 `NoteProperty` **MemberType** 属性。

命令返回 **system.diagnostics.eventing.reader.eventlogrecord** 对象的 **消息** 属性。

### 示例5：获取具有指定属性的对象

此示例从 cmdlet 列表的输出中获取具有 **MachineName** 属性的对象。

`$list`变量包含要评估的 cmdlet 列表。 **Foreach** 语句调用每个命令并将结果发送到 `Get-Member` 。 **Name** 参数将结果限制 `Get-Member` 为具有名称 **MachineName** 的成员。

```powershell
$list = "Get-Process", "Get-Service", "Get-Culture", "Get-PSDrive", "Get-ExecutionPolicy"
foreach ($cmdlet in $list) {& $cmdlet | Get-Member -Name MachineName}
```

```Output
   TypeName: System.Diagnostics.Process

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;}

   TypeName: System.Service.ServiceController#StartupType

Name        MemberType Definition
----        ---------- ----------
MachineName Property   string MachineName {get;set;}
```

结果显示仅处理对象和服务对象具有 **MachineName** 属性。

### 示例6：获取数组的成员

此示例演示如何查找对象数组的成员。 当你将对象的管道和数组传递给时 `Get-Member` ，该 cmdlet 将为数组中的每个唯一对象类型返回成员列表。
如果使用 **InputObject** 参数传递数组，则会将该数组视为单个对象。

```powershell
$array = @(1,'hello')
$array | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType Definition
----        ---------- ----------
CompareTo   Method     int CompareTo(System.Object value), int CompareTo(int value), int ICompar...
Equals      Method     bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int...
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
GetTypeCode Method     System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method     bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method     byte IConvertible.ToByte(System.IFormatProvider provider)
...

   TypeName: System.String

Name                 MemberType            Definition
----                 ----------            ----------
Clone                Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo            Method                int CompareTo(System.Object value), int CompareTo(str...
Contains             Method                bool Contains(string value), bool Contains(string val...
CopyTo               Method                void CopyTo(int sourceIndex, char[] destination, int ...
EndsWith             Method                bool EndsWith(string value), bool EndsWith(string val...
EnumerateRunes       Method                System.Text.StringRuneEnumerator EnumerateRunes()
Equals               Method                bool Equals(System.Object obj), bool Equals(string va...
GetEnumerator        Method                System.CharEnumerator GetEnumerator(), System.Collect...
GetHashCode          Method                int GetHashCode(), int GetHashCode(System.StringCompa...
...
```

```powershell
Get-Member -InputObject $array
```

```Output
   TypeName: System.Object[]

Name           MemberType            Definition
----           ----------            ----------
Add            Method                int IList.Add(System.Object value)
Address        Method                System.Object&, System.Private.CoreLib, Version=4.0.0.0, Cu...
Clear          Method                void IList.Clear()
Clone          Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo      Method                int IStructuralComparable.CompareTo(System.Object other, Sy...
...
```

`$array`变量包含 **Int32** 对象和 **字符串** 对象，如将数组输送到时所见 `Get-Member` 。 当 `$array` 使用 **InputObject** 参数传递时，将 `Get-Member` 返回 **对象 []** 类型的成员。

### 示例7：确定可以设置的对象属性

此示例演示如何确定对象的哪个属性可更改。

```powershell
$File = Get-Item c:\test\textFile.txt
$File.PSObject.Properties | Where-Object isSettable | Select-Object -Property Name
```

```Output
Name
----
PSPath
PSParentPath
PSChildName
PSDrive
PSProvider
PSIsContainer
IsReadOnly
CreationTime
CreationTimeUtc
LastAccessTime
LastAccessTimeUtc
LastWriteTime
LastWriteTimeUtc
Attributes
```

## PARAMETERS

### -Force

将内部成员和编译器生成的 **get_** 和 **set_** 方法添加到显示中。
以下列表描述了在使用 **Force** 参数时添加的属性：

- **PSBase**：不带扩展名或调整的 .net 对象的原始属性。 这些是为对象类定义的属性。
- **PSAdapted**。 PowerShell 扩展类型系统中定义的属性和方法。
- **PSExtended**。 在文件中添加的属性和方法， `Types.ps1xml` 或者使用 `Add-Member` cmdlet。
- **PSObject**。 将基对象转换为 PowerShell **PSObject** 对象的适配器。
- **PSTypeNames**。 描述该对象的对象类型列表，以特异性排序。 设置对象的格式时，PowerShell 会在 `Format.ps1xml` powershell 安装目录中的文件中搜索类型 (`$PSHOME`) 。 它使用它找到的第一个类型的格式设置定义。

默认情况下，将 `Get-Member` 在所有视图中获取这些属性（ **Base** 和 **改编** 除外），但不会显示它们。

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

### -InputObject

指定要检索其成员的对象。

使用 **InputObject** 参数不同于将对象传递给 `Get-Member` 。 不同之处如下：

- 当你通过管道将对象集合传递给时 `Get-Member` ，将 `Get-Member` 获取集合中单个对象的成员，例如字符串数组中的每个字符串的属性。
- 使用 **InputObject** 提交对象集合时，将 `Get-Member` 获取集合的成员，例如字符串数组中数组的属性。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MemberType

指定此 cmdlet 获取的成员类型。 默认值是 **All**。

此参数的可接受值为：

- AliasProperty
- CodeProperty
- 属性
- NoteProperty
- ScriptProperty
- 属性
- PropertySet
- 方法
- CodeMethod
- ScriptMethod
- 方法
- ParameterizedProperty
- 集
- 事件
- 动态
- 全部

有关这些值的信息，请参阅 [PSMemberTypes 枚举](/dotnet/api/system.management.automation.psmembertypes)。

并非所有对象都具有每种类型的成员。 如果指定了对象不具有的成员类型，则 PowerShell 将返回 null 值。

若要获取成员的相关类型，例如所有扩展成员，请使用 **View** 参数。 如果将 **MemberType** 参数与 **Static** 或 **View** 参数一起使用，则将 `Get-Member` 获取同时属于这两个集的成员。

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

指定该对象的一个或多个属性或方法的名称。 `Get-Member` 仅获取指定的属性和方法。

如果将 **Name** 参数与 **MemberType**、 **View** 或 **Static** 参数一起使用，则 `Get-Member` 仅获取满足所有参数的条件的成员。

若要按名称获取静态成员，请将 **static** 参数与 **name** 参数一起使用。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Static

指示此 cmdlet 仅获取对象的静态属性和方法。 在对象的类上定义的静态属性和方法，而不是在类的任何特定实例上。

如果将 **Static** 参数与 **view** 参数一起使用，则将忽略 **view** 参数。
如果将 **Static** 参数与 **MemberType** 参数一起使用，则 `Get-Member` 仅获取属于这两个集的成员。

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

### -View

指定此 cmdlet 仅获取特定类型的属性和方法。 指定一个或多个值。 默认 **值为 "** 已 **扩展**"。

此参数的可接受值为：

- Base。 仅获取 .NET 对象的原始属性和方法， (不带扩展名或适配) 。
- 改写. 仅获取 PowerShell 扩展类型系统中定义的属性和方法。
- 扩展。 仅获取在文件中添加的属性和方法， `Types.ps1xml` 或使用 `Add-Member` cmdlet。
- 全部。 在基本、改写和扩展视图中获取成员。

**View** 参数确定检索的成员，而不仅仅是这些成员的显示。

若要获取特定成员类型，例如脚本属性，请使用 **MemberType** 参数。 如果在同一命令中使用 **MemberType** 和 **View** 参数，将 `Get-Member` 获取同时属于这两个集的成员。 如果在同一命令中使用 **Static** 和 **View** 参数，则将忽略 **View** 参数。

```yaml
Type: System.Management.Automation.PSMemberViewTypes
Parameter Sets: (All)
Aliases:
Accepted values: Extended, Adapted, Base, All

Required: False
Position: Named
Default value: Adapted, Extended
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

可以通过管道将任何对象传递给 `Get-Member` 。

## 输出

### Microsoft.PowerShell.Commands.MemberDefinition

`Get-Member` 为其获取的每个属性或方法返回一个对象。

## 注释

可以通过使用 **InputObject** 参数或通过管道将对象（前面加逗号）传递到来获取有关集合对象的信息 `Get-Member` 。

可以 `$This` 在定义新属性和方法的值的脚本块中使用自动变量。 `$This`变量引用要向其中添加属性和方法的对象的实例。 有关变量的详细信息 `$This` ，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。

如果传递一个表示 _类型_ 的对象（如类型文本，如 `[int]` ），则 `Get-Member` 返回有关该类型的信息 `[System.RuntimeType]` 。 但是，当你使用 **静态** 参数时，将 `Get-Member` 返回实例所表示的特定类型的静态成员 `System.RuntimeType` 。

## 相关链接

[Add-Member](Add-Member.md)

