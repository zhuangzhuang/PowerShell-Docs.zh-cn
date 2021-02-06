---
description: 介绍如何使用 `Types.ps1xml` 文件来扩展在 PowerShell 中使用的对象的类型。
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1xml
ms.openlocfilehash: 9a87394631d3318f3fb3f4b2a0cb2ab8d25408d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596220"
---
# <a name="about-typesps1xml"></a>关于 Types.ps1xml

## <a name="short-description"></a>简短说明
介绍如何使用 `Types.ps1xml` 文件来扩展在 PowerShell 中使用的对象的类型。

## <a name="long-description"></a>长说明

扩展类型数据定义了 PowerShell 中对象类型的 "成员" )  ( 的附加属性和方法。 可通过两种方法将扩展类型数据添加到 PowerShell 会话。

- `Types.ps1xml` 文件：定义扩展类型数据的 XML 文件。
- `Update-TypeData`：一个 cmdlet，用于重新加载 `Types.ps1xml` 文件并为当前会话中的类型定义扩展数据。

本主题描述 `Types.ps1xml` 文件。 有关使用 `Update-TypeData` cmdlet 向当前会话添加动态扩展类型数据的详细信息，请参阅 [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)。

## <a name="about-extended-type-data"></a>关于扩展类型数据

扩展类型数据定义了 PowerShell 中对象类型的 "成员" )  ( 的附加属性和方法。 你可以扩展 PowerShell 支持的任何类型，并使用已添加的属性和方法，其方式与你使用在对象类型上定义的属性相同。

例如，PowerShell 会将 **DateTime** 属性添加到所有 `System.DateTime` 对象，如 `Get-Date` cmdlet 返回的对象。

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

不会在 [system.web](/dotnet/api/system.datetime)结构的描述中找到 **datetime** 属性，因为 powershell 会添加属性，它仅在 PowerShell 中可见。

PowerShell 在内部定义一组默认的扩展类型。 此类型信息将在启动时在每个 PowerShell 会话中加载。 **DateTime** 属性是此默认集的一部分。 在 PowerShell 6 之前，类型定义存储 `Types.ps1xml` 在 powershell 安装目录中 (`$PSHOME`) 。

## <a name="adding-extended-type-data-to-powershell"></a>将扩展类型数据添加到 PowerShell

PowerShell 会话中有三个扩展类型数据源。

- 由 PowerShell 定义并自动加载到每个 PowerShell 会话中。 从 PowerShell 6 开始，此信息编译到 PowerShell 中，不再在文件中发送 `Types.ps1xml` 。

- 模块 `Types.ps1xml` 导入到当前会话中时将加载模块导出的文件。

- 使用 cmdlet 定义的扩展类型数据 `Update-TypeData` 仅添加到当前会话中。 它不保存在文件中。

在会话中，三个源中的扩展类型数据以相同的方式应用于对象，并可用于指定类型的所有对象。

## <a name="the-typedata-cmdlets"></a>Update-typedata cmdlet

以下 cmdlet 包含在 PowerShell 3.0 和更高版本的 **Microsoft. Utility** 模块中。

- `Get-TypeData`：获取当前会话中的扩展类型数据。
- `Update-TypeData`：重新加载 `Types.ps1xml` 文件。 将扩展类型数据添加到当前会话中。
- `Remove-TypeData`：从当前会话中删除扩展类型数据。

有关这些 cmdlet 的详细信息，请参阅每个 cmdlet 的帮助主题。

## <a name="built-in-typesps1xml-files"></a>内置 Types.ps1xml 文件

`Types.ps1xml`目录中的文件 `$PSHOME` 将自动添加到每个会话中。

`Types.ps1xml`Powershell 安装目录中的文件 (`$PSHOME`) 是基于 XML 的文本文件，可让你向 PowerShell 中使用的对象添加属性和方法。 PowerShell 具有 `Types.ps1xml` 将几个元素添加到 .net 类型的内置文件，但你可以创建其他 `Types.ps1xml` 文件来进一步扩展这些类型。

例如，默认情况下，数组对象 (`System.Array`) 的 **Length** 属性列出数组中对象的数量。 但是，因为名称 **长度** 并不清楚地描述属性，所以 PowerShell 会添加一个别名属性 **，其中显示相同的值** 。 下面的 XML 将 **Count** 属性添加到该 `System.Array` 类型。

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

若要获取新的 **AliasProperty**，请 `Get-Member` 在任何数组上使用命令，如以下示例中所示。

```powershell
Get-Member -InputObject (1,2,3,4)
```

该命令将返回以下结果。

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

因此，可以在 PowerShell 中使用数组的 **Count** 属性或 **Length** 属性。 例如：

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a>创建新的 Types.ps1xml 文件

`.ps1xml`随 PowerShell 一起安装的文件已进行数字签名，以防止篡改，因为格式设置可以包括脚本块。 因此，若要将属性或方法添加到 .NET 类型，请创建自己的 `Types.ps1xml` 文件，然后将其添加到 PowerShell 会话。

若要创建新文件，请从复制现有 `Types.ps1xml` 文件开始。 新文件可以具有任何名称，但它必须具有 `.ps1xml` 文件扩展名。 可以将新文件放在 PowerShell 可访问的任何目录中，但将文件放在 PowerShell 安装目录中 (`$PSHOME`) 或安装目录的子目录中。

保存新文件后，使用 `Update-TypeData` cmdlet 将新文件添加到 PowerShell 会话。 如果你希望你的类型优先于定义的内置类型，请使用 cmdlet 的 **PrependData** 参数 `Update-TypeData` 。 `Update-TypeData` 仅影响当前会话。 若要对所有未来的会话进行更改，请导出控制台，或将 `Update-TypeData` 命令添加到 PowerShell 配置文件。

## <a name="typesps1xml-and-add-member"></a>Types.ps1xml 和 Add-Member

`Types.ps1xml`文件将属性和方法添加到受影响的 PowerShell 会话中指定 .net 类型的对象的所有实例。 但是，如果需要将属性或方法仅添加到对象的一个实例，请使用 `Add-Member` cmdlet。

有关详细信息，请参阅 [添加成员](xref:Microsoft.PowerShell.Utility.Add-Member)。

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a>示例：将 Age 成员添加到 FileInfo 对象

此示例演示如何将 **Age** 属性添加到 **FileInfo** 对象。 文件的保留时间是其创建时间和当前时间之间的差异（以天为单位）。

因为 **Age** 属性是通过使用脚本块进行计算的，所以请查找一个标记，将其 `<ScriptProperty>` 用作新的 **Age** 属性的模型。

将以下 XML 代码保存到文件 `$PSHOME\MyTypes.ps1xml` 。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

运行 `Update-TypeData` 将新文件添加 `Types.ps1xml` 到当前会话。 该命令使用 **PrependData** 参数将新文件置于比原始定义更高的优先顺序。

有关的详细信息 `Update-TypeData` ，请参阅 [update-typedata](xref:Microsoft.PowerShell.Utility.Update-TypeData)。

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

若要测试更改，请运行 `Get-ChildItem` 命令以获取目录中的 PowerShell.exe 文件 `$PSHOME` ，然后通过管道将该文件传递给 `Format-List` cmdlet 以列出该文件的所有属性。 更改后， **Age** 属性将显示在列表中。

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a>Types.ps1xml 文件中的 XML

在 GitHub 上的 PowerShell 源代码存储库 [中，](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) 可以找到完整的架构定义。

`<Types>`标记包含在文件中定义的所有类型。 应该只有一个 `<Types>` 标记。

文件中提到的每个 .NET 类型都应由 `<Type>` 标记表示。

类型标记必须包含以下标记：

`<Name>`：包含受影响的 .NET 类型的名称。

`<Members>`：包含为 .NET 类型定义的新属性和方法的标记。

以下任何成员标记可以位于 `<Members>` 标记内。

`<AliasProperty>`：定义现有属性的新名称。

`<AliasProperty>`标记必须有一个 `<Name>` 标记，该标记指定新属性的名称和 `<ReferencedMemberName>` 指定现有属性的标记。

例如， **Count** alias 属性是数组对象的 **Length** 属性的别名。

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

`<CodeMethod>`：引用 .NET 类的静态方法。

`<CodeMethod>`标记必须有一个 `<Name>` 指定新方法的名称的标记和一个 `<GetCodeReference>` 标记，该标记指定在其中定义方法的代码。

例如，对象的 **Mode** 属性 `System.IO.DirectoryInfo` 是在 PowerShell FileSystem 提供程序中定义的代码属性。

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<CodeProperty>`：引用 .NET 类的静态方法。

`<CodeProperty>`标记必须有一个 `<Name>` 指定新属性的名称的标记和一个 `<GetCodeReference>` 标记，该标记指定在其中定义属性的代码。

例如，对象的 **Mode** 属性 `System.IO.DirectoryInfo` 是在 PowerShell FileSystem 提供程序中定义的代码属性。

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<MemberSet>`：定义)  (属性和方法的成员的集合。

`<MemberSet>`标记出现在主标记中 `<Members>` 。 标记必须围绕成员集的名称加上一个 `<Name>` 标记，并在 `<Members>` 集合中包含成员 (属性和方法) 的辅助标记。 创建属性 (的任何标记（如 `<NoteProperty>` 或 `<ScriptProperty>`) 或 (如或) 的方法） `<Method>` `<ScriptMethod>` 都可以是集的成员。

在 `Types.ps1xml` 文件中， `<MemberSet>` 标记用于在 PowerShell 中定义 .net 对象的默认视图。 在这种情况下，成员集的名称 (标记) 内的值 `<Name>` 始终是 **PsStandardMembers** 的，并且 () 标记值的属性的名称 `<Name>` 是以下值之一：

- `DefaultDisplayProperty`：对象的单个属性。

- `DefaultDisplayPropertySet`：对象的一个或多个属性。

- `DefaultKeyPropertySet`：对象的一个或多个键属性。 键属性标识属性值的实例，如会话历史记录中项目的 ID。

例如，下面的 XML 定义了服务的默认显示 (`System.ServiceProcess.ServiceController` 对象) 由 `Get-Service` cmdlet 返回。 它定义了一个名为 **PsStandardMembers** 的成员集，其中包含具有 **Status**、 **Name** 和 **DisplayName** 属性的默认属性集。

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<Method>`：引用基础对象的本机方法。

`<Methods>`：对象的方法的集合。

`<NoteProperty>`：定义具有静态值的属性。

`<NoteProperty>`标记必须有一个 `<Name>` 标记，该标记指定新属性的名称和 `<Value>` 指定属性值的标记。

例如，以下 XML 将为 **DirectoryInfo** 对象创建 **Status** 属性。 **Status** 属性的值始终为 **Success**。

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

`<ParameterizedProperty>`：采用参数并返回值的属性。

`<Properties>`：对象的属性的集合。

`<Property>`：基对象的一个属性。

`<PropertySet>`：定义对象的属性的集合。

`<PropertySet>`标记必须有一个 `<Name>` 标记，该标记指定属性集的名称和 `<ReferencedProperty>` 指定属性的标记。 属性的名称括在 `<Name>` 标记中。

在中 `Types.ps1xml` ， `<PropertySet>` 使用标记来定义对象默认显示的属性集。 可以通过标记的标记中的值 **PsStandardMembers** 标识默认显示 `<Name>` `<MemberSet>` 。

例如，下面的 XML 为对象创建了一个 **状态** 属性 `System.IO.DirectoryInfo` 。 **Status** 属性的值始终为 **Success**。

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<ScriptMethod>`：定义一个方法，其值为脚本的输出。

`<ScriptMethod>`标记必须有一个 `<Name>` 标记，该标记指定新方法的名称，并具有一个标记，该标记包含 `<Script>` 返回方法结果的脚本块。

例如， `ConvertToDateTime` `ConvertFromDateTime` () 的管理对象的和方法 `System.System.Management.ManagementObject` 是使用 `ToDateTime` 类的和静态方法的脚本方法 `ToDmtfDateTime` `System.Management.ManagementDateTimeConverter` 。

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

`<ScriptProperty>`：定义一个属性，其值为脚本的输出。

`<ScriptProperty>`标记必须有一个 `<Name>` 标记，该标记指定新属性的名称，以及一个包含 `<GetScriptBlock>` 返回属性值的脚本块的标记。

例如， **FileInfo** 对象的 **VersionInfo** 属性是一个脚本属性，该属性是使用 **GetVersionInfo** 静态方法的 **FullName** 属性（ **FileVersionInfo** 对象）生成的。

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

有关详细信息，请参阅 [Windows PowerShell 软件开发工具包 (SDK) ](/powershell/scripting/developer/windows-powershell)。

## <a name="update-typedata"></a>Update-TypeData

若要将 `Types.ps1xml` 文件加载到 PowerShell 会话，请运行 `Update-TypeData` cmdlet。 如果希望文件中的类型优先于内置文件中的类型 `Types.ps1xml` ，请添加的 **PrependData** 参数 `Update-TypeData` 。 `Update-TypeData` 仅影响当前会话。 若要对所有未来的会话进行更改，请导出会话，或者将 `Update-TypeData` 命令添加到 PowerShell 配置文件。

在属性中发生的异常或通过将属性添加到 `Update-TypeData` 命令中时，不会将错误报告给 `StdErr` 。 这是为了取消显示在格式设置和输出期间在许多常见类型中发生的异常。 如果你正在获取 .NET 属性，则可以通过使用方法语法来解决禁止显示异常的情况，如以下示例中所示：

```powershell
"hello".get_Length()
```

请注意，方法语法仅可用于 .NET 属性。 通过运行 cmdlet 添加的属性 `Update-TypeData` 不能使用方法语法。

## <a name="signing-a-typesps1xml-file"></a>对 Types.ps1xml 文件进行签名

若要保护文件的用户 `Types.ps1xml` ，可以使用数字签名对文件进行签名。 有关详细信息，请参阅 [about_Signing](about_Signing.md)。

## <a name="see-also"></a>请参阅

[about_Signing](about_Signing.md)

[Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)

[Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Get-TypeData](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[Remove-TypeData](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)

