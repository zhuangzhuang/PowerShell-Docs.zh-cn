---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-TypeData
ms.openlocfilehash: 1314d388bff5a46bcf335f3da7908a65233aa46e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598681"
---
# <span data-ttu-id="0e079-102">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="0e079-102">Update-TypeData</span></span>

## <span data-ttu-id="0e079-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0e079-103">Synopsis</span></span>
<span data-ttu-id="0e079-104">更新会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-104">Updates the extended type data in the session.</span></span>

## <span data-ttu-id="0e079-105">语法</span><span class="sxs-lookup"><span data-stu-id="0e079-105">Syntax</span></span>

### <span data-ttu-id="0e079-106">FileSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="0e079-106">FileSet (Default)</span></span>

```
Update-TypeData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="0e079-107">DynamicTypeSet</span><span class="sxs-lookup"><span data-stu-id="0e079-107">DynamicTypeSet</span></span>

```
Update-TypeData [-MemberType <PSMemberTypes>] [-MemberName <String>] [-Value <Object>]
 [-SecondValue <Object>] [-TypeConverter <Type>] [-TypeAdapter <Type>]
 [-SerializationMethod <String>] [-TargetTypeForDeserialization <Type>]
 [-SerializationDepth <Int32>] [-DefaultDisplayProperty <String>]
 [-InheritPropertySerializationSet <Nullable`1>] [-StringSerializationSource <String>]
 [-DefaultDisplayPropertySet <String[]>] [-DefaultKeyPropertySet <String[]>]
 [-PropertySerializationSet <String[]>] -TypeName <String> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="0e079-108">TypeDataSet</span><span class="sxs-lookup"><span data-stu-id="0e079-108">TypeDataSet</span></span>

```
Update-TypeData [-Force] [-TypeData] <TypeData[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0e079-109">说明</span><span class="sxs-lookup"><span data-stu-id="0e079-109">Description</span></span>

<span data-ttu-id="0e079-110">该 `Update-TypeData` cmdlet 将更新会话中的扩展类型数据，方法是 `Types.ps1xml` 将文件重新加载到内存中并添加新的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-110">The `Update-TypeData` cmdlet updates the extended type data in the session by reloading the `Types.ps1xml` files into memory and adding new extended type data.</span></span>

<span data-ttu-id="0e079-111">默认情况下，PowerShell 将在需要时加载扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-111">By default, PowerShell loads extended type data as it is needed.</span></span> <span data-ttu-id="0e079-112">如果没有参数，则 `Update-TypeData` 会重新加载 `Types.ps1xml` 已在会话中加载的所有文件，包括你添加的所有类型文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-112">Without parameters, `Update-TypeData` reloads all of the `Types.ps1xml` files that it has loaded in the session, including any type files that you added.</span></span> <span data-ttu-id="0e079-113">您可以使用的参数 `Update-TypeData` 添加新的类型文件以及添加和替换扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-113">You can use the parameters of `Update-TypeData` to add new type files and add and replace extended type data.</span></span>

<span data-ttu-id="0e079-114">`Update-TypeData`Cmdlet 可用于预加载所有类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-114">The `Update-TypeData` cmdlet can be used to preload all type data.</span></span> <span data-ttu-id="0e079-115">当你要开发类型并且想要加载这些新类型用于测试目的时，此功能尤其有用。</span><span class="sxs-lookup"><span data-stu-id="0e079-115">This feature is particularly useful when you are developing types and want to load those new types for testing purposes.</span></span>

<span data-ttu-id="0e079-116">从 Windows PowerShell 3.0 开始，你可以使用 `Update-TypeData` 添加和替换会话中的扩展类型数据，而无需使用 `Types.ps1xml` 文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-116">Beginning in Windows PowerShell 3.0, you can use `Update-TypeData` to add and replace extended type data in the session without using a `Types.ps1xml` file.</span></span> <span data-ttu-id="0e079-117">仅将动态（即无需文件）添加的类型数据添加到当前会话中。</span><span class="sxs-lookup"><span data-stu-id="0e079-117">Type data that is added dynamically, that is, without a file, is added only to the current session.</span></span> <span data-ttu-id="0e079-118">若要将类型数据添加到所有会话，请将 `Update-TypeData` 命令添加到 PowerShell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-118">To add the type data to all sessions, add an `Update-TypeData` command to your PowerShell profile.</span></span> <span data-ttu-id="0e079-119">有关详细信息，请参阅 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="0e079-119">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

<span data-ttu-id="0e079-120">此外，从 Windows PowerShell 3.0 开始，你可以使用 `Get-TypeData` cmdlet 来获取当前会话中的扩展类型，使用 `Remove-TypeData` cmdlet 从当前会话中删除扩展类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-120">Also, beginning in Windows PowerShell 3.0, you can use the `Get-TypeData` cmdlet to get the extended types in the current session and the `Remove-TypeData` cmdlet to delete extended types from the current session.</span></span>

<span data-ttu-id="0e079-121">在属性中发生的异常或通过将属性添加到 `Update-TypeData` 命令中时，不会报告错误。</span><span class="sxs-lookup"><span data-stu-id="0e079-121">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors.</span></span> <span data-ttu-id="0e079-122">这是为了取消显示在格式设置和输出期间在许多常见类型中发生的异常。</span><span class="sxs-lookup"><span data-stu-id="0e079-122">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="0e079-123">如果你正在获取 .NET 属性，则可以通过使用方法语法来解决禁止显示异常的情况，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="0e079-123">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

`"hello".get_Length()`

<span data-ttu-id="0e079-124">请注意，方法语法仅可用于 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-124">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="0e079-125">通过运行 cmdlet 添加的属性 `Update-TypeData` 不能使用方法语法。</span><span class="sxs-lookup"><span data-stu-id="0e079-125">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

<span data-ttu-id="0e079-126">有关 PowerShell 中的文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0e079-126">For more information about the `Types.ps1xml` files in PowerShell, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span>

## <span data-ttu-id="0e079-127">示例</span><span class="sxs-lookup"><span data-stu-id="0e079-127">Examples</span></span>

### <span data-ttu-id="0e079-128">示例1：更新扩展类型</span><span class="sxs-lookup"><span data-stu-id="0e079-128">Example 1: Update extended types</span></span>

```powershell
Update-TypeData
```

<span data-ttu-id="0e079-129">此命令从已 `Types.ps1xml` 在会话中使用的文件中更新扩展类型配置。</span><span class="sxs-lookup"><span data-stu-id="0e079-129">This command updates the extended type configuration from the `Types.ps1xml` files that have already been used in the session.</span></span>

### <span data-ttu-id="0e079-130">示例2：多次更新类型</span><span class="sxs-lookup"><span data-stu-id="0e079-130">Example 2: Update types multiple times</span></span>

<span data-ttu-id="0e079-131">此示例显示了如何在同一会话中多次更新类型文件中的类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-131">This example shows how to update the types in a type file multiple times in the same session.</span></span>

<span data-ttu-id="0e079-132">第一个命令从文件更新扩展类型配置 `Types.ps1xml` ， `TypesA.types.ps1xml` 并首先处理和 `TypesB.types.ps1xml` 文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-132">The first command updates the extended type configuration from the `Types.ps1xml` files, processing the `TypesA.types.ps1xml` and `TypesB.types.ps1xml` files first.</span></span>

<span data-ttu-id="0e079-133">第二个命令显示如何重新更新 `TypesA.types.ps1xml` ，如您在文件中添加或更改了类型时可能会执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0e079-133">The second command shows how to update the `TypesA.types.ps1xml` again, such as you might do if you added or changed a type in the file.</span></span> <span data-ttu-id="0e079-134">您可以为文件重复前面的命令 `TypesA.types.ps1xml` ，也可以运行 `Update-TypeData` 不带参数的命令，因为已 `TypesA.types.ps1xml` 在当前会话的类型文件列表中。</span><span class="sxs-lookup"><span data-stu-id="0e079-134">You can either repeat the previous command for the `TypesA.types.ps1xml` file, or run an `Update-TypeData` command without parameters, because `TypesA.types.ps1xml` is already in the type file list for the current session.</span></span>

```powershell
Update-TypeData -PrependPath TypesA.types.ps1xml, TypesB.types.ps1xml
Update-TypeData -PrependPath TypesA.types.ps1xml
```

### <span data-ttu-id="0e079-135">示例3：向 DateTime 对象添加脚本属性</span><span class="sxs-lookup"><span data-stu-id="0e079-135">Example 3: Add a script property to DateTime objects</span></span>

<span data-ttu-id="0e079-136">此示例使用 `Update-TypeData` 将 "**季度** 脚本" 属性添加到当前会话中的 **system.object** 对象，如 cmdlet 返回的对象。 `Get-Date`</span><span class="sxs-lookup"><span data-stu-id="0e079-136">This example uses `Update-TypeData` to add the **Quarter** script property to **System.DateTime** objects in the current session, such as those returned by the `Get-Date` cmdlet.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -MemberType ScriptProperty -MemberName "Quarter" -Value {
  if ($this.Month -in @(1,2,3)) {"Q1"}
  elseif ($this.Month -in @(4,5,6)) {"Q2"}
  elseif ($this.Month -in @(7,8,9)) {"Q3"}
  else {"Q4"}
}
(Get-Date).Quarter
```

```Output
Q1
```

<span data-ttu-id="0e079-137">该 `Update-TypeData` 命令使用 **TypeName** 参数来指定 system.string 类型，使用 **成员** 名称参数指定新属性的名称，使用 **MemberType** 属性指定 **ScriptProperty** 类型，并使用 **Value** 参数指定用于确定年季度的脚本。</span><span class="sxs-lookup"><span data-stu-id="0e079-137">The `Update-TypeData` command uses the **TypeName** parameter to specify **the System.DateTime** type, the **MemberName** parameter to specify a name for the new property, the **MemberType** property to specify the **ScriptProperty** type, and the **Value** parameter to specify the script that determines the annual quarter.</span></span>

<span data-ttu-id="0e079-138">**Value** 属性的值是一个用于计算当前年度季度的脚本。</span><span class="sxs-lookup"><span data-stu-id="0e079-138">The value of the **Value** property is a script that calculates the current annual quarter.</span></span> <span data-ttu-id="0e079-139">脚本块使用 `$this` 自动变量来表示对象的当前实例，并使用 In 运算符来确定每个整数数组中是否出现月份值。</span><span class="sxs-lookup"><span data-stu-id="0e079-139">The script block uses the `$this` automatic variable to represent the current instance of the object and the In operator to determine whether the month value appears in each integer array.</span></span> <span data-ttu-id="0e079-140">有关运算符的详细信息 `-in` ，请参阅 [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0e079-140">For more information about the `-in` operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/about/about_Comparison_Operators.md).</span></span>

<span data-ttu-id="0e079-141">第二个命令将获取当前日期的新 Quarter 属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-141">The second command gets the new Quarter property of the current date.</span></span>

### <span data-ttu-id="0e079-142">示例4：更新默认显示在列表中的类型</span><span class="sxs-lookup"><span data-stu-id="0e079-142">Example 4: Update a type that displays in lists by default</span></span>

<span data-ttu-id="0e079-143">此示例演示如何设置默认情况下在列表中显示的类型的属性，即，当未指定任何属性时。</span><span class="sxs-lookup"><span data-stu-id="0e079-143">This example shows how to set the properties of a type that displays in lists by default, that is, when no properties are specified.</span></span> <span data-ttu-id="0e079-144">由于未在文件中指定类型数据 `Types.ps1xml` ，因此它仅在当前会话中有效。</span><span class="sxs-lookup"><span data-stu-id="0e079-144">Because the type data is not specified in a `Types.ps1xml` file, it is effective only in the current session.</span></span>

```powershell
Update-TypeData -TypeName "System.DateTime" -DefaultDisplayPropertySet "DateTime, DayOfYear, Quarter"
Get-Date | Format-List
```

```Output
Thursday, March 15, 2012 12:00:00 AM
DayOfYear : 75
Quarter   : Q1
```

<span data-ttu-id="0e079-145">第一个命令使用 `Update-TypeData` cmdlet 为 system.string 类型设置默认列表属性。 </span><span class="sxs-lookup"><span data-stu-id="0e079-145">The first command uses the `Update-TypeData` cmdlet to set the default list properties for the **System.DateTime** type.</span></span> <span data-ttu-id="0e079-146">该命令使用 **TypeName** 参数指定类型，并使用 **DefaultDisplayPropertySet** 参数指定列表的默认属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-146">The command uses the **TypeName** parameter to specify the type and the **DefaultDisplayPropertySet** parameter to specify the default properties for a list.</span></span> <span data-ttu-id="0e079-147">所选属性包括在前面的示例中添加的新的 " **季度** 脚本" 属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-147">The selected properties include the new **Quarter** script property that was added in a previous example.</span></span>

<span data-ttu-id="0e079-148">第二个命令使用 `Get-Date` cmdlet 获取表示当前日期的 system.string 对象。</span><span class="sxs-lookup"><span data-stu-id="0e079-148">The second command uses the `Get-Date` cmdlet to get a **System.DateTime** object that represents the current date.</span></span> <span data-ttu-id="0e079-149">该命令使用管道运算符 (`|`) 将 **DateTime** 对象发送到 `Format-List` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0e079-149">The command uses a pipeline operator (`|`) to send the **DateTime** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="0e079-150">由于该 `Format-List` 命令未指定要在列表中显示的属性，因此 PowerShell 将使用通过命令建立的默认值 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-150">Because the `Format-List` command does not specify the properties to display in the list, PowerShell uses the default values that were established by the `Update-TypeData` command.</span></span>

### <span data-ttu-id="0e079-151">示例5：更新管道对象的类型数据</span><span class="sxs-lookup"><span data-stu-id="0e079-151">Example 5: Update type data for a piped object</span></span>

```powershell
Get-Module | Update-TypeData -MemberType ScriptProperty -MemberName "SupportsUpdatableHelp" -Value {
  if ($this.HelpInfoUri) {$True} else {$False}
}
Get-Module -ListAvailable | Format-Table Name, SupportsUpdatableHelp
```

```Output
Name                             SupportsUpdatableHelp
----                             ---------------------
Microsoft.PowerShell.Diagnostics                  True
Microsoft.PowerShell.Host                         True
Microsoft.PowerShell.Management                   True
Microsoft.PowerShell.Security                     True
Microsoft.PowerShell.Utility                      True
Microsoft.WSMan.Management                        True
PSDiagnostics                                    False
PSScheduledJob                                    True
PSWorkflow                                        True
ServerManager                                     True
TroubleshootingPack                              False
```

<span data-ttu-id="0e079-152">此示例演示当你通过管道将对象传递给时 `Update-TypeData` ，会 `Update-TypeData` 为该对象类型添加扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-152">This example demonstrates that when you pipe an object to `Update-TypeData`, `Update-TypeData` adds extended type data for the object type.</span></span>

<span data-ttu-id="0e079-153">此方法比使用 `Get-Member` cmdlet 或 `Get-Type` 方法获取对象类型要快。</span><span class="sxs-lookup"><span data-stu-id="0e079-153">This technique is quicker than using the `Get-Member` cmdlet or the `Get-Type` method to get the object type.</span></span> <span data-ttu-id="0e079-154">但是，如果您通过管道将对象的集合传递给 `Update-TypeData` ，它会更新第一个对象类型的类型数据，然后为该集合中的所有其他对象返回一个错误，因为已在该类型上定义了成员。</span><span class="sxs-lookup"><span data-stu-id="0e079-154">However, if you pipe a collection of objects to `Update-TypeData`, it updates the type data of the first object type and then returns an error for all other objects in the collection because the member is already defined on the type.</span></span>

<span data-ttu-id="0e079-155">第一个命令使用 `Get-Module` cmdlet 来获取 PSScheduledJob 模块。</span><span class="sxs-lookup"><span data-stu-id="0e079-155">The first command uses the `Get-Module` cmdlet to get the PSScheduledJob module.</span></span> <span data-ttu-id="0e079-156">命令通过管道将模块对象传递给 `Update-TypeData` cmdlet，这会更新 **PSModuleInfo** 类型的类型数据以及从其派生的类型，例如， `Get-Module` 当你在命令中使用 **ListAvailable** 参数时返回的 ModuleInfoGrouping 类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-156">The command pipes the module object to the `Update-TypeData` cmdlet, which updates the type data for the **System.Management.Automation.PSModuleInfo** type and the types derived from it, such as the ModuleInfoGrouping type that `Get-Module` returns when you use the **ListAvailable** parameter in the command.</span></span>

<span data-ttu-id="0e079-157">这些 `Update-TypeData` 命令将 **SupportsUpdatableHelp** 脚本属性添加到所有导入的模块中。</span><span class="sxs-lookup"><span data-stu-id="0e079-157">The `Update-TypeData` commands adds the **SupportsUpdatableHelp** script property to all imported modules.</span></span> <span data-ttu-id="0e079-158">**Value** 参数的值是一个脚本， `$True` 如果填充了模块的 **HelpInfoUri** 属性，则返回，否则返回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-158">The value of the **Value** parameter is a script that returns `$True` if the **HelpInfoUri** property of the module is populated and `$False` otherwise.</span></span>

<span data-ttu-id="0e079-159">第二个命令通过管道将模块对象传递 `Get-Module` 给 `Format-Table` cmdlet，后者将显示列表中所有模块的 **Name** 和 **SupportsUpdatableHelp** 属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-159">The second command pipes the module objects from `Get-Module` to the `Format-Table` cmdlet, which displays the **Name** and **SupportsUpdatableHelp** properties of all modules in a list.</span></span>

## <span data-ttu-id="0e079-160">参数</span><span class="sxs-lookup"><span data-stu-id="0e079-160">Parameters</span></span>

### <span data-ttu-id="0e079-161">-AppendPath</span><span class="sxs-lookup"><span data-stu-id="0e079-161">-AppendPath</span></span>

<span data-ttu-id="0e079-162">指定可选文件的路径 `.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-162">Specifies the path to optional `.ps1xml` files.</span></span> <span data-ttu-id="0e079-163">按加载内置文件后列出指定文件的顺序来加载这些文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-163">The specified files are loaded in the order that they are listed after the built-in files are loaded.</span></span> <span data-ttu-id="0e079-164">还可以通过管道将 **AppendPath** 值传递给 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-164">You can also pipe an **AppendPath** value to `Update-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-165">-DefaultDisplayProperty</span><span class="sxs-lookup"><span data-stu-id="0e079-165">-DefaultDisplayProperty</span></span>

<span data-ttu-id="0e079-166">指定 `Format-Wide` 在未指定其他属性时由 cmdlet 显示的类型的属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-166">Specifies the property of the type that is displayed by the `Format-Wide` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="0e079-167">键入类型的标准或扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-167">Type the name of a standard or extended property of the type.</span></span> <span data-ttu-id="0e079-168">此参数的值可以是已添加到同一命令中的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-168">The value of this parameter can be the name of a type that is added in the same command.</span></span>

<span data-ttu-id="0e079-169">仅当没有为文件中的类型定义宽视图时，此值才有效 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-169">This value is effective only when there are no wide views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="0e079-170">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-170">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-171">-DefaultDisplayPropertySet</span><span class="sxs-lookup"><span data-stu-id="0e079-171">-DefaultDisplayPropertySet</span></span>

<span data-ttu-id="0e079-172">指定类型的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-172">Specifies one or more properties of the type.</span></span> <span data-ttu-id="0e079-173">`Format-List`如果未指定其他属性，则 cmdlet 将显示这些属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-173">These properties are displayed by the `Format-List` cmdlet when no other properties are specified.</span></span>

<span data-ttu-id="0e079-174">键入类型的标准或扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-174">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="0e079-175">此参数的值可以是已添加到同一命令中的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-175">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="0e079-176">仅当没有为文件中的类型定义列表视图时，此值才有效 `Format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-176">This value is effective only when there are no list views defined for the type in a `Format.ps1xml` file.</span></span>

<span data-ttu-id="0e079-177">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-178">-DefaultKeyPropertySet</span><span class="sxs-lookup"><span data-stu-id="0e079-178">-DefaultKeyPropertySet</span></span>

<span data-ttu-id="0e079-179">指定类型的一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-179">Specifies one or more properties of the type.</span></span> <span data-ttu-id="0e079-180">`Group-Object` `Sort-Object` 当未指定其他属性时，和 cmdlet 将使用这些属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-180">These properties are used by the `Group-Object` and `Sort-Object` cmdlets when no other properties are specified.</span></span>

<span data-ttu-id="0e079-181">键入类型的标准或扩展属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-181">Type the names of standard or extended properties of the type.</span></span> <span data-ttu-id="0e079-182">此参数的值可以是已添加到同一命令中的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-182">The value of this parameter can be the names of types that are added in the same command.</span></span>

<span data-ttu-id="0e079-183">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-183">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-184">-Force</span><span class="sxs-lookup"><span data-stu-id="0e079-184">-Force</span></span>

<span data-ttu-id="0e079-185">指示该 cmdlet 使用指定的类型数据，即使已为该类型指定了类型数据。</span><span class="sxs-lookup"><span data-stu-id="0e079-185">Indicates that the cmdlet uses the specified type data, even if type data has already been specified for that type.</span></span>

<span data-ttu-id="0e079-186">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-186">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DynamicTypeSet, TypeDataSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-187">-InheritPropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="0e079-187">-InheritPropertySerializationSet</span></span>

<span data-ttu-id="0e079-188">指示是否继承序列化的属性集。</span><span class="sxs-lookup"><span data-stu-id="0e079-188">Indicates whether the set of properties that are serialized is inherited.</span></span> <span data-ttu-id="0e079-189">默认值是 `$Null`。</span><span class="sxs-lookup"><span data-stu-id="0e079-189">The default value is `$Null`.</span></span> <span data-ttu-id="0e079-190">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0e079-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0e079-191">`$True`.</span><span class="sxs-lookup"><span data-stu-id="0e079-191">`$True`.</span></span> <span data-ttu-id="0e079-192">继承属性集。</span><span class="sxs-lookup"><span data-stu-id="0e079-192">The property set is inherited.</span></span>
- <span data-ttu-id="0e079-193">`$False`.</span><span class="sxs-lookup"><span data-stu-id="0e079-193">`$False`.</span></span> <span data-ttu-id="0e079-194">不继承属性集。</span><span class="sxs-lookup"><span data-stu-id="0e079-194">The property set is not inherited.</span></span>
- <span data-ttu-id="0e079-195">`$Null`.</span><span class="sxs-lookup"><span data-stu-id="0e079-195">`$Null`.</span></span> <span data-ttu-id="0e079-196">未定义继承。</span><span class="sxs-lookup"><span data-stu-id="0e079-196">Inheritance is not defined.</span></span>

<span data-ttu-id="0e079-197">仅当 **SerializationMethod** 参数的值为时，此参数才有效 `SpecificProperties` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-197">This parameter is valid only when the value of the **SerializationMethod** parameter is `SpecificProperties`.</span></span> <span data-ttu-id="0e079-198">当此参数的值为时 `$False` ， **PropertySerializationSet** 参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="0e079-198">When the value of this parameter is `$False`, the **PropertySerializationSet** parameter is required.</span></span>

<span data-ttu-id="0e079-199">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Nullable`1[System.Boolean]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-200">-MemberName</span><span class="sxs-lookup"><span data-stu-id="0e079-200">-MemberName</span></span>

<span data-ttu-id="0e079-201">指定属性或方法的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-201">Specifies the name of a property or method.</span></span>

<span data-ttu-id="0e079-202">将此参数与 **TypeName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-202">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="0e079-203">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-204">-MemberType</span><span class="sxs-lookup"><span data-stu-id="0e079-204">-MemberType</span></span>

<span data-ttu-id="0e079-205">指定要添加或更改的成员类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-205">Specifies the type of the member to add or change.</span></span>

<span data-ttu-id="0e079-206">将此参数与 **TypeName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-206">Use this parameter with the **TypeName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span> <span data-ttu-id="0e079-207">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0e079-207">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0e079-208">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="0e079-208">AliasProperty</span></span>
- <span data-ttu-id="0e079-209">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="0e079-209">CodeMethod</span></span>
- <span data-ttu-id="0e079-210">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="0e079-210">CodeProperty</span></span>
- <span data-ttu-id="0e079-211">Noteproperty</span><span class="sxs-lookup"><span data-stu-id="0e079-211">Noteproperty</span></span>
- <span data-ttu-id="0e079-212">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="0e079-212">ScriptMethod</span></span>
- <span data-ttu-id="0e079-213">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="0e079-213">ScriptProperty</span></span>

<span data-ttu-id="0e079-214">有关这些值的信息，请参阅 [PSMemberTypes 枚举](/dotnet/api/system.management.automation.psmembertypes)。</span><span class="sxs-lookup"><span data-stu-id="0e079-214">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes).</span></span>

<span data-ttu-id="0e079-215">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: DynamicTypeSet
Aliases:
Accepted values: NoteProperty, AliasProperty, ScriptProperty, CodeProperty, ScriptMethod, CodeMethod

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-216">-PrependPath</span><span class="sxs-lookup"><span data-stu-id="0e079-216">-PrependPath</span></span>

<span data-ttu-id="0e079-217">指定可选文件的路径 `.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-217">Specifies the path to the optional `.ps1xml` files.</span></span> <span data-ttu-id="0e079-218">按加载内置文件前列出指定文件的顺序来加载这些文件。</span><span class="sxs-lookup"><span data-stu-id="0e079-218">The specified files are loaded in the order that they are listed before the built-in files are loaded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-219">-PropertySerializationSet</span><span class="sxs-lookup"><span data-stu-id="0e079-219">-PropertySerializationSet</span></span>

<span data-ttu-id="0e079-220">指定已进行序列化的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-220">Specifies the names of properties that are serialized.</span></span> <span data-ttu-id="0e079-221">当 **SerializationMethod** 参数的值为 **SpecificProperties** 时，使用此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-221">Use this parameter when the value of the **SerializationMethod** parameter is **SpecificProperties**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-222">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="0e079-222">-SecondValue</span></span>

<span data-ttu-id="0e079-223">指定 **AliasProperty**、**ScriptProperty**、**CodeProperty** 或 **CodeMethod** 成员的其他值。</span><span class="sxs-lookup"><span data-stu-id="0e079-223">Specifies additional values for **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="0e079-224">将此参数与 **TypeName**、 **MemberType**、 **Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-224">Use this parameter with the **TypeName**, **MemberType**, **Value**, and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="0e079-225">当 **MemberType** 参数的值为时 `AliasProperty` ， **SecondValue** 参数的值必须是数据类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-225">When the value of the **MemberType** parameter is `AliasProperty`, the value of the **SecondValue** parameter must be a data type.</span></span> <span data-ttu-id="0e079-226">PowerShell) 会将别名属性的值转换 (为指定的类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-226">PowerShell converts (that is, casts) the value of the alias property to the specified type.</span></span> <span data-ttu-id="0e079-227">例如，如果添加 **了为字符串** 属性提供备用名称的别名属性，则还可以指定 **SecondValue** 来将别名字符串值转换为整数。</span><span class="sxs-lookup"><span data-stu-id="0e079-227">For example, if you add an alias property that provides an alternate name for a string property, you can also specify a **SecondValue** of **System.Int32** to convert the aliased string value to an integer.</span></span>

<span data-ttu-id="0e079-228">当 **MemberType** 参数的值为时 `ScriptProperty` ，可以使用 **SecondValue** 参数来指定其他脚本块。</span><span class="sxs-lookup"><span data-stu-id="0e079-228">When the value of the **MemberType** parameter is `ScriptProperty`, you can use the **SecondValue** parameter to specify an additional script block.</span></span> <span data-ttu-id="0e079-229">**Value** 参数的值中的脚本块将获取变量的值。</span><span class="sxs-lookup"><span data-stu-id="0e079-229">The script block in the value of the **Value** parameter gets the value of a variable.</span></span> <span data-ttu-id="0e079-230">**SecondValue** 参数的值中的脚本块将设置该变量的值。</span><span class="sxs-lookup"><span data-stu-id="0e079-230">The script block in the value of the **SecondValue** parameter set the value of the variable.</span></span>

<span data-ttu-id="0e079-231">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-232">-SerializationDepth</span><span class="sxs-lookup"><span data-stu-id="0e079-232">-SerializationDepth</span></span>

<span data-ttu-id="0e079-233">指定将多少个级别的类型对象序列化为字符串。</span><span class="sxs-lookup"><span data-stu-id="0e079-233">Specifies how many levels of type objects are serialized as strings.</span></span> <span data-ttu-id="0e079-234">默认值将 `1` 序列化对象及其属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-234">The default value `1` serializes the object and its properties.</span></span> <span data-ttu-id="0e079-235">值用于 `0` 序列化对象，但不序列化其属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-235">A value of `0` serializes the object, but not its properties.</span></span> <span data-ttu-id="0e079-236">值用于 `2` 序列化对象、其属性和属性值中的任何对象。</span><span class="sxs-lookup"><span data-stu-id="0e079-236">A value of `2` serializes the object, its properties, and any objects in property values.</span></span>

<span data-ttu-id="0e079-237">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-238">-SerializationMethod</span><span class="sxs-lookup"><span data-stu-id="0e079-238">-SerializationMethod</span></span>

<span data-ttu-id="0e079-239">为类型指定序列化方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-239">Specifies a serialization method for the type.</span></span> <span data-ttu-id="0e079-240">序列化方法将确定序列化类型的哪些属性以及用于对其进行序列化的方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-240">A serialization method determines which properties of the type are serialized and the technique that is used to serialize them.</span></span> <span data-ttu-id="0e079-241">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0e079-241">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0e079-242">`AllPublicProperties`.</span><span class="sxs-lookup"><span data-stu-id="0e079-242">`AllPublicProperties`.</span></span> <span data-ttu-id="0e079-243">序列化类型的所有公共属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-243">Serialize all public properties of the type.</span></span> <span data-ttu-id="0e079-244">可以使用 **SerializationDepth** 参数确定是否序列化子属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-244">You can use the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>
- <span data-ttu-id="0e079-245">`String`.</span><span class="sxs-lookup"><span data-stu-id="0e079-245">`String`.</span></span> <span data-ttu-id="0e079-246">将类型序列化为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="0e079-246">Serialize the type as a string.</span></span> <span data-ttu-id="0e079-247">可以使用 **StringSerializationSource** 指定要用作序列化结果的类型的属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-247">You can use the **StringSerializationSource** to specify a property of the type to use as the serialization result.</span></span> <span data-ttu-id="0e079-248">否则，通过使用对象的 **ToString** 方法序列化该类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-248">Otherwise, the type is serialized by using the **ToString** method of the object.</span></span>
- <span data-ttu-id="0e079-249">`SpecificProperties`.</span><span class="sxs-lookup"><span data-stu-id="0e079-249">`SpecificProperties`.</span></span> <span data-ttu-id="0e079-250">仅序列化此类型的指定属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-250">Serialize only the specified properties of this type.</span></span> <span data-ttu-id="0e079-251">使用 **PropertySerializationSet** 参数指定已进行序列化的类型的属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-251">Use the **PropertySerializationSet** parameter to specify the properties of the type that are serialized.</span></span>
  <span data-ttu-id="0e079-252">还可以使用 **InheritPropertySerializationSet** 参数确定是否继承属性集，并使用 **SerializationDepth** 参数确定是否序列化子属性。</span><span class="sxs-lookup"><span data-stu-id="0e079-252">You can also use the **InheritPropertySerializationSet** parameter to determine whether the property set is inherited and the **SerializationDepth** parameter to determine whether child properties are serialized.</span></span>

<span data-ttu-id="0e079-253">在 PowerShell 中，序列化方法存储在 **PSStandardMembers** 内部对象中。</span><span class="sxs-lookup"><span data-stu-id="0e079-253">In PowerShell, serialization methods are stored in **PSStandardMembers** internal objects.</span></span>

<span data-ttu-id="0e079-254">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-255">-StringSerializationSource</span><span class="sxs-lookup"><span data-stu-id="0e079-255">-StringSerializationSource</span></span>

<span data-ttu-id="0e079-256">指定类型的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-256">Specifies the name of a property of the type.</span></span> <span data-ttu-id="0e079-257">指定属性的值将用作序列化结果。</span><span class="sxs-lookup"><span data-stu-id="0e079-257">The value of specified property is used as the serialization result.</span></span> <span data-ttu-id="0e079-258">仅当 **SerializationMethod** 参数的值为 String 时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="0e079-258">This parameter is valid only when the value of the **SerializationMethod** parameter is String.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-259">-TargetTypeForDeserialization</span><span class="sxs-lookup"><span data-stu-id="0e079-259">-TargetTypeForDeserialization</span></span>

<span data-ttu-id="0e079-260">指定此类型的对象被反序列化时将转换为哪种类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-260">Specifies the type to which object of this type are converted when they are deserialized.</span></span>

<span data-ttu-id="0e079-261">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-262">-TypeAdapter</span><span class="sxs-lookup"><span data-stu-id="0e079-262">-TypeAdapter</span></span>

<span data-ttu-id="0e079-263">指定类型适配器的类型（如 **microsoft.powershell.cim.ciminstanceadapter 等**）。</span><span class="sxs-lookup"><span data-stu-id="0e079-263">Specifies the type of a type adapter, such as **Microsoft.PowerShell.Cim.CimInstanceAdapter**.</span></span> <span data-ttu-id="0e079-264">类型适配器使 PowerShell 能够获取类型的成员。</span><span class="sxs-lookup"><span data-stu-id="0e079-264">A type adapter enables PowerShell to get the members of a type.</span></span>

<span data-ttu-id="0e079-265">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-266">-TypeConverter</span><span class="sxs-lookup"><span data-stu-id="0e079-266">-TypeConverter</span></span>

<span data-ttu-id="0e079-267">指定可在不同类型之间转换值的类型转换器。</span><span class="sxs-lookup"><span data-stu-id="0e079-267">Specifies a type converter to convert values between different types.</span></span> <span data-ttu-id="0e079-268">如果为某个类型定义一个类型转换器，则该类型转换器的实例将用于转换过程。</span><span class="sxs-lookup"><span data-stu-id="0e079-268">If a type converter is defined for a type, an instance of the type converter is used for the conversion.</span></span>

<span data-ttu-id="0e079-269">输入派生自 **System.ComponentModel.TypeConverter** 或 **System.Management.Automation.PSTypeConverter** 类的 **System.Type** 值。</span><span class="sxs-lookup"><span data-stu-id="0e079-269">Enter a **System.Type** value that is derived from the **System.ComponentModel.TypeConverter** or **System.Management.Automation.PSTypeConverter** classes.</span></span>

<span data-ttu-id="0e079-270">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-270">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Type
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-271">-TypeData</span><span class="sxs-lookup"><span data-stu-id="0e079-271">-TypeData</span></span>

<span data-ttu-id="0e079-272">指定此 cmdlet 添加到会话中的类型数据的数组。</span><span class="sxs-lookup"><span data-stu-id="0e079-272">Specifies an array of type data that this cmdlet adds to the session.</span></span> <span data-ttu-id="0e079-273">输入包含 **update-typedata** 对象的变量或获取 **update-typedata** 对象的命令（如 `Get-TypeData` 命令）。</span><span class="sxs-lookup"><span data-stu-id="0e079-273">Enter a variable that contains a **TypeData** object or a command that gets a **TypeData** object, such as a `Get-TypeData` command.</span></span> <span data-ttu-id="0e079-274">还可以通过管道将 **update-typedata** 对象传递给 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-274">You can also pipe a **TypeData** object to `Update-TypeData`.</span></span>

<span data-ttu-id="0e079-275">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.TypeData[]
Parameter Sets: TypeDataSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-276">-TypeName</span><span class="sxs-lookup"><span data-stu-id="0e079-276">-TypeName</span></span>

<span data-ttu-id="0e079-277">指定要扩展的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-277">Specifies the name of the type to extend.</span></span>

<span data-ttu-id="0e079-278">对于 **System** 命名空间中的类型，请输入短名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-278">For types in the **System** namespace, enter the short name.</span></span> <span data-ttu-id="0e079-279">否则，必须输入完整类型名称。</span><span class="sxs-lookup"><span data-stu-id="0e079-279">Otherwise, the full type name is required.</span></span> <span data-ttu-id="0e079-280">不支持通配符。</span><span class="sxs-lookup"><span data-stu-id="0e079-280">Wildcards are not supported.</span></span>

<span data-ttu-id="0e079-281">可以通过管道将类型命名为 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-281">You can pipe type names to `Update-TypeData`.</span></span> <span data-ttu-id="0e079-282">将对象通过管道传递给时 `Update-TypeData` ，将 `Update-TypeData` 获取对象的类型名称，并将数据键入到对象类型。</span><span class="sxs-lookup"><span data-stu-id="0e079-282">When you pipe an object to `Update-TypeData`, `Update-TypeData` gets the type name of the object and type data to the object type.</span></span>

<span data-ttu-id="0e079-283">将此参数与 **MemberName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-283">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="0e079-284">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DynamicTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-285">-Value</span><span class="sxs-lookup"><span data-stu-id="0e079-285">-Value</span></span>

<span data-ttu-id="0e079-286">指定属性或方法的值。</span><span class="sxs-lookup"><span data-stu-id="0e079-286">Specifies the value of the property or method.</span></span>

<span data-ttu-id="0e079-287">如果添加 `AliasProperty` 、 `CodeProperty` 、 `ScriptProperty` 或 `CodeMethod` 成员，则可以使用 **SecondValue** 参数添加其他信息。</span><span class="sxs-lookup"><span data-stu-id="0e079-287">If you add an `AliasProperty`, `CodeProperty`, `ScriptProperty`, or `CodeMethod` member, you can use the **SecondValue** parameter to add additional information.</span></span>

<span data-ttu-id="0e079-288">将此参数与 **MemberName**、**MemberType**、**Value** 和 **SecondValue** 参数一起使用，以添加或更改某个类型的属性或方法。</span><span class="sxs-lookup"><span data-stu-id="0e079-288">Use this parameter with the **MemberName**, **MemberType**, **Value** and **SecondValue** parameters to add or change a property or method of a type.</span></span>

<span data-ttu-id="0e079-289">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="0e079-289">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: DynamicTypeSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-290">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0e079-290">-Confirm</span></span>

<span data-ttu-id="0e079-291">提示你在运行 cmdlet 之前进行确认。</span><span class="sxs-lookup"><span data-stu-id="0e079-291">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-292">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0e079-292">-WhatIf</span></span>

<span data-ttu-id="0e079-293">显示运行该 cmdlet 时会发生什么情况。</span><span class="sxs-lookup"><span data-stu-id="0e079-293">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="0e079-294">此 cmdlet 未运行。</span><span class="sxs-lookup"><span data-stu-id="0e079-294">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0e079-295">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e079-295">CommonParameters</span></span>

<span data-ttu-id="0e079-296">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0e079-296">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0e079-297">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0e079-297">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0e079-298">输入</span><span class="sxs-lookup"><span data-stu-id="0e079-298">Inputs</span></span>

### <span data-ttu-id="0e079-299">System.String</span><span class="sxs-lookup"><span data-stu-id="0e079-299">System.String</span></span>

<span data-ttu-id="0e079-300">可以通过管道将包含 **AppendPath**、 **TypeName** 或 **update-typedata** 参数值的字符串传递给 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="0e079-300">You can pipe a string that contains the values of the **AppendPath**, **TypeName**, or **TypeData** parameters to `Update-TypeData`.</span></span>

## <span data-ttu-id="0e079-301">输出</span><span class="sxs-lookup"><span data-stu-id="0e079-301">Outputs</span></span>

### <span data-ttu-id="0e079-302">无</span><span class="sxs-lookup"><span data-stu-id="0e079-302">None</span></span>

<span data-ttu-id="0e079-303">此 cmdlet 不返回任何输出。</span><span class="sxs-lookup"><span data-stu-id="0e079-303">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="0e079-304">说明</span><span class="sxs-lookup"><span data-stu-id="0e079-304">Notes</span></span>

## <span data-ttu-id="0e079-305">相关链接</span><span class="sxs-lookup"><span data-stu-id="0e079-305">Related links</span></span>

[<span data-ttu-id="0e079-306">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="0e079-306">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="0e079-307">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="0e079-307">Get-TypeData</span></span>](Get-TypeData.md)

[<span data-ttu-id="0e079-308">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="0e079-308">Remove-TypeData</span></span>](Remove-TypeData.md)

