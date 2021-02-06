---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: db5dc586f2a165d83c25bdf2addaeb625f9e1ba0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596403"
---
# <span data-ttu-id="71f8c-102">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="71f8c-102">Get-TypeData</span></span>

## <span data-ttu-id="71f8c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="71f8c-103">Synopsis</span></span>
<span data-ttu-id="71f8c-104">获取当前会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="71f8c-104">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="71f8c-105">语法</span><span class="sxs-lookup"><span data-stu-id="71f8c-105">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="71f8c-106">说明</span><span class="sxs-lookup"><span data-stu-id="71f8c-106">Description</span></span>

<span data-ttu-id="71f8c-107">`Get-TypeData`Cmdlet 将获取当前会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="71f8c-107">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="71f8c-108">这包括通过 `Types.ps1xml` 使用 cmdlet 的参数添加的文件和动态类型数据添加到会话中的类型数据 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="71f8c-108">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="71f8c-109">您可以使用返回的扩展类型数据 `Get-TypeData` 来检查会话中的类型数据，并将其发送到 `Update-TypeData` 和 `Remove-TypeData` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="71f8c-109">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="71f8c-110">扩展类型数据将属性和方法添加到 PowerShell 中的对象。</span><span class="sxs-lookup"><span data-stu-id="71f8c-110">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="71f8c-111">可采用与使用对象类型中所定义的属性和方法相同的方式来使用已添加的属性和方法。</span><span class="sxs-lookup"><span data-stu-id="71f8c-111">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="71f8c-112">但是，在编写脚本时，请注意，已添加的属性和方法可能不会出现在每个 PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="71f8c-112">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="71f8c-113">有关文件的详细信息 `Types.ps1xml` ，请参阅 [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="71f8c-113">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="71f8c-114">有关 cmdlet 添加的动态类型数据的详细信息 `Update-TypeData` ，请参阅 `Update-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="71f8c-114">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="71f8c-115">此 cmdlet 是在 Windows PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="71f8c-115">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="71f8c-116">示例</span><span class="sxs-lookup"><span data-stu-id="71f8c-116">Examples</span></span>

### <span data-ttu-id="71f8c-117">示例1：获取所有扩展类型数据</span><span class="sxs-lookup"><span data-stu-id="71f8c-117">Example 1: Get all extended type data</span></span>

<span data-ttu-id="71f8c-118">此示例获取当前会话中的所有扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="71f8c-118">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="71f8c-119">示例2：按名称获取类型</span><span class="sxs-lookup"><span data-stu-id="71f8c-119">Example 2: Get types by name</span></span>

<span data-ttu-id="71f8c-120">此示例获取当前会话中具有包含事件的名称的所有类型。</span><span class="sxs-lookup"><span data-stu-id="71f8c-120">This example gets all types in the current session that have names that contain Eventing.</span></span>

 ```powershell
"*Eventing*" | Get-TypeData
```

```Output
TypeName                                                  Members
--------                                                  -------
System.Diagnostics.Eventing.Reader.EventLogConfiguration  {}System.Diagnostics.Eventing.Reader.EventLogRecord
                                                          {}System.Diagnostics.Eventing.Reader.ProviderMetadata
                                                          {[ProviderName, System.Management.Automation.Runspaces.AliasProper...
```

### <span data-ttu-id="71f8c-121">示例3：获取创建属性值的脚本块</span><span class="sxs-lookup"><span data-stu-id="71f8c-121">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="71f8c-122">此示例将获取用于创建 **EventLogEntry** 对象的 **EventID** 属性值的脚本块。</span><span class="sxs-lookup"><span data-stu-id="71f8c-122">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="71f8c-123">示例4：获取为指定的对象定义属性的脚本块</span><span class="sxs-lookup"><span data-stu-id="71f8c-123">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="71f8c-124">此示例获取在 PowerShell 中定义 system.exception 对象的 **datetime** 属性 **的脚本** 块。</span><span class="sxs-lookup"><span data-stu-id="71f8c-124">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="71f8c-125">该命令使用 `Get-TypeData` cmdlet 来获取 **DataTime** 类型的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="71f8c-125">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="71f8c-126">该命令将获取 **TypeData** 对象的 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="71f8c-126">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="71f8c-127">**Members** 属性包含一个由扩展类型数据定义的属性和方法的哈希表。</span><span class="sxs-lookup"><span data-stu-id="71f8c-127">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="71f8c-128">Members 哈希表中的每个键均为某个属性或方法名称，每个值均为该属性或方法值的定义。</span><span class="sxs-lookup"><span data-stu-id="71f8c-128">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="71f8c-129">此命令获取 **Members** 中的 **DateTime** 键及其 **GetScriptBlock** 属性值。</span><span class="sxs-lookup"><span data-stu-id="71f8c-129">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="71f8c-130">输出显示脚本块，该脚本块创建 PowerShell 中每个 **system.web** 对象的 **datetime** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="71f8c-130">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="71f8c-131">参数</span><span class="sxs-lookup"><span data-stu-id="71f8c-131">Parameters</span></span>

### <span data-ttu-id="71f8c-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="71f8c-132">-TypeName</span></span>

<span data-ttu-id="71f8c-133">仅将类型数据指定为具有指定名称的类型的数组。</span><span class="sxs-lookup"><span data-stu-id="71f8c-133">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="71f8c-134">默认情况下， `Get-TypeData` 获取会话中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="71f8c-134">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="71f8c-135">输入类型名称或名称模式。</span><span class="sxs-lookup"><span data-stu-id="71f8c-135">Enter type names or a name patterns.</span></span> <span data-ttu-id="71f8c-136">即使对于 System 命名空间中的类型，也需要带有通配符的全名或名称模式。</span><span class="sxs-lookup"><span data-stu-id="71f8c-136">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="71f8c-137">支持通配符，参数名 **TypeName** 是可选的。</span><span class="sxs-lookup"><span data-stu-id="71f8c-137">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="71f8c-138">还可以通过管道将类型命名为 `Get-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="71f8c-138">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="71f8c-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71f8c-139">CommonParameters</span></span>

<span data-ttu-id="71f8c-140">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="71f8c-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71f8c-141">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="71f8c-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71f8c-142">输入</span><span class="sxs-lookup"><span data-stu-id="71f8c-142">Inputs</span></span>

### <span data-ttu-id="71f8c-143">System.String</span><span class="sxs-lookup"><span data-stu-id="71f8c-143">System.String</span></span>

<span data-ttu-id="71f8c-144">可以通过管道将类型命名为 `Get-TypeData` 。</span><span class="sxs-lookup"><span data-stu-id="71f8c-144">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="71f8c-145">输出</span><span class="sxs-lookup"><span data-stu-id="71f8c-145">Outputs</span></span>

### <span data-ttu-id="71f8c-146">System.Management.Automation.Runspaces.TypeData</span><span class="sxs-lookup"><span data-stu-id="71f8c-146">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="71f8c-147">说明</span><span class="sxs-lookup"><span data-stu-id="71f8c-147">Notes</span></span>

<span data-ttu-id="71f8c-148">`Get-TypeData` 仅获取当前会话中的扩展类型数据。</span><span class="sxs-lookup"><span data-stu-id="71f8c-148">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="71f8c-149">它不获取位于计算机上但未添加到当前会话中的扩展类型数据，例如在模块中定义但未导入到当前会话中的扩展类型。</span><span class="sxs-lookup"><span data-stu-id="71f8c-149">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="71f8c-150">相关链接</span><span class="sxs-lookup"><span data-stu-id="71f8c-150">Related links</span></span>

[<span data-ttu-id="71f8c-151">about_Types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="71f8c-151">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="71f8c-152">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="71f8c-152">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="71f8c-153">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="71f8c-153">Update-TypeData</span></span>](Update-TypeData.md)

