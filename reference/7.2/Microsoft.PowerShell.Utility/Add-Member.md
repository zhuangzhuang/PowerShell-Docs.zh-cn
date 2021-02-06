---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-member?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Member
ms.openlocfilehash: 4e9e5ec6d188bec0b4032151fb92e6995d8efbb8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595811"
---
# <span data-ttu-id="9b36c-102">Add-Member</span><span class="sxs-lookup"><span data-stu-id="9b36c-102">Add-Member</span></span>

## <span data-ttu-id="9b36c-103">摘要</span><span class="sxs-lookup"><span data-stu-id="9b36c-103">SYNOPSIS</span></span>
<span data-ttu-id="9b36c-104">将自定义属性和方法添加到 PowerShell 对象的实例。</span><span class="sxs-lookup"><span data-stu-id="9b36c-104">Adds custom properties and methods to an instance of a PowerShell object.</span></span>

## <span data-ttu-id="9b36c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b36c-105">SYNTAX</span></span>

### <span data-ttu-id="9b36c-106">TypeNameSet (默认值) </span><span class="sxs-lookup"><span data-stu-id="9b36c-106">TypeNameSet (Default)</span></span>

```
Add-Member -InputObject <PSObject> -TypeName <String> [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="9b36c-107">NotePropertyMultiMemberSet</span><span class="sxs-lookup"><span data-stu-id="9b36c-107">NotePropertyMultiMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru]
 [-NotePropertyMembers] <IDictionary> [<CommonParameters>]
```

### <span data-ttu-id="9b36c-108">NotePropertySingleMemberSet</span><span class="sxs-lookup"><span data-stu-id="9b36c-108">NotePropertySingleMemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-TypeName <String>] [-Force] [-PassThru] [-NotePropertyName] <String>
 [-NotePropertyValue] <Object> [<CommonParameters>]
```

### <span data-ttu-id="9b36c-109">集</span><span class="sxs-lookup"><span data-stu-id="9b36c-109">MemberSet</span></span>

```
Add-Member -InputObject <PSObject> [-MemberType] <PSMemberTypes> [-Name] <String> [[-Value] <Object>]
 [[-SecondValue] <Object>] [-TypeName <String>] [-Force] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="9b36c-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9b36c-110">DESCRIPTION</span></span>

<span data-ttu-id="9b36c-111">`Add-Member`Cmdlet 允许你向 PowerShell 对象的实例 (属性和方法) 添加成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-111">The `Add-Member` cmdlet lets you add members (properties and methods) to an instance of a PowerShell object.</span></span> <span data-ttu-id="9b36c-112">例如，可以添加包含对象说明的 NoteProperty 成员或运行脚本的 **ScriptMethod** 成员，以更改对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-112">For instance, you can add a NoteProperty member that contains a description of the object or a **ScriptMethod** member that runs a script to change the object.</span></span>

<span data-ttu-id="9b36c-113">若要使用 `Add-Member` ，请将对象传递给 `Add-Member` ，或使用 **InputObject** 参数来指定对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-113">To use `Add-Member`, pipe the object to `Add-Member`, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="9b36c-114">**MemberType** 参数指示要添加的成员的类型。</span><span class="sxs-lookup"><span data-stu-id="9b36c-114">The **MemberType** parameter indicates the type of member that you want to add.</span></span> <span data-ttu-id="9b36c-115">**Name** 参数将名称分配给新成员，**值** 参数设置成员的值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-115">The **Name** parameter assigns a name to the new member, and the **Value** parameter sets the value of the member.</span></span>

<span data-ttu-id="9b36c-116">你添加的属性和方法只会添加到你指定的对象的特定实例中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-116">The properties and methods that you add are added only to the particular instance of the object that you specify.</span></span> <span data-ttu-id="9b36c-117">`Add-Member` 不会更改对象类型。</span><span class="sxs-lookup"><span data-stu-id="9b36c-117">`Add-Member` does not change the object type.</span></span> <span data-ttu-id="9b36c-118">若要创建新的对象类型，请使用 `Add-Type` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b36c-118">To create a new object type, use the `Add-Type` cmdlet.</span></span>

<span data-ttu-id="9b36c-119">你还可以使用 `Export-Clixml` cmdlet 在文件中保存对象的实例，包括其他成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-119">You can also use the `Export-Clixml` cmdlet to save the instance of the object, including the additional members, in a file.</span></span> <span data-ttu-id="9b36c-120">然后，可以使用 `Import-Clixml` cmdlet 从导出文件中存储的信息重新创建对象的实例。</span><span class="sxs-lookup"><span data-stu-id="9b36c-120">Then you can use the `Import-Clixml` cmdlet to re-create the instance of the object from the information that is stored in the exported file.</span></span>

<span data-ttu-id="9b36c-121">从 Windows PowerShell 3.0 开始， `Add-Member` 具有新功能，使你可以更轻松地向对象添加注释属性。</span><span class="sxs-lookup"><span data-stu-id="9b36c-121">Beginning in Windows PowerShell 3.0, `Add-Member` has new features that make it easier to add note properties to objects.</span></span>
<span data-ttu-id="9b36c-122">可以使用 **NotePropertyName** 和 **NotePropertyValue** 参数定义附注属性，或使用 **NotePropertyMembers** 参数，该参数采用包含附注属性名称和值的哈希表。</span><span class="sxs-lookup"><span data-stu-id="9b36c-122">You can use the **NotePropertyName** and **NotePropertyValue** parameters to define a note property or use the **NotePropertyMembers** parameter, which takes a hash table of note property names and values.</span></span>

<span data-ttu-id="9b36c-123">此外，从 Windows PowerShell 3.0 开始，将很少需要使用用于生成输出对象的 **PassThru** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-123">Also, beginning in Windows PowerShell 3.0, the **PassThru** parameter, which generates an output object, is needed less frequently.</span></span> <span data-ttu-id="9b36c-124">`Add-Member` 现在将新成员直接添加到更多类型的输入对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-124">`Add-Member` now adds the new members directly to the input object of more types.</span></span> <span data-ttu-id="9b36c-125">有关详细信息，请参阅 **PassThru** 参数说明。</span><span class="sxs-lookup"><span data-stu-id="9b36c-125">For more information, see the **PassThru** parameter description.</span></span>

## <span data-ttu-id="9b36c-126">示例</span><span class="sxs-lookup"><span data-stu-id="9b36c-126">EXAMPLES</span></span>

### <span data-ttu-id="9b36c-127">示例1：向 PSObject 添加注释属性</span><span class="sxs-lookup"><span data-stu-id="9b36c-127">Example 1: Add a note property to a PSObject</span></span>

<span data-ttu-id="9b36c-128">下面的示例将值为 "Done" 的 **状态** 注释属性添加到表示该文件的 **FileInfo** 对象 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-128">The following example adds a **Status** note property with a value of "Done" to the **FileInfo** object that represents the `Test.txt` file.</span></span>

<span data-ttu-id="9b36c-129">第一个命令使用 `Get-ChildItem` cmdlet 来获取表示该文件的 **FileInfo** 对象 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-129">The first command uses the `Get-ChildItem` cmdlet to get a **FileInfo** object representing the `Test.txt` file.</span></span> <span data-ttu-id="9b36c-130">它将其保存在 `$a` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-130">It saves it in the `$a` variable.</span></span>

<span data-ttu-id="9b36c-131">第二个命令将 note 属性添加到中的对象 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-131">The second command adds the note property to the object in `$a`.</span></span>

<span data-ttu-id="9b36c-132">第三个命令使用点表示法来获取中对象的 **Status** 属性的值 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-132">The third command uses dot notation to get the value of the **Status** property of the object in `$a`.</span></span> <span data-ttu-id="9b36c-133">如输出所示，值为 "Done"。</span><span class="sxs-lookup"><span data-stu-id="9b36c-133">As the output shows, the value is "Done".</span></span>

```powershell
$A = Get-ChildItem c:\ps-test\test.txt
$A | Add-Member -NotePropertyName Status -NotePropertyValue Done
$A.Status
```

```Output
Done
```

### <span data-ttu-id="9b36c-134">示例2：向 PSObject 添加 alias 属性</span><span class="sxs-lookup"><span data-stu-id="9b36c-134">Example 2: Add an alias property to a PSObject</span></span>

<span data-ttu-id="9b36c-135">下面的示例将一个 **Size** alias 属性添加到表示该文件的对象 `Test.txt` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-135">The following example adds a **Size** alias property to the object that represents the `Test.txt` file.</span></span> <span data-ttu-id="9b36c-136">新属性是 **Length** 属性的别名。</span><span class="sxs-lookup"><span data-stu-id="9b36c-136">The new property is an alias for the **Length** property.</span></span>

<span data-ttu-id="9b36c-137">第一个命令使用 `Get-ChildItem` cmdlet 来获取 `Test.txt` **FileInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-137">The first command uses the `Get-ChildItem` cmdlet to get the `Test.txt` **FileInfo** object.</span></span>

<span data-ttu-id="9b36c-138">第二个命令添加 **Size** alias 属性。</span><span class="sxs-lookup"><span data-stu-id="9b36c-138">The second command adds the **Size** alias property.</span></span>
<span data-ttu-id="9b36c-139">第三个命令使用点表示法来获取新的 **Size** 属性的值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-139">The third command uses dot notation to get the value of the new **Size** property.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$A | Add-Member -MemberType AliasProperty -Name Size -Value Length
$A.Size
```

```Output
2394
```

### <span data-ttu-id="9b36c-140">示例3：向字符串添加 StringUse 注释属性</span><span class="sxs-lookup"><span data-stu-id="9b36c-140">Example 3: Add a StringUse note property to a string</span></span>

<span data-ttu-id="9b36c-141">此示例将 **StringUse** note 属性添加到字符串。</span><span class="sxs-lookup"><span data-stu-id="9b36c-141">This example adds the **StringUse** note property to a string.</span></span>
<span data-ttu-id="9b36c-142">由于 `Add-Member` 无法将类型添加到 **字符串** 输入对象，因此可以指定 **PassThru** 参数来生成输出对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-142">Because `Add-Member` cannot add types to **String** input objects, you can specify the **PassThru** parameter to generate an output object.</span></span> <span data-ttu-id="9b36c-143">示例中的最后一个命令将显示新属性。</span><span class="sxs-lookup"><span data-stu-id="9b36c-143">The last command in the example displays the new property.</span></span>

<span data-ttu-id="9b36c-144">此示例使用 **NotePropertyMembers** 参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-144">This example uses the **NotePropertyMembers** parameter.</span></span> <span data-ttu-id="9b36c-145">**NotePropertyMembers** 参数的值是一个哈希表。</span><span class="sxs-lookup"><span data-stu-id="9b36c-145">The value of the **NotePropertyMembers** parameter is a hash table.</span></span> <span data-ttu-id="9b36c-146">键为便笺属性名称 **StringUse**，值为 "注释" 属性值 " **显示**"。</span><span class="sxs-lookup"><span data-stu-id="9b36c-146">The key is the note property name, **StringUse**, and the value is the note property value, **Display**.</span></span>

```powershell
$A = "A string"
$A = $A | Add-Member -NotePropertyMembers @{StringUse="Display"} -PassThru
$A.StringUse
```

```Output
Display
```

### <span data-ttu-id="9b36c-147">示例4：将脚本方法添加到 FileInfo 对象</span><span class="sxs-lookup"><span data-stu-id="9b36c-147">Example 4: Add a script method to a FileInfo object</span></span>

<span data-ttu-id="9b36c-148">此示例将 **SizeInMB** 脚本方法添加到 **FileInfo** 对象，该对象将文件大小计算为最接近的兆字节。</span><span class="sxs-lookup"><span data-stu-id="9b36c-148">This example adds the **SizeInMB** script method to a **FileInfo** object which calculates the file size to the nearest MegaByte.</span></span> <span data-ttu-id="9b36c-149">第二个命令创建一个 **ScriptBlock** ，该 ScriptBlock 使用类型中的 **循环** 静态方法将 `[math]` 文件大小舍入到第二个小数位。</span><span class="sxs-lookup"><span data-stu-id="9b36c-149">The second command creates a **ScriptBlock** that uses the **Round** static method from the `[math]` type to round the file size to the second decimal place.</span></span>

<span data-ttu-id="9b36c-150">**Value** 参数还使用 `$This` 自动变量，它表示当前的对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-150">The **Value** parameter also uses the `$This` automatic variable, which represents the current object.</span></span> <span data-ttu-id="9b36c-151">`$This`变量仅在定义新属性和方法的脚本块中有效。</span><span class="sxs-lookup"><span data-stu-id="9b36c-151">The `$This` variable is valid only in script blocks that define new properties and methods.</span></span>

<span data-ttu-id="9b36c-152">最后一个命令使用点表示法对变量中的对象调用新的 **SizeInMB** 脚本方法 `$A` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-152">The last command uses dot notation to call the new **SizeInMB** script method on the object in the `$A` variable.</span></span>

```powershell
$A = Get-ChildItem C:\Temp\test.txt
$S = {[math]::Round(($this.Length / 1MB), 2)}
$A | Add-Member -MemberType ScriptMethod -Name "SizeInMB" -Value $S
$A.SizeInMB()
```

```Output
0.43
```

### <span data-ttu-id="9b36c-153">示例5：将对象的所有属性复制到另一个</span><span class="sxs-lookup"><span data-stu-id="9b36c-153">Example 5: Copy all properties of an object to another</span></span>

<span data-ttu-id="9b36c-154">此函数将一个对象的所有属性复制到另一个对象中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-154">This function copies all of the properties of one object to another object.</span></span>

<span data-ttu-id="9b36c-155">`foreach`循环使用 `Get-Member` cmdlet **从** 对象获取的每个属性。</span><span class="sxs-lookup"><span data-stu-id="9b36c-155">The `foreach` loop uses the `Get-Member` cmdlet to get each of the properties of the **From** object.</span></span> <span data-ttu-id="9b36c-156">循环内的命令 `foreach` 在每个属性上以序列的顺序执行。</span><span class="sxs-lookup"><span data-stu-id="9b36c-156">The commands within the `foreach` loop are performed in series on each of the properties.</span></span>

<span data-ttu-id="9b36c-157">`Add-Member`命令将 **从** 对象的属性作为 **NoteProperty** 添加到对象 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-157">The `Add-Member` command adds the property of the **From** object to the **To** object as a **NoteProperty**.</span></span> <span data-ttu-id="9b36c-158">使用 **value** 参数复制值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-158">The value is copied using the **Value** parameter.</span></span> <span data-ttu-id="9b36c-159">它使用 **Force** 参数添加具有相同成员名称的成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-159">It uses the **Force** parameter to add members with the same member name.</span></span>

```powershell
function Copy-Property ($From, $To)
{
    $properties = Get-Member -InputObject $From -MemberType Property
    foreach ($p in $properties)
    {
        $To | Add-Member -MemberType NoteProperty -Name $p.Name -Value $From.$($p.Name) -Force
    }
}
```

### <span data-ttu-id="9b36c-160">示例6：创建自定义对象</span><span class="sxs-lookup"><span data-stu-id="9b36c-160">Example 6: Create a custom object</span></span>

<span data-ttu-id="9b36c-161">此示例将创建一个 **资产** 自定义对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-161">This example creates an **Asset** custom object.</span></span>

<span data-ttu-id="9b36c-162">`New-Object`Cmdlet 将创建 **PSObject**。</span><span class="sxs-lookup"><span data-stu-id="9b36c-162">The `New-Object` cmdlet creates a **PSObject**.</span></span> <span data-ttu-id="9b36c-163">该示例将 **PSObject** 保存在 `$Asset` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-163">The example saves the **PSObject** in the `$Asset` variable.</span></span>

<span data-ttu-id="9b36c-164">第二个命令使用 `[ordered]` 类型加速器创建名称和值的有序字典。</span><span class="sxs-lookup"><span data-stu-id="9b36c-164">The second command uses the `[ordered]` type accelerator to create an ordered dictionary of names and values.</span></span> <span data-ttu-id="9b36c-165">该命令将结果保存在 `$D` 变量中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-165">The command saves the result in the `$D` variable.</span></span>

<span data-ttu-id="9b36c-166">第三个命令使用 cmdlet 的 **NotePropertyMembers** 参数 `Add-Member` 将变量中的字典添加 `$D` 到 **PSObject**。</span><span class="sxs-lookup"><span data-stu-id="9b36c-166">The third command uses the **NotePropertyMembers** parameter of the `Add-Member` cmdlet to add the dictionary in the `$D` variable to the **PSObject**.</span></span>
<span data-ttu-id="9b36c-167">**TypeName** 属性将新名称、**资产** 分配给 **PSObject**。</span><span class="sxs-lookup"><span data-stu-id="9b36c-167">The **TypeName** property assigns a new name, **Asset**, to the **PSObject**.</span></span>

<span data-ttu-id="9b36c-168">最后一个命令通过管道将新的 **资产** 对象传递给 `Get-Member` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b36c-168">The last command pipes the new **Asset** object to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="9b36c-169">该输出显示该对象具有类型名称 " **资产** " 和在 "排序字典" 中定义的附注属性。</span><span class="sxs-lookup"><span data-stu-id="9b36c-169">The output shows that the object has a type name of **Asset** and the note properties that we defined in the ordered dictionary.</span></span>

```powershell
$Asset = New-Object -TypeName PSObject
$d = [ordered]@{Name="Server30";System="Server Core";PSVersion="4.0"}
$Asset | Add-Member -NotePropertyMembers $d -TypeName Asset
$Asset | Get-Member
```

```Output
   TypeName: Asset

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty System.String Name=Server30
PSVersion   NoteProperty System.String PSVersion=4.0
System      NoteProperty System.String System=Server Core
```

## <span data-ttu-id="9b36c-170">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9b36c-170">PARAMETERS</span></span>

### <span data-ttu-id="9b36c-171">-Force</span><span class="sxs-lookup"><span data-stu-id="9b36c-171">-Force</span></span>

<span data-ttu-id="9b36c-172">指示此 cmdlet 添加新成员，即使该对象具有同名的自定义成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-172">Indicates that this cmdlet adds a new member even the object has a custom member with the same name.</span></span>
<span data-ttu-id="9b36c-173">不能使用 **Force** 参数来替换类型的标准成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-173">You cannot use the **Force** parameter to replace a standard member of a type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MemberSet, NotePropertySingleMemberSet, NotePropertyMultiMemberSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-174">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9b36c-174">-InputObject</span></span>

<span data-ttu-id="9b36c-175">指定要向其添加新成员的对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-175">Specifies the object to which the new member is added.</span></span>
<span data-ttu-id="9b36c-176">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="9b36c-176">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-177">-MemberType</span><span class="sxs-lookup"><span data-stu-id="9b36c-177">-MemberType</span></span>

<span data-ttu-id="9b36c-178">指定要添加的成员的类型。</span><span class="sxs-lookup"><span data-stu-id="9b36c-178">Specifies the type of the member to add.</span></span>
<span data-ttu-id="9b36c-179">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="9b36c-179">This parameter is required.</span></span>
<span data-ttu-id="9b36c-180">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="9b36c-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9b36c-181">NoteProperty</span><span class="sxs-lookup"><span data-stu-id="9b36c-181">NoteProperty</span></span>
- <span data-ttu-id="9b36c-182">AliasProperty</span><span class="sxs-lookup"><span data-stu-id="9b36c-182">AliasProperty</span></span>
- <span data-ttu-id="9b36c-183">ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="9b36c-183">ScriptProperty</span></span>
- <span data-ttu-id="9b36c-184">CodeProperty</span><span class="sxs-lookup"><span data-stu-id="9b36c-184">CodeProperty</span></span>
- <span data-ttu-id="9b36c-185">ScriptMethod</span><span class="sxs-lookup"><span data-stu-id="9b36c-185">ScriptMethod</span></span>
- <span data-ttu-id="9b36c-186">CodeMethod</span><span class="sxs-lookup"><span data-stu-id="9b36c-186">CodeMethod</span></span>

<span data-ttu-id="9b36c-187">有关这些值的信息，请参阅 PowerShell SDK 中的 [PSMemberTypes 枚举](/dotnet/api/system.management.automation.psmembertypes) 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-187">For information about these values, see [PSMemberTypes Enumeration](/dotnet/api/system.management.automation.psmembertypes) in the PowerShell SDK.</span></span>

<span data-ttu-id="9b36c-188">并非所有对象都具有每种类型的成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-188">Not all objects have every type of member.</span></span>
<span data-ttu-id="9b36c-189">如果指定了对象不具有的成员类型，则 PowerShell 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="9b36c-189">If you specify a member type that the object does not have, PowerShell returns an error.</span></span>

```yaml
Type: System.Management.Automation.PSMemberTypes
Parameter Sets: MemberSet
Aliases: Type
Accepted values: AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, Event, Dynamic, All

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-190">-Name</span><span class="sxs-lookup"><span data-stu-id="9b36c-190">-Name</span></span>

<span data-ttu-id="9b36c-191">指定此 cmdlet 添加的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="9b36c-191">Specifies the name of the member that this cmdlet adds.</span></span>

```yaml
Type: System.String
Parameter Sets: MemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-192">-NotePropertyMembers</span><span class="sxs-lookup"><span data-stu-id="9b36c-192">-NotePropertyMembers</span></span>

<span data-ttu-id="9b36c-193">指定附注属性名称和值的哈希表或有序字典。</span><span class="sxs-lookup"><span data-stu-id="9b36c-193">Specifies a hash table or ordered dictionary of note property names and values.</span></span>
<span data-ttu-id="9b36c-194">键入哈希表或字典，其中的键为附注属性名称，值为附注属性值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-194">Type a hash table or dictionary in which the keys are note property names and the values are note property values.</span></span>

<span data-ttu-id="9b36c-195">有关 PowerShell 中的哈希表和有序字典的详细信息，请参阅 [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)。</span><span class="sxs-lookup"><span data-stu-id="9b36c-195">For more information about hash tables and ordered dictionaries in PowerShell, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="9b36c-196">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-196">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: NotePropertyMultiMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-197">-NotePropertyName</span><span class="sxs-lookup"><span data-stu-id="9b36c-197">-NotePropertyName</span></span>

<span data-ttu-id="9b36c-198">指定便笺属性名称。</span><span class="sxs-lookup"><span data-stu-id="9b36c-198">Specifies the note property name.</span></span>

<span data-ttu-id="9b36c-199">将此参数与 **NotePropertyValue** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="9b36c-199">Use this parameter with the **NotePropertyValue** parameter.</span></span>
<span data-ttu-id="9b36c-200">此参数可选。</span><span class="sxs-lookup"><span data-stu-id="9b36c-200">This parameter is optional.</span></span>

<span data-ttu-id="9b36c-201">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-202">-NotePropertyValue</span><span class="sxs-lookup"><span data-stu-id="9b36c-202">-NotePropertyValue</span></span>

<span data-ttu-id="9b36c-203">指定 note 属性值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-203">Specifies the note property value.</span></span>

<span data-ttu-id="9b36c-204">将此参数与 **NotePropertyName** 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="9b36c-204">Use this parameter with the **NotePropertyName** parameter.</span></span>
<span data-ttu-id="9b36c-205">此参数可选。</span><span class="sxs-lookup"><span data-stu-id="9b36c-205">This parameter is optional.</span></span>

<span data-ttu-id="9b36c-206">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: NotePropertySingleMemberSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-207">-PassThru</span><span class="sxs-lookup"><span data-stu-id="9b36c-207">-PassThru</span></span>

<span data-ttu-id="9b36c-208">返回一个代表你所处理的项目的对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-208">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="9b36c-209">默认情况下，此 cmdlet 将不产生任何输出。</span><span class="sxs-lookup"><span data-stu-id="9b36c-209">By default, this cmdlet does not generate any output.</span></span>

<span data-ttu-id="9b36c-210">对于大多数对象，会 `Add-Member` 将新成员添加到输入对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-210">For most objects, `Add-Member` adds the new members to the input object.</span></span>
<span data-ttu-id="9b36c-211">但是，当输入对象是一个字符串时， `Add-Member` 不能将该成员添加到 input 对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-211">However, when the input object is a string, `Add-Member` cannot add the member to the input object.</span></span>
<span data-ttu-id="9b36c-212">对于这些对象，请使用 **PassThru** 参数来创建输出对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-212">For these objects, use the **PassThru** parameter to create an output object.</span></span>

<span data-ttu-id="9b36c-213">在 Windows PowerShell 2.0 中， `Add-Member` 只将成员添加到了对象的 **PSObject** 包装，而不是添加到对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-213">In Windows PowerShell 2.0, `Add-Member` added members only to the **PSObject** wrapper of objects, not to the object.</span></span>
<span data-ttu-id="9b36c-214">使用 **PassThru** 参数为具有 **PSObject** 包装器的任何对象创建输出对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-214">Use the **PassThru** parameter to create an output object for any object that has a **PSObject** wrapper.</span></span>

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

### <span data-ttu-id="9b36c-215">-SecondValue</span><span class="sxs-lookup"><span data-stu-id="9b36c-215">-SecondValue</span></span>

<span data-ttu-id="9b36c-216">指定有关 **AliasProperty**、**ScriptProperty**、**CodeProperty** 或 **CodeMethod** 成员的可选附加信息。</span><span class="sxs-lookup"><span data-stu-id="9b36c-216">Specifies optional additional information about **AliasProperty**, **ScriptProperty**, **CodeProperty**, or **CodeMethod** members.</span></span>

<span data-ttu-id="9b36c-217">如果在添加 **AliasProperty** 时使用此参数，则此参数必须为数据类型。</span><span class="sxs-lookup"><span data-stu-id="9b36c-217">If used when adding an **AliasProperty**, this parameter must be a data type.</span></span>
<span data-ttu-id="9b36c-218">到指定数据类型的转换将添加到 **AliasProperty** 的值中。</span><span class="sxs-lookup"><span data-stu-id="9b36c-218">A conversion to the specified data type is added to the value of the **AliasProperty**.</span></span>

<span data-ttu-id="9b36c-219">例如，如果添加了为字符串属性提供备用名称的 **AliasProperty** ，则还可以指定 **SecondValue** 参数，以指示在使用相应的 **AliasProperty** 进行访问时，应将该字符串属性的值转换为 **整数。**</span><span class="sxs-lookup"><span data-stu-id="9b36c-219">For example, if you add an **AliasProperty** that provides an alternate name for a string property, you can also specify a **SecondValue** parameter of **System.Int32** to indicate that the value of that string property should be converted to an integer when accessed by using the corresponding **AliasProperty**.</span></span>

<span data-ttu-id="9b36c-220">添加 **ScriptProperty** 成员时，可以使用 **SecondValue** 参数来指定其他 **ScriptBlock** 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-220">You can use the **SecondValue** parameter to specify an additional **ScriptBlock** when adding a **ScriptProperty** member.</span></span> <span data-ttu-id="9b36c-221">在 **Value** 参数中指定的第一个 **ScriptBlock** 用于获取变量的值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-221">The first **ScriptBlock**, specified in the **Value** parameter, is used to get the value of a variable.</span></span> <span data-ttu-id="9b36c-222">在 **SecondValue** 参数中指定的第二个 **ScriptBlock** 用于设置变量的值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-222">The second **ScriptBlock**, specified in the **SecondValue** parameter, is used to set the value of a variable.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-223">-Value</span><span class="sxs-lookup"><span data-stu-id="9b36c-223">-Value</span></span>

<span data-ttu-id="9b36c-224">指定已添加成员的初始值。</span><span class="sxs-lookup"><span data-stu-id="9b36c-224">Specifies the initial value of the added member.</span></span>
<span data-ttu-id="9b36c-225">如果添加了 **AliasProperty**、 **CodeProperty**、 **ScriptProperty** 或 **CodeMethod** 成员，则可以使用 **SecondValue** 参数提供可选的附加信息。</span><span class="sxs-lookup"><span data-stu-id="9b36c-225">If you add an **AliasProperty**, **CodeProperty**, **ScriptProperty** or **CodeMethod** member, you can supply optional, additional information by using the **SecondValue** parameter.</span></span>

```yaml
Type: System.Object
Parameter Sets: MemberSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-226">-TypeName</span><span class="sxs-lookup"><span data-stu-id="9b36c-226">-TypeName</span></span>

<span data-ttu-id="9b36c-227">指定类型的名称。</span><span class="sxs-lookup"><span data-stu-id="9b36c-227">Specifies a name for the type.</span></span>

<span data-ttu-id="9b36c-228">如果类型是 **System** 命名空间中的类或具有类型加速器的类型，则可以输入类型的短名称。</span><span class="sxs-lookup"><span data-stu-id="9b36c-228">When the type is a class in the **System** namespace or a type that has a type accelerator, you can enter the short name of the type.</span></span> <span data-ttu-id="9b36c-229">否则，必须输入完整类型名称。</span><span class="sxs-lookup"><span data-stu-id="9b36c-229">Otherwise, the full type name is required.</span></span>
<span data-ttu-id="9b36c-230">仅当 **InputObject** 为 **PSObject** 时，此参数才有效。</span><span class="sxs-lookup"><span data-stu-id="9b36c-230">This parameter is effective only when the **InputObject** is a **PSObject**.</span></span>

<span data-ttu-id="9b36c-231">已在 Windows PowerShell 3.0 中引入了此参数。</span><span class="sxs-lookup"><span data-stu-id="9b36c-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: TypeNameSet, NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet
Aliases:

Required: True (TypeNameSet), False (NotePropertyMultiMemberSet, NotePropertySingleMemberSet, MemberSet)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b36c-232">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b36c-232">CommonParameters</span></span>

<span data-ttu-id="9b36c-233">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9b36c-233">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b36c-234">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="9b36c-234">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9b36c-235">输入</span><span class="sxs-lookup"><span data-stu-id="9b36c-235">INPUTS</span></span>

### <span data-ttu-id="9b36c-236">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9b36c-236">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9b36c-237">可以通过管道将任何对象类型传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b36c-237">You can pipe any object type to this cmdlet.</span></span>

## <span data-ttu-id="9b36c-238">输出</span><span class="sxs-lookup"><span data-stu-id="9b36c-238">OUTPUTS</span></span>

### <span data-ttu-id="9b36c-239">None 或 system.string</span><span class="sxs-lookup"><span data-stu-id="9b36c-239">None or System.Object</span></span>

<span data-ttu-id="9b36c-240">当使用 **PassThru** 参数时，此 cmdlet 将返回新扩展的对象。</span><span class="sxs-lookup"><span data-stu-id="9b36c-240">When you use the **PassThru** parameter, this cmdlet returns the newly-extended object.</span></span>
<span data-ttu-id="9b36c-241">否则，此 cmdlet 将不生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="9b36c-241">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9b36c-242">注释</span><span class="sxs-lookup"><span data-stu-id="9b36c-242">NOTES</span></span>

<span data-ttu-id="9b36c-243">只能向 **PSObject** 对象添加成员。</span><span class="sxs-lookup"><span data-stu-id="9b36c-243">You can add members only to **PSObject** objects.</span></span> <span data-ttu-id="9b36c-244">若要确定某个对象是否为 **PSObject** 对象，请使用 `-is` 运算符。</span><span class="sxs-lookup"><span data-stu-id="9b36c-244">To determine whether an object is a **PSObject** object, use the `-is` operator.</span></span>

<span data-ttu-id="9b36c-245">例如，若要测试变量中存储的对象 `$obj` ，请键入 `$obj -is [PSObject]` 。</span><span class="sxs-lookup"><span data-stu-id="9b36c-245">For instance, to test an object stored in the `$obj` variable, type `$obj -is [PSObject]`.</span></span>

<span data-ttu-id="9b36c-246">**MemberType**、 **Name**、 **Value** 和 **SecondValue** 参数的名称是可选的。</span><span class="sxs-lookup"><span data-stu-id="9b36c-246">The names of the **MemberType**, **Name**, **Value**, and **SecondValue** parameters are optional.</span></span>
<span data-ttu-id="9b36c-247">如果省略参数名称，则未命名参数值必须按以下顺序出现： " **MemberType**"、" **Name**"、" **Value**" 和 " **SecondValue**"。</span><span class="sxs-lookup"><span data-stu-id="9b36c-247">If you omit the parameter names, the unnamed parameter values must appear in this order: **MemberType**, **Name**, **Value**, and **SecondValue**.</span></span>

<span data-ttu-id="9b36c-248">如果包括参数名称，则参数能够以任何顺序出现。</span><span class="sxs-lookup"><span data-stu-id="9b36c-248">If you include the parameter names, the parameters can appear in any order.</span></span>

<span data-ttu-id="9b36c-249">可以 `$this` 在定义新属性和方法的值的脚本块中使用自动变量。</span><span class="sxs-lookup"><span data-stu-id="9b36c-249">You can use the `$this` automatic variable in script blocks that define the values of new properties and methods.</span></span>
<span data-ttu-id="9b36c-250">`$this`变量引用要向其中添加属性和方法的对象的实例。</span><span class="sxs-lookup"><span data-stu-id="9b36c-250">The `$this` variable refers to the instance of the object to which the properties and methods are being added.</span></span> <span data-ttu-id="9b36c-251">有关变量的详细信息 `$this` ，请参阅 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="9b36c-251">For more information about the `$this` variable, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="9b36c-252">相关链接</span><span class="sxs-lookup"><span data-stu-id="9b36c-252">RELATED LINKS</span></span>

[<span data-ttu-id="9b36c-253">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="9b36c-253">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="9b36c-254">Get-Member</span><span class="sxs-lookup"><span data-stu-id="9b36c-254">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="9b36c-255">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="9b36c-255">Import-Clixml</span></span>](Import-Clixml.md)

[<span data-ttu-id="9b36c-256">New-Object</span><span class="sxs-lookup"><span data-stu-id="9b36c-256">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="9b36c-257">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="9b36c-257">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

