---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e461c07360b3d9eaf7d9a3c8875d34cd1fc841e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596648"
---
# <span data-ttu-id="0145b-102">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="0145b-102">ConvertTo-Xml</span></span>

## <span data-ttu-id="0145b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0145b-103">SYNOPSIS</span></span>
<span data-ttu-id="0145b-104">创建对象的基于 XML 的表示形式。</span><span class="sxs-lookup"><span data-stu-id="0145b-104">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="0145b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0145b-105">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="0145b-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0145b-106">DESCRIPTION</span></span>

<span data-ttu-id="0145b-107">`ConvertTo-Xml`Cmdlet 可创建一个或多个更多 .net 对象的[基于 XML](/dotnet/api/system.xml.xmldocument)的表示形式。</span><span class="sxs-lookup"><span data-stu-id="0145b-107">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="0145b-108">若要使用此 cmdlet，请通过管道将一个或多个对象传递给 cmdlet，或使用 **InputObject** 参数来指定对象。</span><span class="sxs-lookup"><span data-stu-id="0145b-108">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="0145b-109">当通过管道将多个对象传递给 `ConvertTo-Xml` 或使用 **InputObject** 参数提交多个对象时，将 `ConvertTo-Xml` 返回一个内存中 XML 文档，其中包含所有对象的表示形式。</span><span class="sxs-lookup"><span data-stu-id="0145b-109">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="0145b-110">此 cmdlet 类似于 [export-clixml](./Export-Clixml.md) ，但前者将 `Export-Clixml` 生成的 XML 存储在 [公共语言基础结构中 (CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) 文件，该文件可以重新导入为包含 [export-clixml](./Import-Clixml.md)的对象。</span><span class="sxs-lookup"><span data-stu-id="0145b-110">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="0145b-111">`ConvertTo-Xml` 返回 XML 文档的内存中表示形式，以便您可以继续在 PowerShell 中处理它。</span><span class="sxs-lookup"><span data-stu-id="0145b-111">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="0145b-112">`ConvertTo-Xml` 没有将对象转换为 CLI XML 的选项。</span><span class="sxs-lookup"><span data-stu-id="0145b-112">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="0145b-113">示例</span><span class="sxs-lookup"><span data-stu-id="0145b-113">EXAMPLES</span></span>

### <span data-ttu-id="0145b-114">示例1：将日期转换为 XML</span><span class="sxs-lookup"><span data-stu-id="0145b-114">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="0145b-115">此命令将 **DateTime** 对象) 的当前日期转换为 XML (。</span><span class="sxs-lookup"><span data-stu-id="0145b-115">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="0145b-116">示例2：将进程转换为 XML</span><span class="sxs-lookup"><span data-stu-id="0145b-116">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="0145b-117">此命令可将表示计算机上所有进程的进程对象转换为一个 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="0145b-117">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="0145b-118">这些对象的级别深度将扩展至三。</span><span class="sxs-lookup"><span data-stu-id="0145b-118">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="0145b-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0145b-119">PARAMETERS</span></span>

### <span data-ttu-id="0145b-120">-As</span><span class="sxs-lookup"><span data-stu-id="0145b-120">-As</span></span>

<span data-ttu-id="0145b-121">确定输出格式。</span><span class="sxs-lookup"><span data-stu-id="0145b-121">Determines the output format.</span></span>
<span data-ttu-id="0145b-122">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0145b-122">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0145b-123">字符串。</span><span class="sxs-lookup"><span data-stu-id="0145b-123">String.</span></span>
<span data-ttu-id="0145b-124">返回单个字符串。</span><span class="sxs-lookup"><span data-stu-id="0145b-124">Returns a single string.</span></span>
- <span data-ttu-id="0145b-125">流。</span><span class="sxs-lookup"><span data-stu-id="0145b-125">Stream.</span></span>
<span data-ttu-id="0145b-126">返回一个字符串数组。</span><span class="sxs-lookup"><span data-stu-id="0145b-126">Returns an array of strings.</span></span>
- <span data-ttu-id="0145b-127">Document。</span><span class="sxs-lookup"><span data-stu-id="0145b-127">Document.</span></span>
<span data-ttu-id="0145b-128">返回一个 **xml** 对象。</span><span class="sxs-lookup"><span data-stu-id="0145b-128">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="0145b-129">默认值为 Document。</span><span class="sxs-lookup"><span data-stu-id="0145b-129">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0145b-130">-Depth</span><span class="sxs-lookup"><span data-stu-id="0145b-130">-Depth</span></span>

<span data-ttu-id="0145b-131">指定 XML 表示形式中所包含的包含对象的级别数。</span><span class="sxs-lookup"><span data-stu-id="0145b-131">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="0145b-132">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="0145b-132">The default value is 1.</span></span>

<span data-ttu-id="0145b-133">例如，如果对象的属性还包含对象，若要保存所包含对象的属性的 XML 表示形式，则必须将深度指定为 2。</span><span class="sxs-lookup"><span data-stu-id="0145b-133">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="0145b-134">可以覆盖 Types.ps1xml 文件中对象类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="0145b-134">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="0145b-135">有关详细信息，请参阅 about_Types.ps1xml。</span><span class="sxs-lookup"><span data-stu-id="0145b-135">For more information, see about_Types.ps1xml.</span></span>

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

### <span data-ttu-id="0145b-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="0145b-136">-InputObject</span></span>

<span data-ttu-id="0145b-137">指定要转换的对象。</span><span class="sxs-lookup"><span data-stu-id="0145b-137">Specifies the object to be converted.</span></span> <span data-ttu-id="0145b-138">输入一个包含对象的变量，或键入可获取对象的命令或表达式。</span><span class="sxs-lookup"><span data-stu-id="0145b-138">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="0145b-139">还可以通过管道将对象传递给 **convertto-html**。</span><span class="sxs-lookup"><span data-stu-id="0145b-139">You can also pipe objects to **ConvertTo-XML**.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0145b-140">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="0145b-140">-NoTypeInformation</span></span>

<span data-ttu-id="0145b-141">省略对象节点中的 Type 属性。</span><span class="sxs-lookup"><span data-stu-id="0145b-141">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="0145b-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0145b-142">CommonParameters</span></span>

<span data-ttu-id="0145b-143">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0145b-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0145b-144">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0145b-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0145b-145">输入</span><span class="sxs-lookup"><span data-stu-id="0145b-145">INPUTS</span></span>

### <span data-ttu-id="0145b-146">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="0145b-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="0145b-147">可以通过管道将任何对象传递给 **convertto-html**。</span><span class="sxs-lookup"><span data-stu-id="0145b-147">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="0145b-148">输出</span><span class="sxs-lookup"><span data-stu-id="0145b-148">OUTPUTS</span></span>

### <span data-ttu-id="0145b-149">System.object 或 System.Xml.Xml文档</span><span class="sxs-lookup"><span data-stu-id="0145b-149">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="0145b-150">*As* 参数的值确定 **convertto-html** 返回的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="0145b-150">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="0145b-151">注释</span><span class="sxs-lookup"><span data-stu-id="0145b-151">NOTES</span></span>

## <span data-ttu-id="0145b-152">相关链接</span><span class="sxs-lookup"><span data-stu-id="0145b-152">RELATED LINKS</span></span>

[<span data-ttu-id="0145b-153">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="0145b-153">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="0145b-154">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="0145b-154">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="0145b-155">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="0145b-155">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="0145b-156">获取日期</span><span class="sxs-lookup"><span data-stu-id="0145b-156">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="0145b-157">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="0145b-157">Import-Clixml</span></span>](Import-Clixml.md)

