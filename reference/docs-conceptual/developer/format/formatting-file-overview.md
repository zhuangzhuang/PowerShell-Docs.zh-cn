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
# <a name="formatting-file-overview"></a><span data-ttu-id="501d1-103">格式设置文件概述</span><span class="sxs-lookup"><span data-stu-id="501d1-103">Formatting File Overview</span></span>

<span data-ttu-id="501d1-104"> (cmdlet、函数和脚本的命令返回的对象的显示格式) 是使用格式设置文件 ( # B0 xml 文件) 来定义的。</span><span class="sxs-lookup"><span data-stu-id="501d1-104">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="501d1-105">PowerShell 提供其中几个文件，用于定义由 PowerShell 提供的命令返回的对象的显示格式，如 cmdlet 返回的[system.object](/dotnet/api/System.Diagnostics.Process)对象。 `Get-Process`</span><span class="sxs-lookup"><span data-stu-id="501d1-105">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="501d1-106">但是，您还可以创建自己的自定义格式设置文件来覆盖默认的显示格式，也可以编写自定义格式设置文件来定义由您自己的命令返回的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="501d1-106">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="501d1-107">格式化文件不确定返回到管道的对象的元素。</span><span class="sxs-lookup"><span data-stu-id="501d1-107">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="501d1-108">当对象返回到管道时，即使某些成员未显示，该对象的所有成员仍可用。</span><span class="sxs-lookup"><span data-stu-id="501d1-108">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="501d1-109">PowerShell 使用这些格式设置文件中的数据来确定所显示的内容以及显示的数据的格式。</span><span class="sxs-lookup"><span data-stu-id="501d1-109">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="501d1-110">显示的数据可以包括对象的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="501d1-110">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="501d1-111">如果希望显示某个对象的属性中不能直接使用的值，例如，添加对象的两个属性的值，然后将 sum 显示为一段数据，则可以使用脚本。</span><span class="sxs-lookup"><span data-stu-id="501d1-111">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="501d1-112">通过为要显示的对象定义视图来完成显示数据的格式设置。</span><span class="sxs-lookup"><span data-stu-id="501d1-112">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="501d1-113">您可以为每个对象定义一个视图，可以为多个对象定义一个视图，也可以为同一对象定义多个视图。</span><span class="sxs-lookup"><span data-stu-id="501d1-113">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="501d1-114">您可以定义的视图数没有限制。</span><span class="sxs-lookup"><span data-stu-id="501d1-114">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="501d1-115">格式化文件的常用功能</span><span class="sxs-lookup"><span data-stu-id="501d1-115">Common Features of Formatting Files</span></span>

<span data-ttu-id="501d1-116">每个格式化文件都可以定义以下组件，这些组件可在文件定义的所有视图之间共享：</span><span class="sxs-lookup"><span data-stu-id="501d1-116">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="501d1-117">默认配置设置，例如，如果数据的长度超过列的宽度，则在表的行中显示的数据是否将显示在下一行。</span><span class="sxs-lookup"><span data-stu-id="501d1-117">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="501d1-118">有关这些设置的详细信息，请参阅 [定义常用配置设置](./defining-common-configuration-features.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-118">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="501d1-119">可由任何格式设置文件视图显示的对象集。</span><span class="sxs-lookup"><span data-stu-id="501d1-119">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="501d1-120">有关这些集 (称为 *选择集*) 的详细信息，请参阅 [定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-120">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="501d1-121">格式设置文件的所有视图都可以使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="501d1-121">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="501d1-122">控件使您可以更好地控制数据的显示方式。</span><span class="sxs-lookup"><span data-stu-id="501d1-122">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="501d1-123">有关控件的详细信息，请参阅 [定义自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-123">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="501d1-124">格式视图</span><span class="sxs-lookup"><span data-stu-id="501d1-124">Formatting Views</span></span>

<span data-ttu-id="501d1-125">格式视图可按表格式显示对象、列表格式、宽格式和自定义格式。</span><span class="sxs-lookup"><span data-stu-id="501d1-125">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="501d1-126">大多数情况下，每个格式设置定义由一组描述视图的 XML 标记来描述。</span><span class="sxs-lookup"><span data-stu-id="501d1-126">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="501d1-127">每个视图都包含视图的名称、使用该视图的对象和视图的元素，例如表视图的列和行信息。</span><span class="sxs-lookup"><span data-stu-id="501d1-127">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="501d1-128">表视图在一个或多个列中列出对象或脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="501d1-128">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="501d1-129">每个列表示对象的一个属性或一个脚本值。</span><span class="sxs-lookup"><span data-stu-id="501d1-129">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="501d1-130">您可以定义显示对象的所有属性的表视图、对象属性的子集或属性和脚本值的组合。</span><span class="sxs-lookup"><span data-stu-id="501d1-130">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="501d1-131">表中的每一行都表示一个返回的对象。</span><span class="sxs-lookup"><span data-stu-id="501d1-131">Each row of the table represents a returned object.</span></span> <span data-ttu-id="501d1-132">创建表视图非常类似于通过管道将对象传递给 `Format-Table` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="501d1-132">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="501d1-133">有关此视图的详细信息，请参阅 [表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-133">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="501d1-134">列表视图在单个列中列出对象或脚本值的属性。</span><span class="sxs-lookup"><span data-stu-id="501d1-134">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="501d1-135">列表中的每一行都显示一个可选标签或属性名称，后跟属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="501d1-135">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="501d1-136">创建列表视图非常类似于通过管道将对象传递给 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="501d1-136">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="501d1-137">有关此视图的详细信息，请参阅 [列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-137">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="501d1-138">宽视图在一个或多个列中列出对象或脚本值的单个属性。</span><span class="sxs-lookup"><span data-stu-id="501d1-138">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="501d1-139">此视图没有标签或标题。</span><span class="sxs-lookup"><span data-stu-id="501d1-139">There is no label or header for this view.</span></span> <span data-ttu-id="501d1-140">创建宽视图非常类似于通过管道将对象传递给 `Format-Wide` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="501d1-140">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="501d1-141">有关此视图的详细信息，请参阅 [宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-141">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="501d1-142">自定义视图显示对象属性或脚本值的可自定义视图，这些视图不遵守严格的表视图、列表视图或宽视图结构。</span><span class="sxs-lookup"><span data-stu-id="501d1-142">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="501d1-143">您可以定义独立的自定义视图，或者可以定义另一个视图（如表视图或列表视图）使用的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="501d1-143">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="501d1-144">创建自定义视图非常类似于通过管道将对象传递给 `Format-Custom` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="501d1-144">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="501d1-145">有关此视图的详细信息，请参阅 [自定义视图](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="501d1-145">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="501d1-146">视图的组件</span><span class="sxs-lookup"><span data-stu-id="501d1-146">Components of a View</span></span>

<span data-ttu-id="501d1-147">下面的 XML 示例显示了视图的基本 XML 组件。</span><span class="sxs-lookup"><span data-stu-id="501d1-147">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="501d1-148">各个 XML 元素的变化取决于您要创建的视图，但视图的基本组件都是相同的。</span><span class="sxs-lookup"><span data-stu-id="501d1-148">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="501d1-149">首先，每个视图都有一个 `Name` 元素，该元素指定用于引用视图的用户友好名称。</span><span class="sxs-lookup"><span data-stu-id="501d1-149">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="501d1-150">一个 `ViewSelectedBy` 元素，该元素定义视图将显示哪些 .net 对象，以及一个定义视图的 *控件* 元素。</span><span class="sxs-lookup"><span data-stu-id="501d1-150">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="501d1-151">在 control 元素中，可以定义一个或多个 *entry* 元素。</span><span class="sxs-lookup"><span data-stu-id="501d1-151">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="501d1-152">如果使用多个定义，则必须指定哪些 .NET 对象使用每个定义。</span><span class="sxs-lookup"><span data-stu-id="501d1-152">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="501d1-153">每个控件通常只需要一个具有一个定义的条目。</span><span class="sxs-lookup"><span data-stu-id="501d1-153">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="501d1-154">在视图的每个条目元素中，指定定义该视图显示的 .NET 属性或脚本的 *项* 元素。</span><span class="sxs-lookup"><span data-stu-id="501d1-154">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="501d1-155">如前面的示例所示，格式设置文件可以包含多个视图，一个视图可以包含多个定义，每个定义可以包含多个项。</span><span class="sxs-lookup"><span data-stu-id="501d1-155">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="501d1-156">表格视图的示例</span><span class="sxs-lookup"><span data-stu-id="501d1-156">Example of a Table View</span></span>

<span data-ttu-id="501d1-157">下面的示例显示用于定义包含两个列的表视图的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="501d1-157">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="501d1-158">[ViewDefinitions](./viewdefinitions-element-format.md)元素是在格式设置文件中定义的所有视图的容器元素。</span><span class="sxs-lookup"><span data-stu-id="501d1-158">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="501d1-159">[View](./view-element-format.md)元素定义特定的表、列表、宽视图或自定义视图。</span><span class="sxs-lookup"><span data-stu-id="501d1-159">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="501d1-160">在每个 [view](./view-element-format.md) 元素内， [name](./name-element-for-view-format.md) 元素指定视图的名称， [ViewSelectedBy](./viewselectedby-element-format.md) 元素定义使用视图的对象，而不同控件元素 (如 `TableControl` 下面的示例中所示的元素) 定义视图的类型。</span><span class="sxs-lookup"><span data-stu-id="501d1-160">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="501d1-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="501d1-161">See Also</span></span>

[<span data-ttu-id="501d1-162">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="501d1-162">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="501d1-163">创建表视图</span><span class="sxs-lookup"><span data-stu-id="501d1-163">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="501d1-164">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="501d1-164">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="501d1-165">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="501d1-165">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="501d1-166">编写 PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="501d1-166">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
