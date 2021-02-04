---
ms.date: 09/13/2016
ms.topic: reference
title: 格式设置文件概述
description: 格式设置文件概述
ms.openlocfilehash: 769a86d274ef3b35a322d76e2f03cb551d9204a1
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879130"
---
# <a name="formatting-file-overview"></a>格式设置文件概述

 (cmdlet、函数和脚本的命令返回的对象的显示格式) 是使用格式设置文件 ( # B0 xml 文件) 来定义的。 PowerShell 提供其中几个文件，用于定义由 PowerShell 提供的命令返回的对象的显示格式，如 cmdlet 返回的[system.object](/dotnet/api/System.Diagnostics.Process)对象。 `Get-Process` 但是，您还可以创建自己的自定义格式设置文件来覆盖默认的显示格式，也可以编写自定义格式设置文件来定义由您自己的命令返回的对象的显示。

> [!IMPORTANT]
> 格式化文件不确定返回到管道的对象的元素。 当对象返回到管道时，即使某些成员未显示，该对象的所有成员仍可用。

PowerShell 使用这些格式设置文件中的数据来确定所显示的内容以及显示的数据的格式。 显示的数据可以包括对象的属性或脚本的值。 如果希望显示某个对象的属性中不能直接使用的值，例如，添加对象的两个属性的值，然后将 sum 显示为一段数据，则可以使用脚本。 通过为要显示的对象定义视图来完成显示数据的格式设置。 您可以为每个对象定义一个视图，可以为多个对象定义一个视图，也可以为同一对象定义多个视图。 您可以定义的视图数没有限制。

## <a name="common-features-of-formatting-files"></a>格式化文件的常用功能

每个格式化文件都可以定义以下组件，这些组件可在文件定义的所有视图之间共享：

- 默认配置设置，例如，如果数据的长度超过列的宽度，则在表的行中显示的数据是否将显示在下一行。 有关这些设置的详细信息，请参阅 [定义常用配置设置](./defining-common-configuration-features.md)。

- 可由任何格式设置文件视图显示的对象集。 有关这些集 (称为 *选择集*) 的详细信息，请参阅 [定义对象集](./defining-selection-sets.md)。

- 格式设置文件的所有视图都可以使用的公共控件。 控件使您可以更好地控制数据的显示方式。 有关控件的详细信息，请参阅 [定义自定义控件](./creating-custom-controls.md)。

## <a name="formatting-views"></a>格式视图

格式视图可按表格式显示对象、列表格式、宽格式和自定义格式。 大多数情况下，每个格式设置定义由一组描述视图的 XML 标记来描述。 每个视图都包含视图的名称、使用该视图的对象和视图的元素，例如表视图的列和行信息。

表视图在一个或多个列中列出对象或脚本块值的属性。 每个列表示对象的一个属性或一个脚本值。 您可以定义显示对象的所有属性的表视图、对象属性的子集或属性和脚本值的组合。 表中的每一行都表示一个返回的对象。 创建表视图非常类似于通过管道将对象传递给 `Format-Table` cmdlet。 有关此视图的详细信息，请参阅 [表视图](./creating-a-table-view.md)。

列表视图在单个列中列出对象或脚本值的属性。 列表中的每一行都显示一个可选标签或属性名称，后跟属性或脚本的值。 创建列表视图非常类似于通过管道将对象传递给 `Format-List` cmdlet。 有关此视图的详细信息，请参阅 [列表视图](./creating-a-list-view.md)。

宽视图在一个或多个列中列出对象或脚本值的单个属性。 此视图没有标签或标题。 创建宽视图非常类似于通过管道将对象传递给 `Format-Wide` cmdlet。 有关此视图的详细信息，请参阅 [宽视图](./creating-a-wide-view.md)。

自定义视图显示对象属性或脚本值的可自定义视图，这些视图不遵守严格的表视图、列表视图或宽视图结构。 您可以定义独立的自定义视图，或者可以定义另一个视图（如表视图或列表视图）使用的自定义视图。 创建自定义视图非常类似于通过管道将对象传递给 `Format-Custom` cmdlet。 有关此视图的详细信息，请参阅 [自定义视图](./creating-custom-controls.md)。

## <a name="components-of-a-view"></a>视图的组件

下面的 XML 示例显示了视图的基本 XML 组件。 各个 XML 元素的变化取决于您要创建的视图，但视图的基本组件都是相同的。

首先，每个视图都有一个 `Name` 元素，该元素指定用于引用视图的用户友好名称。 一个 `ViewSelectedBy` 元素，该元素定义视图将显示哪些 .net 对象，以及一个定义视图的 *控件* 元素。

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

在 control 元素中，可以定义一个或多个 *entry* 元素。 如果使用多个定义，则必须指定哪些 .NET 对象使用每个定义。 每个控件通常只需要一个具有一个定义的条目。

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

在视图的每个条目元素中，指定定义该视图显示的 .NET 属性或脚本的 *项* 元素。

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

如前面的示例所示，格式设置文件可以包含多个视图，一个视图可以包含多个定义，每个定义可以包含多个项。

## <a name="example-of-a-table-view"></a>表格视图的示例

下面的示例显示用于定义包含两个列的表视图的 XML 标记。 [ViewDefinitions](./viewdefinitions-element-format.md)元素是在格式设置文件中定义的所有视图的容器元素。 [View](./view-element-format.md)元素定义特定的表、列表、宽视图或自定义视图。 在每个 [view](./view-element-format.md) 元素内， [name](./name-element-for-view-format.md) 元素指定视图的名称， [ViewSelectedBy](./viewselectedby-element-format.md) 元素定义使用视图的对象，而不同控件元素 (如 `TableControl` 下面的示例中所示的元素) 定义视图的类型。

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>另请参阅

[创建列表视图](./creating-a-list-view.md)

[创建表视图](./creating-a-table-view.md)

[创建宽视图](./creating-a-wide-view.md)

[创建自定义控件](./creating-custom-controls.md)

[编写 PowerShell 格式设置和类型文件](./writing-a-powershell-formatting-file.md)
