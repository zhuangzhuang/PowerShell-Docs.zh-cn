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
# Select-Xml

## 摘要
在 XML 字符串或文档中查找文本。

## SYNTAX

### Xml（默认值）

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### 路径

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### 内容

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## DESCRIPTION

使用 **Select xml** cmdlet 可以使用 XPath 查询来搜索 Xml 字符串和文档中的文本。
输入 XPath 查询，并使用 *Content*、 *Path* 或 *xml* 参数来指定要搜索的 Xml。

## 示例

### 示例1：选择 AliasProperty 节点

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

此示例在 Types.ps1xml 中获取别名属性。
（有关此文件的信息，请参阅 about_Types.ps1xml。）

第一个命令将路径保存到 $Path 变量中的 Types.ps1xml 文件。

第二个命令将 XML 路径保存到 $XPath 变量中的 AliasProperty 节点。

第三个命令使用 **Select-Xml** cmdlet 来获取由 Types.ps1xml 文件中的 XPath 语句标识的 AliasProperty 节点。
此命令使用管道运算符将 AliasProperty 节点发送给 Select-Object cmdlet。
*ExpandProperty* 参数将展开 **节点** 对象并返回其 Name 和 ReferencedMemberName 属性。

结果显示 Types.ps1xml 文件中每个别名属性的名称和 ReferencedMemberName。
例如，有一个 **Count** 属性，它是 **Length** 属性的别名。

### 示例2：输入 XML 文档

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

此示例演示如何使用 *xml* 参数将 xml 文档提供给 **Select xml** cmdlet。

第一个命令使用 Get-Content cmdlet 获取 Types.ps1xml 文件内容，并将其保存在 $Types 变量中。
\[Xml 将 \] 变量强制转换为 xml 对象。

第二个命令使用 **Select-Xml** cmdlet 来获取 Types.ps1xml 文件中的 MethodName 节点。
该命令使用 *Xml* 参数指定 $Types 变量中的 XML 内容，并使用 *XPath* 参数指定到 MethodName 节点的路径。

### 示例3：搜索 PowerShell 帮助文件

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

此示例演示如何使用 **Select Xml** cmdlet 搜索基于 PowerShell Xml 的 cmdlet 帮助文件。
在此示例中，我们将搜索 cmdlet 名称，它用作每个帮助文件的标题以及指向该帮助文件的路径。

第一个命令创建表示用于帮助文件的 XML 命名空间的哈希表，并将其保存在 $Namespace 变量中。

### 示例4：输入 XML 的不同方式

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

此示例显示了将 XML 发送到 **Select xml** cmdlet 的两种不同方法。

第一个命令保存包含 $Xml 变量中的 XML 的一个字符串。
（有关 here-string 的详细信息，请参阅 about_Quoting_Rules。）

### 示例5：使用默认的 xmlns 命名空间

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

此示例演示如何将 **Select xml** cmdlet 与使用默认 xmlns 命名空间的 Xml 文档一起使用。
此示例获取 Windows PowerShell ISE 用户创建的代码段文件的标题。
有关代码段的信息，请参阅 New-IseSnippet。

第一个命令为代码段的默认命名空间创建一个哈希表，该哈希表用于代码段，并将其分配给 $SnippetNamespace 变量。
哈希表值是 XML 代码段中的 XMLNS 架构 URI。
哈希表键名称是随意的。
你可以使用不保留的任何名称，但不能使用 xmlns。

## PARAMETERS

### -Content

指定包含要搜索的 XML 的字符串。
还可以通过管道将字符串传递给 **Select-Xml**。

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

### -LiteralPath

指定要搜索的 XML 文件的路径和文件名。
与 *Path* 不同，*LiteralPath* 参数的值严格按照所键入的形式使用。
不会将任何字符解释为通配符。
如果路径包括转义符，请将其括在单引号中。
单引号指示 PowerShell 不要将任何字符解释为转义序列。

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

### -Namespace

指定在 XML 中使用的命名空间的哈希表。
使用格式 @ { \<namespaceName\>  =  \<namespaceValue\> }。

当 XML 使用以 xmlns 开头的默认命名空间时，使用命名空间名称的任意键。
不能使用 xmlns。
在 XPath 语句中，使用命名空间名称和冒号作为每个节点名称的前缀，如//namespaceName： Node。

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

### -Path

指定要搜索的 XML 文件的路径和文件名。
允许使用通配符。

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

### -Xml

指定一个或多个 XML 节点。

将作为 XML 节点的集合处理 XML 文档。
如果通过管道将 XML 文档传递给 **Select-xml**，则将在每个文档节点通过管道时单独搜索。

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

### -XPath

指定 XPath 搜索查询。
查询语言区分大小写。
此参数是必需的。

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

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.String 或 System.Xml.XmlNode

可以通过管道将路径或 XML 节点传递给此 cmdlet。

## 输出

### Microsoft.PowerShell.Commands.SelectXmlInfo

## 注释

XPath 是一种标准语言，它可以识别 XML 文档的各个部分。 有关 XPath 语言的详细信息，请参阅 " [Xpath 参考](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) " 和 " [事件选择](/previous-versions//aa385231(v=vs.85))" 的 "选择筛选器" 部分。

## 相关链接

[ConvertTo-Xml](ConvertTo-Xml.md)
