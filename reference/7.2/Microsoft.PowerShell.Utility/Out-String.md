---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 59e5b728604ce37f27b56ebe62e1a22d6af8a966
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/21/2021
ms.locfileid: "99597251"
---
# <span data-ttu-id="bff71-102">Out-String</span><span class="sxs-lookup"><span data-stu-id="bff71-102">Out-String</span></span>

## <span data-ttu-id="bff71-103">摘要</span><span class="sxs-lookup"><span data-stu-id="bff71-103">Synopsis</span></span>
<span data-ttu-id="bff71-104">将输入对象输出为字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-104">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="bff71-105">语法</span><span class="sxs-lookup"><span data-stu-id="bff71-105">Syntax</span></span>

### <span data-ttu-id="bff71-106">NoNewLineFormatting (默认值) </span><span class="sxs-lookup"><span data-stu-id="bff71-106">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="bff71-107">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="bff71-107">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="bff71-108">说明</span><span class="sxs-lookup"><span data-stu-id="bff71-108">Description</span></span>

<span data-ttu-id="bff71-109">`Out-String`Cmdlet 将输入对象转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="bff71-110">默认情况下， `Out-String` 累积字符串并将它们作为单个字符串返回，但你可以使用 **Stream** 参数定向 `Out-String` 到一次返回一行或创建字符串数组。</span><span class="sxs-lookup"><span data-stu-id="bff71-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="bff71-111">此 cmdlet 用于在对象操作不太方便时像在传统 shell 中一样搜索和操作字符串输出。</span><span class="sxs-lookup"><span data-stu-id="bff71-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="bff71-112">示例</span><span class="sxs-lookup"><span data-stu-id="bff71-112">Examples</span></span>

### <span data-ttu-id="bff71-113">示例1：获取当前区域性并将数据转换为字符串</span><span class="sxs-lookup"><span data-stu-id="bff71-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="bff71-114">此示例获取当前用户的区域设置，并将对象数据转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="bff71-115">`$C`变量存储 **Selected.System。全球化 CultureInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="bff71-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="bff71-116">对象是将 `Get-Culture` 管道的输出发送到的结果 `Select-Object` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="bff71-117">**Property** 参数使用星号 (`*`) 通配符来指定对象中包含的所有属性。</span><span class="sxs-lookup"><span data-stu-id="bff71-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="bff71-118">`Out-String` 使用 **InputObject** 参数指定存储在变量中的 **CultureInfo** 对象 `$C` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="bff71-119">中的对象 `$C` 将转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="bff71-120">若要查看 `Out-String` 数组，请将输出存储到变量中，并使用数组索引来查看元素。</span><span class="sxs-lookup"><span data-stu-id="bff71-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="bff71-121">有关数组索引的详细信息，请参阅 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="bff71-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="bff71-122">示例2：使用对象</span><span class="sxs-lookup"><span data-stu-id="bff71-122">Example 2: Working with objects</span></span>

<span data-ttu-id="bff71-123">此示例演示了使用对象和使用字符串之间的差异。</span><span class="sxs-lookup"><span data-stu-id="bff71-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="bff71-124">该命令显示一个别名，其中包含文本 **gcm**（的别名） `Get-Command` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-124">The command displays an alias that includes the text **gcm**, the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="bff71-125">`Get-Alias` 获取每个别名的 **system.management.automation.aliasinfo** 对象，并沿管道向下发送对象。</span><span class="sxs-lookup"><span data-stu-id="bff71-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="bff71-126">`Out-String` 使用 **Stream** 参数将每个对象转换为字符串，而不是将所有对象连接到一个字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="bff71-127">**系统** 对象将沿管道向下发送，并 `Select-String` 使用 **Pattern** 参数查找文本 **gcm** 的匹配项。</span><span class="sxs-lookup"><span data-stu-id="bff71-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="bff71-128">如果省略 **Stream** 参数，则该命令将显示所有别名，因为 `Select-String` 在返回的单个字符串中查找文本 gcm `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="bff71-129">示例3：使用 Width 参数防止截断。</span><span class="sxs-lookup"><span data-stu-id="bff71-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="bff71-130">虽然中的大部分输出 `Out-String` 都被包装到下一行，但在某些情况下，输出在传递到之前会被格式化系统截断 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="bff71-131">使用 **Width** 参数可避免截断。</span><span class="sxs-lookup"><span data-stu-id="bff71-131">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="bff71-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bff71-132">PARAMETERS</span></span>

### <span data-ttu-id="bff71-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="bff71-133">-InputObject</span></span>

<span data-ttu-id="bff71-134">指定要写入字符串的对象。</span><span class="sxs-lookup"><span data-stu-id="bff71-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="bff71-135">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="bff71-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="bff71-136">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="bff71-136">-NoNewline</span></span>

<span data-ttu-id="bff71-137">从 PowerShell 格式化程序生成的输出中删除所有换行符。</span><span class="sxs-lookup"><span data-stu-id="bff71-137">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="bff71-138">保留作为字符串对象一部分的换行符。</span><span class="sxs-lookup"><span data-stu-id="bff71-138">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="bff71-139">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="bff71-139">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bff71-140">-Stream</span><span class="sxs-lookup"><span data-stu-id="bff71-140">-Stream</span></span>

<span data-ttu-id="bff71-141">默认情况下，将 `Out-String` 输出单个字符串的格式，如您在控制台中所看到的那样，其中包括任何空白标头或尾随换行符。</span><span class="sxs-lookup"><span data-stu-id="bff71-141">By default, `Out-String` outputs a single string formatted as you would see it in the console including any blank headers or trailing newlines.</span></span> <span data-ttu-id="bff71-142">**Stream** 参数使 `Out-String` 能够逐个输出每一行。</span><span class="sxs-lookup"><span data-stu-id="bff71-142">The **Stream** parameter enables `Out-String` to output each line one by one.</span></span> <span data-ttu-id="bff71-143">唯一的例外是多行字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-143">The only exception to this are multiline strings.</span></span> <span data-ttu-id="bff71-144">在这种情况下， `Out-String` 仍会将字符串输出为单个多行字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-144">In that case, `Out-String` will still output the string as a single, multiline string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bff71-145">-Width</span><span class="sxs-lookup"><span data-stu-id="bff71-145">-Width</span></span>

<span data-ttu-id="bff71-146">指定输出的每一行中的字符数。</span><span class="sxs-lookup"><span data-stu-id="bff71-146">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="bff71-147">任何其他字符将换行到下一行，或根据所使用的格式化程序 cmdlet 进行截断。</span><span class="sxs-lookup"><span data-stu-id="bff71-147">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="bff71-148">**Width** 参数仅适用于正在设置格式的对象。</span><span class="sxs-lookup"><span data-stu-id="bff71-148">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="bff71-149">如果省略此参数，则由主机程序的特征确定宽度。</span><span class="sxs-lookup"><span data-stu-id="bff71-149">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="bff71-150">在终端 (console) windows 中，当前窗口宽度用作默认值。</span><span class="sxs-lookup"><span data-stu-id="bff71-150">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="bff71-151">默认情况下，在安装时，PowerShell 控制台 windows 的宽度为80个字符。</span><span class="sxs-lookup"><span data-stu-id="bff71-151">PowerShell console windows default to a width of 80 characters on installation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bff71-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bff71-152">CommonParameters</span></span>

<span data-ttu-id="bff71-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bff71-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bff71-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bff71-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bff71-155">输入</span><span class="sxs-lookup"><span data-stu-id="bff71-155">INPUTS</span></span>

### <span data-ttu-id="bff71-156">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="bff71-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bff71-157">可以将对象向下发送到 `Out-String` 。</span><span class="sxs-lookup"><span data-stu-id="bff71-157">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="bff71-158">输出</span><span class="sxs-lookup"><span data-stu-id="bff71-158">OUTPUTS</span></span>

### <span data-ttu-id="bff71-159">System.String</span><span class="sxs-lookup"><span data-stu-id="bff71-159">System.String</span></span>

<span data-ttu-id="bff71-160">`Out-String` 返回它通过输入对象创建的字符串。</span><span class="sxs-lookup"><span data-stu-id="bff71-160">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="bff71-161">注释</span><span class="sxs-lookup"><span data-stu-id="bff71-161">NOTES</span></span>

<span data-ttu-id="bff71-162">包含谓词的 cmdlet `Out` 不设置对象的格式。</span><span class="sxs-lookup"><span data-stu-id="bff71-162">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="bff71-163">`Out`Cmdlet 将对象发送到指定的显示目标的格式化程序。</span><span class="sxs-lookup"><span data-stu-id="bff71-163">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="bff71-164">相关链接</span><span class="sxs-lookup"><span data-stu-id="bff71-164">RELATED LINKS</span></span>

[<span data-ttu-id="bff71-165">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="bff71-165">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="bff71-166">Out-Default</span><span class="sxs-lookup"><span data-stu-id="bff71-166">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="bff71-167">Out-File</span><span class="sxs-lookup"><span data-stu-id="bff71-167">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="bff71-168">Out-Host</span><span class="sxs-lookup"><span data-stu-id="bff71-168">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="bff71-169">Out-Null</span><span class="sxs-lookup"><span data-stu-id="bff71-169">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="bff71-170">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="bff71-170">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="bff71-171">Out-printer</span><span class="sxs-lookup"><span data-stu-id="bff71-171">Out-Printer</span></span>](Out-Printer.md)
