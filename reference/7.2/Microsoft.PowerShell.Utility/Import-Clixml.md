---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 3658ea5eded0fed95a1c9a1ea6e7d84a557e1e36
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597071"
---
# <span data-ttu-id="aee75-102">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="aee75-102">Import-Clixml</span></span>

## <span data-ttu-id="aee75-103">摘要</span><span class="sxs-lookup"><span data-stu-id="aee75-103">SYNOPSIS</span></span>
<span data-ttu-id="aee75-104">导入 EXPORT-CLIXML 文件并在 PowerShell 中创建相应的对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-104">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="aee75-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aee75-105">SYNTAX</span></span>

### <span data-ttu-id="aee75-106">ByPath（默认值）</span><span class="sxs-lookup"><span data-stu-id="aee75-106">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="aee75-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="aee75-107">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="aee75-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aee75-108">DESCRIPTION</span></span>

<span data-ttu-id="aee75-109">`Import-Clixml`Cmdlet (CLI) XML 文件导入公共语言基础结构，其中包含表示 Microsoft .NET 框架对象的数据，并创建 PowerShell 对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-109">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="aee75-110">有关 CLI 的详细信息，请参阅 [语言独立性](/dotnet/standard/language-independence)。</span><span class="sxs-lookup"><span data-stu-id="aee75-110">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="aee75-111">Windows 计算机上的一个重要用途 `Import-Clixml` 是导入凭据，并使用作为安全 XML 导出的安全字符串 `Export-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="aee75-111">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="aee75-112">有关示例，请参见示例2。</span><span class="sxs-lookup"><span data-stu-id="aee75-112">For an example, see Example 2.</span></span>

<span data-ttu-id="aee75-113">`Import-Clixml` 使用字节顺序标记 (BOM) 来检测文件的编码格式。</span><span class="sxs-lookup"><span data-stu-id="aee75-113">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="aee75-114">如果文件没有 BOM，则假定编码为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="aee75-114">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="aee75-115">示例</span><span class="sxs-lookup"><span data-stu-id="aee75-115">EXAMPLES</span></span>

### <span data-ttu-id="aee75-116">示例1：导入序列化的文件并重新创建对象</span><span class="sxs-lookup"><span data-stu-id="aee75-116">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="aee75-117">此示例使用 `Export-Clixml` cmdlet 保存返回的进程信息的序列化副本 `Get-Process` 。</span><span class="sxs-lookup"><span data-stu-id="aee75-117">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="aee75-118">`Import-Clixml` 检索序列化文件的内容，并重新创建存储在变量中的对象 `$Processes` 。</span><span class="sxs-lookup"><span data-stu-id="aee75-118">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="aee75-119">示例2：导入安全凭据对象</span><span class="sxs-lookup"><span data-stu-id="aee75-119">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="aee75-120">在此示例中，给定通过运行 cmdlet 存储在变量中的凭据 `$Credential` `Get-Credential` ，可以运行 `Export-Clixml` cmdlet 将凭据保存到磁盘。</span><span class="sxs-lookup"><span data-stu-id="aee75-120">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aee75-121">`Export-Clixml` 仅导出 Windows 上的加密凭据。</span><span class="sxs-lookup"><span data-stu-id="aee75-121">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="aee75-122">在非 Windows 操作系统（如 macOS 和 Linux）上，凭据以纯文本格式导出。</span><span class="sxs-lookup"><span data-stu-id="aee75-122">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="aee75-123">`Export-Clixml`Cmdlet 使用 Windows[数据保护 API](/previous-versions/windows/apps/hh464970(v=win.10))加密凭据对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-123">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="aee75-124">加密可确保只有你的用户帐户才能解密 credential 对象的内容。</span><span class="sxs-lookup"><span data-stu-id="aee75-124">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="aee75-125">导出的 `CLIXML` 文件不能用于其他计算机或其他用户。</span><span class="sxs-lookup"><span data-stu-id="aee75-125">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="aee75-126">在此示例中，存储凭据的文件由表示 `TestScript.ps1.credential` 。</span><span class="sxs-lookup"><span data-stu-id="aee75-126">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="aee75-127">将 **TestScript** 替换为要在其中加载凭据的脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="aee75-127">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="aee75-128">将凭据对象向下发送到管道 `Export-Clixml` ，并将其保存到在 `$Credxmlpath` 第一个命令中指定的路径。</span><span class="sxs-lookup"><span data-stu-id="aee75-128">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="aee75-129">若要将凭据自动导入脚本，请运行最后两个命令。</span><span class="sxs-lookup"><span data-stu-id="aee75-129">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="aee75-130">运行 `Import-Clixml` 将受保护的凭据对象导入脚本。</span><span class="sxs-lookup"><span data-stu-id="aee75-130">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="aee75-131">此导入消除了在脚本中公开纯文本密码的风险。</span><span class="sxs-lookup"><span data-stu-id="aee75-131">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="aee75-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aee75-132">PARAMETERS</span></span>

### <span data-ttu-id="aee75-133">-第一个</span><span class="sxs-lookup"><span data-stu-id="aee75-133">-First</span></span>

<span data-ttu-id="aee75-134">只获取指定数量的对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-134">Gets only the specified number of objects.</span></span> <span data-ttu-id="aee75-135">输入要获取的对象数量。</span><span class="sxs-lookup"><span data-stu-id="aee75-135">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aee75-136">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="aee75-136">-IncludeTotalCount</span></span>

<span data-ttu-id="aee75-137">报告数据集中的对象总数，后跟所选对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-137">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="aee75-138">如果该 cmdlet 无法确定总计数，则会显示 **未知的总计数**。</span><span class="sxs-lookup"><span data-stu-id="aee75-138">If the cmdlet can't determine the total count, it displays **Unknown total count**.</span></span> <span data-ttu-id="aee75-139">整数具有一个 **准确性** 属性，该属性指示总计值的可靠性。</span><span class="sxs-lookup"><span data-stu-id="aee75-139">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="aee75-140">**准确性** 的值范围从 `0.0` 到到 `1.0` ， `0.0` 表示该 cmdlet 无法对对象进行计数，这 `1.0` 意味着该计数是精确的，介于和之间的值 `0.0` `1.0` 表示越来越可靠的估计值。</span><span class="sxs-lookup"><span data-stu-id="aee75-140">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

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

### <span data-ttu-id="aee75-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aee75-141">-LiteralPath</span></span>

<span data-ttu-id="aee75-142">指定 XML 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="aee75-142">Specifies the path to the XML files.</span></span> <span data-ttu-id="aee75-143">与 **Path** 不同， **LiteralPath** 参数的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="aee75-143">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="aee75-144">不会将任何字符解释为通配符。</span><span class="sxs-lookup"><span data-stu-id="aee75-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aee75-145">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="aee75-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="aee75-146">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="aee75-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aee75-147">-Path</span><span class="sxs-lookup"><span data-stu-id="aee75-147">-Path</span></span>

<span data-ttu-id="aee75-148">指定 XML 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="aee75-148">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="aee75-149">-Skip</span><span class="sxs-lookup"><span data-stu-id="aee75-149">-Skip</span></span>

<span data-ttu-id="aee75-150">忽略指定数量的对象，然后获取其余对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-150">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="aee75-151">输入要跳过的对象数量。</span><span class="sxs-lookup"><span data-stu-id="aee75-151">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aee75-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aee75-152">CommonParameters</span></span>

<span data-ttu-id="aee75-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aee75-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aee75-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="aee75-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aee75-155">输入</span><span class="sxs-lookup"><span data-stu-id="aee75-155">INPUTS</span></span>

### <span data-ttu-id="aee75-156">System.String</span><span class="sxs-lookup"><span data-stu-id="aee75-156">System.String</span></span>

<span data-ttu-id="aee75-157">可以通过管道将包含路径的字符串进行管道 `Import-Clixml` 。</span><span class="sxs-lookup"><span data-stu-id="aee75-157">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="aee75-158">输出</span><span class="sxs-lookup"><span data-stu-id="aee75-158">OUTPUTS</span></span>

### <span data-ttu-id="aee75-159">PSObject</span><span class="sxs-lookup"><span data-stu-id="aee75-159">PSObject</span></span>

<span data-ttu-id="aee75-160">`Import-Clixml` 返回从存储的 XML 文件反序列化的对象。</span><span class="sxs-lookup"><span data-stu-id="aee75-160">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="aee75-161">注释</span><span class="sxs-lookup"><span data-stu-id="aee75-161">NOTES</span></span>

<span data-ttu-id="aee75-162">为一个参数指定多个值时，请使用逗号分隔这些值。</span><span class="sxs-lookup"><span data-stu-id="aee75-162">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="aee75-163">例如，`<parameter-name> <value1>, <value2>`。</span><span class="sxs-lookup"><span data-stu-id="aee75-163">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="aee75-164">相关链接</span><span class="sxs-lookup"><span data-stu-id="aee75-164">RELATED LINKS</span></span>

[<span data-ttu-id="aee75-165">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="aee75-165">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="aee75-166">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="aee75-166">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="aee75-167">Join-Path</span><span class="sxs-lookup"><span data-stu-id="aee75-167">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

<span data-ttu-id="aee75-168">[Securely Store Credentials on Disk](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)（将凭据安全存储到磁盘）</span><span class="sxs-lookup"><span data-stu-id="aee75-168">[Securely Store Credentials on Disk](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)</span></span>

<span data-ttu-id="aee75-169">[Use PowerShell to Pass Credentials to Legacy Systems](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)（使用 PowerShell 将凭据传递到旧系统）</span><span class="sxs-lookup"><span data-stu-id="aee75-169">[Use PowerShell to Pass Credentials to Legacy Systems](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)</span></span>

