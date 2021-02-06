---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7686ade747345b7c770772067007b8abf13aac3d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595802"
---
# <span data-ttu-id="ef630-102">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="ef630-102">Select-Xml</span></span>

## <span data-ttu-id="ef630-103">摘要</span><span class="sxs-lookup"><span data-stu-id="ef630-103">SYNOPSIS</span></span>
<span data-ttu-id="ef630-104">在 XML 字符串或文档中查找文本。</span><span class="sxs-lookup"><span data-stu-id="ef630-104">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="ef630-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef630-105">SYNTAX</span></span>

### <span data-ttu-id="ef630-106">Xml（默认值）</span><span class="sxs-lookup"><span data-stu-id="ef630-106">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="ef630-107">路径</span><span class="sxs-lookup"><span data-stu-id="ef630-107">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="ef630-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ef630-108">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="ef630-109">内容</span><span class="sxs-lookup"><span data-stu-id="ef630-109">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="ef630-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="ef630-110">DESCRIPTION</span></span>

<span data-ttu-id="ef630-111">使用 **Select xml** cmdlet 可以使用 XPath 查询来搜索 Xml 字符串和文档中的文本。</span><span class="sxs-lookup"><span data-stu-id="ef630-111">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="ef630-112">输入 XPath 查询，并使用 *Content*、 *Path* 或 *xml* 参数来指定要搜索的 Xml。</span><span class="sxs-lookup"><span data-stu-id="ef630-112">Enter an XPath query, and use the *Content*, *Path*, or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="ef630-113">示例</span><span class="sxs-lookup"><span data-stu-id="ef630-113">EXAMPLES</span></span>

### <span data-ttu-id="ef630-114">示例1：选择 AliasProperty 节点</span><span class="sxs-lookup"><span data-stu-id="ef630-114">Example 1: Select AliasProperty nodes</span></span>

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

<span data-ttu-id="ef630-115">此示例在 Types.ps1xml 中获取别名属性。</span><span class="sxs-lookup"><span data-stu-id="ef630-115">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="ef630-116">（有关此文件的信息，请参阅 about_Types.ps1xml。）</span><span class="sxs-lookup"><span data-stu-id="ef630-116">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="ef630-117">第一个命令将路径保存到 $Path 变量中的 Types.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="ef630-117">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="ef630-118">第二个命令将 XML 路径保存到 $XPath 变量中的 AliasProperty 节点。</span><span class="sxs-lookup"><span data-stu-id="ef630-118">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="ef630-119">第三个命令使用 **Select-Xml** cmdlet 来获取由 Types.ps1xml 文件中的 XPath 语句标识的 AliasProperty 节点。</span><span class="sxs-lookup"><span data-stu-id="ef630-119">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="ef630-120">此命令使用管道运算符将 AliasProperty 节点发送给 Select-Object cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef630-120">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="ef630-121">*ExpandProperty* 参数将展开 **节点** 对象并返回其 Name 和 ReferencedMemberName 属性。</span><span class="sxs-lookup"><span data-stu-id="ef630-121">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="ef630-122">结果显示 Types.ps1xml 文件中每个别名属性的名称和 ReferencedMemberName。</span><span class="sxs-lookup"><span data-stu-id="ef630-122">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="ef630-123">例如，有一个 **Count** 属性，它是 **Length** 属性的别名。</span><span class="sxs-lookup"><span data-stu-id="ef630-123">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="ef630-124">示例2：输入 XML 文档</span><span class="sxs-lookup"><span data-stu-id="ef630-124">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="ef630-125">此示例演示如何使用 *xml* 参数将 xml 文档提供给 **Select xml** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef630-125">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="ef630-126">第一个命令使用 Get-Content cmdlet 获取 Types.ps1xml 文件内容，并将其保存在 $Types 变量中。</span><span class="sxs-lookup"><span data-stu-id="ef630-126">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="ef630-127">\[Xml 将 \] 变量强制转换为 xml 对象。</span><span class="sxs-lookup"><span data-stu-id="ef630-127">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="ef630-128">第二个命令使用 **Select-Xml** cmdlet 来获取 Types.ps1xml 文件中的 MethodName 节点。</span><span class="sxs-lookup"><span data-stu-id="ef630-128">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="ef630-129">该命令使用 *Xml* 参数指定 $Types 变量中的 XML 内容，并使用 *XPath* 参数指定到 MethodName 节点的路径。</span><span class="sxs-lookup"><span data-stu-id="ef630-129">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="ef630-130">示例3：搜索 PowerShell 帮助文件</span><span class="sxs-lookup"><span data-stu-id="ef630-130">Example 3: Search PowerShell Help files</span></span>

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

<span data-ttu-id="ef630-131">此示例演示如何使用 **Select Xml** cmdlet 搜索基于 PowerShell Xml 的 cmdlet 帮助文件。</span><span class="sxs-lookup"><span data-stu-id="ef630-131">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="ef630-132">在此示例中，我们将搜索 cmdlet 名称，它用作每个帮助文件的标题以及指向该帮助文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ef630-132">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="ef630-133">第一个命令创建表示用于帮助文件的 XML 命名空间的哈希表，并将其保存在 $Namespace 变量中。</span><span class="sxs-lookup"><span data-stu-id="ef630-133">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="ef630-134">示例4：输入 XML 的不同方式</span><span class="sxs-lookup"><span data-stu-id="ef630-134">Example 4: Different ways to input XML</span></span>

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

<span data-ttu-id="ef630-135">此示例显示了将 XML 发送到 **Select xml** cmdlet 的两种不同方法。</span><span class="sxs-lookup"><span data-stu-id="ef630-135">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="ef630-136">第一个命令保存包含 $Xml 变量中的 XML 的一个字符串。</span><span class="sxs-lookup"><span data-stu-id="ef630-136">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="ef630-137">（有关 here-string 的详细信息，请参阅 about_Quoting_Rules。）</span><span class="sxs-lookup"><span data-stu-id="ef630-137">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="ef630-138">示例5：使用默认的 xmlns 命名空间</span><span class="sxs-lookup"><span data-stu-id="ef630-138">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="ef630-139">此示例演示如何将 **Select xml** cmdlet 与使用默认 xmlns 命名空间的 Xml 文档一起使用。</span><span class="sxs-lookup"><span data-stu-id="ef630-139">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="ef630-140">此示例获取 Windows PowerShell ISE 用户创建的代码段文件的标题。</span><span class="sxs-lookup"><span data-stu-id="ef630-140">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="ef630-141">有关代码段的信息，请参阅 New-IseSnippet。</span><span class="sxs-lookup"><span data-stu-id="ef630-141">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="ef630-142">第一个命令为代码段的默认命名空间创建一个哈希表，该哈希表用于代码段，并将其分配给 $SnippetNamespace 变量。</span><span class="sxs-lookup"><span data-stu-id="ef630-142">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="ef630-143">哈希表值是 XML 代码段中的 XMLNS 架构 URI。</span><span class="sxs-lookup"><span data-stu-id="ef630-143">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="ef630-144">哈希表键名称是随意的。</span><span class="sxs-lookup"><span data-stu-id="ef630-144">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="ef630-145">你可以使用不保留的任何名称，但不能使用 xmlns。</span><span class="sxs-lookup"><span data-stu-id="ef630-145">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="ef630-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ef630-146">PARAMETERS</span></span>

### <span data-ttu-id="ef630-147">-Content</span><span class="sxs-lookup"><span data-stu-id="ef630-147">-Content</span></span>

<span data-ttu-id="ef630-148">指定包含要搜索的 XML 的字符串。</span><span class="sxs-lookup"><span data-stu-id="ef630-148">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="ef630-149">还可以通过管道将字符串传递给 **Select-Xml**。</span><span class="sxs-lookup"><span data-stu-id="ef630-149">You can also pipe strings to **Select-Xml**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef630-150">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ef630-150">-LiteralPath</span></span>

<span data-ttu-id="ef630-151">指定要搜索的 XML 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="ef630-151">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="ef630-152">与 *Path* 不同，*LiteralPath* 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="ef630-152">Unlike *Path*, the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="ef630-153">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="ef630-153">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ef630-154">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="ef630-154">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="ef630-155">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="ef630-155">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef630-156">-Namespace</span><span class="sxs-lookup"><span data-stu-id="ef630-156">-Namespace</span></span>

<span data-ttu-id="ef630-157">指定在 XML 中使用的命名空间的哈希表。</span><span class="sxs-lookup"><span data-stu-id="ef630-157">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="ef630-158">使用格式 @ { \<namespaceName\>  =  \<namespaceValue\> }。</span><span class="sxs-lookup"><span data-stu-id="ef630-158">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="ef630-159">当 XML 使用以 xmlns 开头的默认命名空间时，使用命名空间名称的任意键。</span><span class="sxs-lookup"><span data-stu-id="ef630-159">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="ef630-160">不能使用 xmlns。</span><span class="sxs-lookup"><span data-stu-id="ef630-160">You cannot use xmlns.</span></span>
<span data-ttu-id="ef630-161">在 XPath 语句中，使用命名空间名称和冒号作为每个节点名称的前缀，如//namespaceName： Node。</span><span class="sxs-lookup"><span data-stu-id="ef630-161">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef630-162">-Path</span><span class="sxs-lookup"><span data-stu-id="ef630-162">-Path</span></span>

<span data-ttu-id="ef630-163">指定要搜索的 XML 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="ef630-163">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="ef630-164">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="ef630-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ef630-165">-Xml</span><span class="sxs-lookup"><span data-stu-id="ef630-165">-Xml</span></span>

<span data-ttu-id="ef630-166">指定一个或多个 XML 节点。</span><span class="sxs-lookup"><span data-stu-id="ef630-166">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="ef630-167">将作为 XML 节点的集合处理 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="ef630-167">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="ef630-168">如果通过管道将 XML 文档传递给 **Select-xml**，则将在每个文档节点通过管道时单独搜索。</span><span class="sxs-lookup"><span data-stu-id="ef630-168">If you pipe an XML document to **Select-Xml**, each document node will be searched separately as it comes through the pipeline.</span></span>

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef630-169">-XPath</span><span class="sxs-lookup"><span data-stu-id="ef630-169">-XPath</span></span>

<span data-ttu-id="ef630-170">指定 XPath 搜索查询。</span><span class="sxs-lookup"><span data-stu-id="ef630-170">Specifies an XPath search query.</span></span>
<span data-ttu-id="ef630-171">查询语言区分大小写。</span><span class="sxs-lookup"><span data-stu-id="ef630-171">The query language is case-sensitive.</span></span>
<span data-ttu-id="ef630-172">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="ef630-172">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef630-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef630-173">CommonParameters</span></span>

<span data-ttu-id="ef630-174">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="ef630-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef630-175">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="ef630-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef630-176">输入</span><span class="sxs-lookup"><span data-stu-id="ef630-176">INPUTS</span></span>

### <span data-ttu-id="ef630-177">System.String 或 System.Xml.XmlNode</span><span class="sxs-lookup"><span data-stu-id="ef630-177">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="ef630-178">可以通过管道将路径或 XML 节点传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ef630-178">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="ef630-179">输出</span><span class="sxs-lookup"><span data-stu-id="ef630-179">OUTPUTS</span></span>

### <span data-ttu-id="ef630-180">Microsoft.PowerShell.Commands.SelectXmlInfo</span><span class="sxs-lookup"><span data-stu-id="ef630-180">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="ef630-181">注释</span><span class="sxs-lookup"><span data-stu-id="ef630-181">NOTES</span></span>

<span data-ttu-id="ef630-182">XPath 是一种标准语言，它可以识别 XML 文档的各个部分。</span><span class="sxs-lookup"><span data-stu-id="ef630-182">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="ef630-183">有关 XPath 语言的详细信息，请参阅 " [Xpath 参考](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) " 和 " [事件选择](/previous-versions//aa385231(v=vs.85))" 的 "选择筛选器" 部分。</span><span class="sxs-lookup"><span data-stu-id="ef630-183">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="ef630-184">相关链接</span><span class="sxs-lookup"><span data-stu-id="ef630-184">RELATED LINKS</span></span>

[<span data-ttu-id="ef630-185">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="ef630-185">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
