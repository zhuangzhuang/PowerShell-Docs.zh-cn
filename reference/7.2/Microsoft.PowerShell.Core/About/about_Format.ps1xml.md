---
description: 从 PowerShell 6 开始，在 PowerShell 源代码中定义对象的默认视图。  你可以创建自己的 `Format.ps1xml` 文件来更改对象的显示，或为你在 PowerShell 中创建的新对象类型定义默认显示。
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: 56bac204e33c39aa6192da9e6a899f00b0a4a743
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595618"
---
# <a name="about-formatps1xml"></a>关于 Format.ps1xml

## <a name="short-description"></a>简短说明

从 PowerShell 6 开始，在 PowerShell 源代码中定义对象的默认视图。

你可以创建自己的 `Format.ps1xml` 文件来更改对象的显示，或为你在 PowerShell 中创建的新对象类型定义默认显示。

## <a name="long-description"></a>长说明

从 PowerShell 6 开始，默认视图是在 PowerShell 源代码中定义的。 Powershell `Format.ps1xml` 6 及更高版本中不存在 powershell 5.1 及更早版本中的文件。

PowerShell 源代码定义 PowerShell 控制台中对象的默认显示。 你可以创建自己的 `Format.ps1xml` 文件来更改对象的显示，或为你在 PowerShell 中创建的新对象类型定义默认显示。

当 PowerShell 显示对象时，它将使用结构化格式设置文件中的数据来确定对象的默认显示。 格式设置文件中的数据确定是在表中还是在列表中呈现对象，并确定默认情况下显示哪些属性。

格式设置只影响显示。 它不会影响向下传递管道的对象属性或传递方式。 `Format.ps1xml` 文件不能用于自定义哈希表的输出格式。

`.ps1xml`格式设置文件可以为每个对象定义四个不同的视图：

- 表
- 列表
- Wide
- 自定义

例如，将命令的输出传递 `Get-ChildItem` 给 `Format-List` 命令时， `Format-List` 使用源代码中定义的列表视图来确定如何将文件和文件夹对象显示为列表。

当格式设置文件包含一个对象的多个视图时，PowerShell 将应用找到的第一个视图。

在自定义 `Format.ps1xml` 文件中，视图由一组 XML 标记定义，这些标记描述视图的名称、可应用该视图的对象的类型、列标题和在视图正文中显示的属性。 在 `Format.ps1xml` 向用户显示数据之前，将应用文件中的格式。

## <a name="creating-new-formatps1xml-files"></a>创建新的 Format.ps1xml 文件

若要更改现有对象视图的显示格式，或添加新对象的视图，请创建自己的 `Format.ps1xml` 文件，然后将其添加到 PowerShell 会话。

若要创建 `Format.ps1xml` 文件以定义自定义视图，请使用 [Update-formatdata](xref:Microsoft.PowerShell.Utility.Get-FormatData) 和 [update-formatdata](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlet。 使用文本编辑器编辑该文件。 该文件可以保存到 PowerShell 可以访问的任何目录，例如的子目录 `$HOME` 。

若要更改当前视图的格式，请在格式设置文件中找到该视图，然后使用标记来更改视图。 若要为新的对象类型创建视图，请创建新视图，或使用现有视图作为模型。 下一节将介绍这些标记。 然后，你可以删除该文件中的所有其他视图，以使所做的更改对于检查该文件的任何人都很明显。

保存更改后，使用 [update-formatdata](xref:Microsoft.PowerShell.Utility.Update-FormatData) 将新文件添加到 PowerShell 会话。 如果希望视图优先于在内置文件中定义的视图，请使用 **PrependPath** 参数。 `Update-FormatData` 仅影响当前会话。 若要对所有未来会话进行更改，请将 `Update-FormatData` 命令添加到 PowerShell 配置文件。

### <a name="example-add-calendar-data-to-culture-objects"></a>示例：将日历数据添加到区域性对象

此示例演示如何更改 `Get-Culture` 当前 PowerShell 会话中由 cmdlet 生成的区域性对象的格式设置。 该示例中的命令将 **日历** 属性添加到区域性对象的默认表视图显示中。

若要开始，请从源代码文件中获取格式数据，并创建 `Format.ps1xml` 包含区域性对象的当前视图的文件。

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

`CultureInfo.Format.ps1xml`在任何 XML 或文本编辑器中打开文件，如 Visual Studio Code。 下面的 XML 定义 **CultureInfo** 对象的视图。

该 `CultureInfo.Format.ps1xml` 文件应类似于以下示例：

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
        <TypeName>System.Globalization.CultureInfo</TypeName>
      </ViewSelectedBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader />
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>LCID</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>DisplayName</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

通过添加一组新的标记为 **Calendar** 属性创建一个新列 `<TableColumnHeader>` 。 **Calendar** 属性的值可以很长，因此，请将值指定为45个字符 `<Width>` 。

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

使用和标记为表行中的 **日历** 添加新的列 `<TableColumnItem>` 项 `<PropertyName` ：

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

保存并关闭该文件。 使用 `Update-FormatData` 将新的格式化文件添加到当前 PowerShell 会话。

此示例使用 **PrependPath** 参数将新文件的优先顺序高于原始文件。 有关详细信息，请参阅 [update-formatdata](xref:Microsoft.PowerShell.Utility.Update-FormatData)。

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

若要测试更改，请键入 `Get-Culture` 并检查包含 **Calendar** 属性的输出。

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>Format.ps1xml 文件中的 XML

在 GitHub 上的 PowerShell 源代码存储库 [中，](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 可以找到完整的架构定义。

每个文件的 **ViewDefinitions** 部分 `Format.ps1xml` 包含 `<View>` 定义每个视图的标记。 典型的 `<View>` 标记包括以下标记：

- `<Name>` 标识视图的名称。
- `<ViewSelectedBy>` 指定应用视图的对象类型或类型。
- `<GroupBy>` 指定如何将视图中的项合并到组中。
- `<TableControl>`、 `<ListControl>` 、 `<WideControl>` 和 `<CustomControl>` 包含指定每个项的显示方式的标记。

### <a name="viewselectedby-tag"></a>ViewSelectedBy 标记

`<ViewSelectedBy>`标记可以包含 `<TypeName>` 应用该视图的每个对象类型的标记。 或者，它可以包含一个 `<SelectionSetName>` 标记，该标记引用使用标记在其他位置定义的选项集 `<SelectionSet>` 。

### <a name="groupby-tag"></a>GroupBy 标记

`<GroupBy>`标记包含一个 `<PropertyName>` 标记，该标记指定要将项分组到的对象属性。 它还包含一个 `<Label>` 标记，该标记为每个组指定一个要用作标签的字符串，或者包含一个标记 `<CustomControlName>` ，该标记用于引用在其他位置使用标记定义的自定义控件 `<Control>` 。 `<Control>`标记包含 `<Name>` 标记和 `<CustomControl>` 标记。

### <a name="tablecontroltag"></a>TableControlTag

`<TableControl>`标记通常包含 `<TableHeaders>` `<TableRowEntries>` 定义表的表头和行的格式的标记。 `<TableHeaders>`标记通常包含 `<TableColumnHeader>` 包含 `<Label>` 、 `<Width>` 和标记的标记 `<Alignment>` 。 `<TableRowEntries>`标记包含 `<TableRowEntry>` 表中每一行的标记。 `<TableRowEntry>`标记包含 `<TableColumnItems>` 标记，该标记包含 `<TableColumnItem>` 行中每个列的标记。 通常， `<TableColumnItem>` 标记包含 `<PropertyName>` 标识要在定义的位置中显示的对象属性的标记，或包含用于 `<ScriptBlock>` 计算要在位置中显示的结果的脚本代码的标记。

> [!NOTE]
> 脚本块还可用于计算结果可能有用的位置中的其他位置。

`<TableColumnItem>`标记还可以包含一个 `<FormatString>` 标记，该标记指定如何显示属性或计算结果。

### <a name="listcontrol-tag"></a>ListControl 标记

`<ListControl>`标记通常包含 `<ListEntries>` 标记。 `<ListEntries>`标记包含 `<ListEntry>` 标记。 `<ListEntry>`标记包含 `<ListItems>` 标记。 `<ListItems>`标记包含标记 `<ListItem>` ，其中包含 `<PropertyName>` 标记。 `<PropertyName>`标记指定要在列表中的指定位置显示的对象属性。 如果使用选择集定义视图选择，则 `<ListControl>` 和 `<ListEntry>` 标记还可以包含 `<EntrySelectedBy>` 一个包含一个或多个标记的标记 `<TypeName>` 。 这些 `<TypeName>` 标记指定 `<ListControl>` 用于显示标记的对象类型。

### <a name="widecontrol-tag"></a>WideControl 标记

`<WideControl>`标记通常包含 `<WideEntries>` 标记。 `<WideEntries>`标记包含一个或多个 `<WideEntry>` 标记。 `<WideEntry>`标记通常包含一个 `<PropertyName>` 标记，该标记指定要在视图中的指定位置显示的属性。 `<PropertyName>`标记可以包含一个 `<FormatString>` 标记，该标记指定如何显示属性。

### <a name="customcontrol-tag"></a>CustomControl 标记

`<CustomControl>`标记允许使用脚本块定义格式。 `<CustomControl>`标记通常包含 `<CustomEntries>` 包含多个标记的标记 `<CustomEntry>` 。 每个 `<CustomEntry>` 标记都包含一个 `<CustomItem>` 标记，该标记可包含用于指定视图中指定位置的内容和格式的各种标记，包括 `<Text>` 、、 `<Indentation>` `<ExpressionBinding>` 和 `<NewLine>` 标记。

## <a name="tracing-formatps1xml-file-use"></a>跟踪 Format.ps1xml 文件使用

若要检测文件的加载或应用中的错误 `Format.ps1xml` ，请使用 `Trace-Command` cmdlet，并将以下任何格式的组件用作 **Name** 参数的值：

- FormatFileLoading
- FormatViewBinding

有关详细信息，请参阅 [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) 和 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)。

## <a name="signing-a-formatps1xml-file"></a>对 Format.ps1xml 文件进行签名

若要保护文件的用户 `Format.ps1xml` ，请使用数字签名对文件进行签名。 有关详细信息，请参阅 [about_Signing](about_Signing.md)。

## <a name="sample-xml-for-a-format-table-custom-view"></a>Format-Table 自定义视图的示例 XML

下面的 XML 示例 `Format-Table` 为创建的 **DirectoryInfo** 和 **FileInfo** 对象创建自定义视图 `Get-ChildItem` 。 自定义视图命名为 **mygciview** ，并将 **CreationTime** 列添加到表中。

若要创建自定义视图，请使用 `Get-FormatData` 和 `Export-FormatData` cmdlet 来生成 `.ps1xml` 文件。 然后，编辑 `.ps1xml` 文件，为自定义视图创建代码。 该 `.ps1xml` 文件可存储在 PowerShell 可以访问的任何目录中。 例如，的子目录 `$HOME` 。

`.ps1xml`创建文件后，使用 `Update-FormatData` cmdlet 在当前 PowerShell 会话中包含该视图。 或者，如果需要所有 PowerShell 会话中提供的视图，请将更新命令添加到 PowerShell 配置文件中。

在此示例中，自定义视图必须使用表格格式，否则将 `Format-Table` 失败。

`Format-Table`与 **View** 参数一起使用，以指定自定义视图的名称、 **Mygciview**，并使用 **CreationTime** 列设置该表输出的格式。 有关如何运行该命令的示例，请参阅 [格式表](xref:Microsoft.PowerShell.Utility.Format-Table)。

> [!NOTE]
> 尽管可以从源代码获取格式设置 XML 以创建自定义视图，但可能需要更多的开发才能获得所需的结果。

在下面的 `Get-FormatData` 命令中，可以使用 **PowerShellVersion** 参数的替代方法来确保返回所有本地格式设置信息。 使用 `-PowerShellVersion $PSVersionTable.PSVersion` 而不是特定的 PowerShell 版本。

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Length</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>请参阅

[Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[格式架构 XML 参考](/powershell/scripting/developer/format/format-schema-xml-reference)

[Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[编写 PowerShell 格式设置文件](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
