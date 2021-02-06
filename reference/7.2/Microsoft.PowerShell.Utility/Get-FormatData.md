---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596412"
---
# <span data-ttu-id="f7898-102">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="f7898-102">Get-FormatData</span></span>

## <span data-ttu-id="f7898-103">摘要</span><span class="sxs-lookup"><span data-stu-id="f7898-103">SYNOPSIS</span></span>
<span data-ttu-id="f7898-104">获取当前会话中的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-104">Gets the formatting data in the current session.</span></span>

## <span data-ttu-id="f7898-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7898-105">SYNTAX</span></span>

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## <span data-ttu-id="f7898-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7898-106">DESCRIPTION</span></span>

<span data-ttu-id="f7898-107">`Get-FormatData`Cmdlet 将获取当前会话中的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-107">The `Get-FormatData` cmdlet gets the formatting data in the current session.</span></span>

<span data-ttu-id="f7898-108">会话中的格式设置数据包括格式设置文件中的格式设置数据， `Format.ps1xml` 例如目录中的数据 `$PSHOME` 、导入到会话中的模块的格式数据，以及使用 cmdlet 导入到会话中的命令的格式设置数据的格式 `Import-PSSession` 。</span><span class="sxs-lookup"><span data-stu-id="f7898-108">The formatting data in the session includes formatting data from `Format.ps1xml` formatting files, such as those in the `$PSHOME` directory, formatting data for modules that you import into the session, and formatting data for commands that you import into your session by using the `Import-PSSession` cmdlet.</span></span>

<span data-ttu-id="f7898-109">可以使用此 cmdlet 来检查格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-109">You can use this cmdlet to examine the formatting data.</span></span> <span data-ttu-id="f7898-110">然后，可以使用 `Export-FormatData` cmdlet 序列化对象，将它们转换为 XML，然后将它们保存在 `Format.ps1xml` 文件中。</span><span class="sxs-lookup"><span data-stu-id="f7898-110">Then, you can use the `Export-FormatData` cmdlet to serialize the objects, convert them to XML, and save them in `Format.ps1xml` files.</span></span>

<span data-ttu-id="f7898-111">有关在 PowerShell 中格式化文件的详细信息，请参阅 [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f7898-111">For more information about formatting files in PowerShell, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

## <span data-ttu-id="f7898-112">示例</span><span class="sxs-lookup"><span data-stu-id="f7898-112">EXAMPLES</span></span>

### <span data-ttu-id="f7898-113">示例1：获取所有格式设置数据</span><span class="sxs-lookup"><span data-stu-id="f7898-113">Example 1: Get all formatting data</span></span>

<span data-ttu-id="f7898-114">此示例获取会话中的所有格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-114">This example gets all the formatting data in the session.</span></span>

```powershell
Get-FormatData
```

### <span data-ttu-id="f7898-115">示例2：按类型名称获取格式设置数据</span><span class="sxs-lookup"><span data-stu-id="f7898-115">Example 2: Get formatting data by type name</span></span>

<span data-ttu-id="f7898-116">此示例获取名称以开头的格式设置数据项 `System.Management.Automation.Cmd` 。</span><span class="sxs-lookup"><span data-stu-id="f7898-116">This example gets the formatting data items whose names begin with `System.Management.Automation.Cmd`.</span></span>

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### <span data-ttu-id="f7898-117">示例3：检查格式设置数据对象</span><span class="sxs-lookup"><span data-stu-id="f7898-117">Example 3: Examine a formatting data object</span></span>

<span data-ttu-id="f7898-118">此命令演示如何获取格式设置数据对象并检查其属性。</span><span class="sxs-lookup"><span data-stu-id="f7898-118">This example shows how to get a formatting data object and examine its properties.</span></span>

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### <span data-ttu-id="f7898-119">示例4：获取格式设置数据并将其导出</span><span class="sxs-lookup"><span data-stu-id="f7898-119">Example 4: Get formatting data and export it</span></span>

<span data-ttu-id="f7898-120">此示例演示如何使用 `Get-FormatData` 和 `Export-FormatData` 导出模块添加的格式设置数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-120">This example shows how to use `Get-FormatData` and `Export-FormatData` to export the formatting data that is added by a module.</span></span>

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

<span data-ttu-id="f7898-121">前四个命令使用 `Get-FormatData` 、 `Import-Module` 和 `Compare-Object` Cmdlet 来标识 **BitsTransfer** 模块添加到会话中的格式类型。</span><span class="sxs-lookup"><span data-stu-id="f7898-121">The first four commands use the `Get-FormatData`, `Import-Module`, and `Compare-Object` cmdlets to identify the format type that the **BitsTransfer** module adds to the session.</span></span>

<span data-ttu-id="f7898-122">第五个命令使用 `Get-FormatData` cmdlet 来获取 **BitsTransfer** 模块添加的格式类型。</span><span class="sxs-lookup"><span data-stu-id="f7898-122">The fifth command uses the `Get-FormatData` cmdlet to get the format type that the **BitsTransfer** module adds.</span></span> <span data-ttu-id="f7898-123">它使用管道运算符 (`|`) 将格式类型对象发送到 `Export-FormatData` cmdlet，后者将该对象转换回 XML 并将其保存到指定文件中 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="f7898-123">It uses a pipeline operator (`|`) to send the format type object to the `Export-FormatData` cmdlet, which converts it back to XML and saves it in the specified `format.ps1xml` file.</span></span>

<span data-ttu-id="f7898-124">最后一个命令显示文件内容的摘录 `format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="f7898-124">The final command shows an excerpt of the `format.ps1xml` file content.</span></span>

### <span data-ttu-id="f7898-125">示例5：基于指定的 PowerShell 版本获取格式设置数据</span><span class="sxs-lookup"><span data-stu-id="f7898-125">Example 5: Get formatting data based on the specified version of PowerShell</span></span>

<span data-ttu-id="f7898-126">此示例演示如何使用 `Get-FormatData` 来获取指定的 **TypeName** 和 PowerShell 版本的格式数据。</span><span class="sxs-lookup"><span data-stu-id="f7898-126">This example shows how to use `Get-FormatData` to get format data for a specified **TypeName** and PowerShell version.</span></span>

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## <span data-ttu-id="f7898-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7898-127">PARAMETERS</span></span>

### <span data-ttu-id="f7898-128">-PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="f7898-128">-PowerShellVersion</span></span>

<span data-ttu-id="f7898-129">指定此 cmdlet 为格式化数据获取的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="f7898-129">Specify the version of PowerShell this cmdlet gets for the formatting data.</span></span> <span data-ttu-id="f7898-130">输入用句点分隔的两位数字。</span><span class="sxs-lookup"><span data-stu-id="f7898-130">Enter a two digit number separated by a period.</span></span>

<span data-ttu-id="f7898-131">此参数是在 PowerShell 5.1 中添加的，用于在远程计算机运行较早版本的 PowerShell 时提高兼容性。</span><span class="sxs-lookup"><span data-stu-id="f7898-131">This parameter was added in PowerShell 5.1 to improve compatibility when remoting computers running older versions of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7898-132">-TypeName</span><span class="sxs-lookup"><span data-stu-id="f7898-132">-TypeName</span></span>

<span data-ttu-id="f7898-133">指定此 cmdlet 为格式化数据获取的类型名称。</span><span class="sxs-lookup"><span data-stu-id="f7898-133">Specifies the type names that this cmdlet gets for the formatting data.</span></span>
<span data-ttu-id="f7898-134">输入类型名称。</span><span class="sxs-lookup"><span data-stu-id="f7898-134">Enter the type names.</span></span>
<span data-ttu-id="f7898-135">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="f7898-135">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f7898-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7898-136">CommonParameters</span></span>

<span data-ttu-id="f7898-137">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7898-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7898-138">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7898-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7898-139">输入</span><span class="sxs-lookup"><span data-stu-id="f7898-139">INPUTS</span></span>

### <span data-ttu-id="f7898-140">无</span><span class="sxs-lookup"><span data-stu-id="f7898-140">None</span></span>

<span data-ttu-id="f7898-141">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f7898-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f7898-142">输出</span><span class="sxs-lookup"><span data-stu-id="f7898-142">OUTPUTS</span></span>

### <span data-ttu-id="f7898-143">System.Management.Automation.ExtendedTypeDefinition</span><span class="sxs-lookup"><span data-stu-id="f7898-143">System.Management.Automation.ExtendedTypeDefinition</span></span>

## <span data-ttu-id="f7898-144">注释</span><span class="sxs-lookup"><span data-stu-id="f7898-144">NOTES</span></span>

## <span data-ttu-id="f7898-145">相关链接</span><span class="sxs-lookup"><span data-stu-id="f7898-145">RELATED LINKS</span></span>

[<span data-ttu-id="f7898-146">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="f7898-146">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="f7898-147">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="f7898-147">Update-FormatData</span></span>](Update-FormatData.md)
