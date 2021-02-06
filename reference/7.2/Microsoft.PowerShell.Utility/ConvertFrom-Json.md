---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 525b123d48b0f88ca3eef85a3f95cc303a981ca3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598883"
---
# <span data-ttu-id="fd05e-102">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="fd05e-102">ConvertFrom-Json</span></span>

## <span data-ttu-id="fd05e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="fd05e-103">SYNOPSIS</span></span>
<span data-ttu-id="fd05e-104">将 JSON 格式的字符串转换为自定义对象或哈希表。</span><span class="sxs-lookup"><span data-stu-id="fd05e-104">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="fd05e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fd05e-105">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="fd05e-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fd05e-106">DESCRIPTION</span></span>

<span data-ttu-id="fd05e-107">`ConvertFrom-Json`Cmdlet 将 JavaScript 对象表示法 (json) 格式的字符串转换为自定义 **PSCustomObject** 对象，该对象具有 JSON 字符串中每个字段的属性。</span><span class="sxs-lookup"><span data-stu-id="fd05e-107">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="fd05e-108">JSON 通常可供网站使用，以提供对象的文本表示形式。</span><span class="sxs-lookup"><span data-stu-id="fd05e-108">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="fd05e-109">JSON 标准不禁止使用 **PSCustomObject** 禁止使用。</span><span class="sxs-lookup"><span data-stu-id="fd05e-109">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="fd05e-110">例如，如果 JSON 字符串包含重复的键，则此 cmdlet 仅使用最后一个密钥。</span><span class="sxs-lookup"><span data-stu-id="fd05e-110">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="fd05e-111">请参阅下面的其他示例。</span><span class="sxs-lookup"><span data-stu-id="fd05e-111">See other examples below.</span></span>

<span data-ttu-id="fd05e-112">若要从任何对象生成 JSON 字符串，请使用 `ConvertTo-Json` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fd05e-112">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="fd05e-113">此 cmdlet 是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fd05e-113">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="fd05e-114">从 PowerShell 6 开始，此 cmdlet 支持包含注释的 JSON。</span><span class="sxs-lookup"><span data-stu-id="fd05e-114">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="fd05e-115">接受的注释以两个正斜杠开始 (`//`) 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-115">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="fd05e-116">注释不会在数据中表示出来，并且可以在文件中写入，而不会损坏数据，也不会引发错误，就像在 PowerShell 5.1 中那样。</span><span class="sxs-lookup"><span data-stu-id="fd05e-116">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="fd05e-117">示例</span><span class="sxs-lookup"><span data-stu-id="fd05e-117">EXAMPLES</span></span>

### <span data-ttu-id="fd05e-118">示例1：将 DateTime 对象转换为 JSON 对象</span><span class="sxs-lookup"><span data-stu-id="fd05e-118">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="fd05e-119">此命令使用 `ConvertTo-Json` 和 `ConvertFrom-Json` Cmdlet 将 **DateTime** 对象从 cmdlet 转换为 JSON 对象，然后将其转换 `Get-Date` 为 **PSCustomObject**。</span><span class="sxs-lookup"><span data-stu-id="fd05e-119">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="fd05e-120">该示例使用 `Select-Object` cmdlet 来获取 **DateTime** 对象的所有属性。</span><span class="sxs-lookup"><span data-stu-id="fd05e-120">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="fd05e-121">它使用 `ConvertTo-Json` cmdlet 将 **DateTime** 对象转换为设置为 json 对象格式的字符串，并使用 `ConvertFrom-Json` cmdlet 将 JSON 格式的字符串转换为 **PSCustomObject** 对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-121">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="fd05e-122">示例2：从 web 服务获取 JSON 字符串，并将其转换为 PowerShell 对象</span><span class="sxs-lookup"><span data-stu-id="fd05e-122">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="fd05e-123">此命令使用 `Invoke-WebRequest` cmdlet 从 web 服务获取 json 字符串，然后使用 `ConvertFrom-Json` CMDLET 将 json 内容转换为可在 PowerShell 中管理的对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-123">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="fd05e-124">你还可以使用 `Invoke-RestMethod` cmdlet，它会自动将 JSON 内容转换为对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-124">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="fd05e-125">示例3：将 JSON 字符串转换为自定义对象</span><span class="sxs-lookup"><span data-stu-id="fd05e-125">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="fd05e-126">此示例演示如何使用 `ConvertFrom-Json` cmdlet 将 JSON 文件转换为 PowerShell 自定义对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-126">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="fd05e-127">该命令使用 Get-Content cmdlet 获取 JSON 文件中的字符串。</span><span class="sxs-lookup"><span data-stu-id="fd05e-127">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="fd05e-128">然后，它使用管道运算符将分隔的字符串发送到 `ConvertFrom-Json` cmdlet，该 cmdlet 会将其转换为自定义对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-128">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="fd05e-129">示例4：将 JSON 字符串转换为哈希表</span><span class="sxs-lookup"><span data-stu-id="fd05e-129">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="fd05e-130">此命令显示一个示例，在该示例中， `-AsHashtable` 开关可以克服命令的限制。</span><span class="sxs-lookup"><span data-stu-id="fd05e-130">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="fd05e-131">JSON 字符串包含两个键值对，键仅在大小写方面存在差异。</span><span class="sxs-lookup"><span data-stu-id="fd05e-131">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="fd05e-132">如果不使用开关，则该命令将引发错误。</span><span class="sxs-lookup"><span data-stu-id="fd05e-132">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="fd05e-133">示例5：往返单个元素数组</span><span class="sxs-lookup"><span data-stu-id="fd05e-133">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="fd05e-134">此命令显示一个示例，在该示例中， `-NoEnumerate` 开关用于往返单个元素 JSON 数组。</span><span class="sxs-lookup"><span data-stu-id="fd05e-134">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="fd05e-135">JSON 字符串包含一个具有单个元素的数组。</span><span class="sxs-lookup"><span data-stu-id="fd05e-135">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="fd05e-136">在没有开关的情况下，将 JSON 转换为 PSObject，然后使用 `ConvertTo-Json` 命令结果将其转换回单个整数。</span><span class="sxs-lookup"><span data-stu-id="fd05e-136">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="fd05e-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fd05e-137">PARAMETERS</span></span>

### <span data-ttu-id="fd05e-138">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="fd05e-138">-AsHashtable</span></span>

<span data-ttu-id="fd05e-139">将 JSON 转换为哈希表对象。</span><span class="sxs-lookup"><span data-stu-id="fd05e-139">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="fd05e-140">此开关是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fd05e-140">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="fd05e-141">在某些情况下，它可以克服 cmdlet 的某些限制 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-141">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="fd05e-142">如果 JSON 包含具有仅大小写不同的键的列表。</span><span class="sxs-lookup"><span data-stu-id="fd05e-142">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="fd05e-143">如果没有交换机，这些密钥将被视为相同的键，因此仅使用最后一个键。</span><span class="sxs-lookup"><span data-stu-id="fd05e-143">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="fd05e-144">如果 JSON 包含空字符串，则为。</span><span class="sxs-lookup"><span data-stu-id="fd05e-144">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="fd05e-145">如果不使用开关，该 cmdlet 将引发错误，因为不 `PSCustomObject` 允许这样做，但哈希表会这样做。</span><span class="sxs-lookup"><span data-stu-id="fd05e-145">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="fd05e-146">这种情况的一个示例用例是 `project.lock.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="fd05e-146">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="fd05e-147">对于某些数据结构，可以更快地处理哈希表。</span><span class="sxs-lookup"><span data-stu-id="fd05e-147">Hash tables can be processed faster for certain data structures.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd05e-148">-Depth</span><span class="sxs-lookup"><span data-stu-id="fd05e-148">-Depth</span></span>

<span data-ttu-id="fd05e-149">获取或设置允许 JSON 输入具有的最大深度。</span><span class="sxs-lookup"><span data-stu-id="fd05e-149">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="fd05e-150">默认情况下，它是1024。</span><span class="sxs-lookup"><span data-stu-id="fd05e-150">By default, it is 1024.</span></span>

<span data-ttu-id="fd05e-151">此参数是在 PowerShell 6.2 中引入的。</span><span class="sxs-lookup"><span data-stu-id="fd05e-151">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="fd05e-152">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fd05e-152">-InputObject</span></span>

<span data-ttu-id="fd05e-153">指定要转换为 JSON 对象的 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="fd05e-153">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="fd05e-154">输入一个包含字符串的变量，或键入可获取字符串的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="fd05e-154">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="fd05e-155">还可以通过管道将字符串传递给 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-155">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="fd05e-156">**InputObject** 参数是必需的，但其值可以是空字符串。</span><span class="sxs-lookup"><span data-stu-id="fd05e-156">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="fd05e-157">当输入对象为空字符串时，不 `ConvertFrom-Json` 会生成任何输出。</span><span class="sxs-lookup"><span data-stu-id="fd05e-157">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="fd05e-158">**InputObject** 值不能为 `$null` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-158">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fd05e-159">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="fd05e-159">-NoEnumerate</span></span>

<span data-ttu-id="fd05e-160">指定不枚举输出。</span><span class="sxs-lookup"><span data-stu-id="fd05e-160">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="fd05e-161">设置此参数会导致将数组作为单个对象发送，而不是分别发送每个元素。</span><span class="sxs-lookup"><span data-stu-id="fd05e-161">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="fd05e-162">这可以保证 JSON 可以通过往返 `ConvertTo-Json` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-162">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fd05e-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fd05e-163">CommonParameters</span></span>

<span data-ttu-id="fd05e-164">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fd05e-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fd05e-165">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fd05e-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fd05e-166">输入</span><span class="sxs-lookup"><span data-stu-id="fd05e-166">INPUTS</span></span>

### <span data-ttu-id="fd05e-167">System.String</span><span class="sxs-lookup"><span data-stu-id="fd05e-167">System.String</span></span>

<span data-ttu-id="fd05e-168">可以通过管道将 JSON 字符串传递给 `ConvertFrom-Json` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-168">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="fd05e-169">输出</span><span class="sxs-lookup"><span data-stu-id="fd05e-169">OUTPUTS</span></span>

### <span data-ttu-id="fd05e-170">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="fd05e-170">PSCustomObject</span></span>

### <span data-ttu-id="fd05e-171">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="fd05e-171">System.Collections.Hashtable</span></span>

## <span data-ttu-id="fd05e-172">注释</span><span class="sxs-lookup"><span data-stu-id="fd05e-172">NOTES</span></span>

<span data-ttu-id="fd05e-173">此 cmdlet 是使用 [newtonsoft.json Json.NET](https://www.newtonsoft.com/json)实现的。</span><span class="sxs-lookup"><span data-stu-id="fd05e-173">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="fd05e-174">从 PowerShell 6 开始， `ConvertTo-Json` 尝试将格式化为时间戳的字符串转换为 **DateTime** 值。</span><span class="sxs-lookup"><span data-stu-id="fd05e-174">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="fd05e-175">转换后的值是 `[datetime]` 具有属性设置的实例， `Kind` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="fd05e-175">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="fd05e-176">`Unspecified`如果输入字符串中没有时区信息，则为。</span><span class="sxs-lookup"><span data-stu-id="fd05e-176">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="fd05e-177">`Utc`如果时区信息为后缀，则为 `Z` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-177">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="fd05e-178">`Local`如果将时区信息指定为与类似的尾随 UTC _偏移量_ ，则为 `+02:00` 。</span><span class="sxs-lookup"><span data-stu-id="fd05e-178">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="fd05e-179">偏移量正确转换为调用方配置的时区。</span><span class="sxs-lookup"><span data-stu-id="fd05e-179">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="fd05e-180">默认输出格式不表示原始时区偏移量。</span><span class="sxs-lookup"><span data-stu-id="fd05e-180">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="fd05e-181">相关链接</span><span class="sxs-lookup"><span data-stu-id="fd05e-181">RELATED LINKS</span></span>

<span data-ttu-id="fd05e-182">[JavaScript 和 .NET 中的 JavaScript 对象表示法 (JSON) 简介](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="fd05e-182">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="fd05e-183">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="fd05e-183">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="fd05e-184">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="fd05e-184">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="fd05e-185">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="fd05e-185">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
