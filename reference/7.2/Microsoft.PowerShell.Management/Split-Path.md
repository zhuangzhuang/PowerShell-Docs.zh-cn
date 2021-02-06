---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595638"
---
# <span data-ttu-id="c4ee1-102">Split-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-102">Split-Path</span></span>

## <span data-ttu-id="c4ee1-103">摘要</span><span class="sxs-lookup"><span data-stu-id="c4ee1-103">SYNOPSIS</span></span>
<span data-ttu-id="c4ee1-104">返回指定的路径部分。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-104">Returns the specified part of a path.</span></span>

## <span data-ttu-id="c4ee1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4ee1-105">SYNTAX</span></span>

### <span data-ttu-id="c4ee1-106">ParentSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="c4ee1-106">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-107">LeafSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-107">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-108">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-108">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-109">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-109">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-111">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-111">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-112">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-112">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="c4ee1-113">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="c4ee1-113">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="c4ee1-114">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="c4ee1-114">DESCRIPTION</span></span>

<span data-ttu-id="c4ee1-115">`Split-Path`Cmdlet 仅返回路径的指定部分，如父文件夹、子文件夹或文件名。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-115">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="c4ee1-116">它也可以获取拆分路径所引用的项，并指示该路径是相对路径还是绝对路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-116">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="c4ee1-117">使用此 cmdlet 可以只获取或只提交路径的选定部分。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-117">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="c4ee1-118">示例</span><span class="sxs-lookup"><span data-stu-id="c4ee1-118">EXAMPLES</span></span>

### <span data-ttu-id="c4ee1-119">示例1：获取路径的限定符</span><span class="sxs-lookup"><span data-stu-id="c4ee1-119">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="c4ee1-120">此命令只返回路径的限定符。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-120">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="c4ee1-121">限定符是驱动器。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-121">The qualifier is the drive.</span></span>

### <span data-ttu-id="c4ee1-122">示例2：显示文件名</span><span class="sxs-lookup"><span data-stu-id="c4ee1-122">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="c4ee1-123">此命令显示拆分路径所引用的文件。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-123">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="c4ee1-124">由于此路径拆分为最后一项，也称为叶，因此该命令只显示文件名。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-124">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="c4ee1-125">**Resolve** 参数指示 `Split-Path` 显示拆分路径所引用的项，而不是显示拆分路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-125">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="c4ee1-126">与所有 `Split-Path` 命令一样，此命令将返回字符串。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-126">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="c4ee1-127">它不返回表示文件的 **FileInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-127">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="c4ee1-128">示例3：获取父容器</span><span class="sxs-lookup"><span data-stu-id="c4ee1-128">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="c4ee1-129">此命令只返回路径的父容器。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-129">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="c4ee1-130">由于它不包括任何用于指定拆分的参数，因此将 `Split-Path` 使用默认的拆分位置默认值。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-130">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="c4ee1-131">示例4：确定路径是否为绝对路径</span><span class="sxs-lookup"><span data-stu-id="c4ee1-131">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="c4ee1-132">此命令确定路径是相对路径还是绝对路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-132">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="c4ee1-133">在这种情况下，因为路径是当前文件夹的相对路径，而该文件夹由点 `.`)  (，则返回 `$False` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-133">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="c4ee1-134">示例5：将位置更改为指定路径</span><span class="sxs-lookup"><span data-stu-id="c4ee1-134">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="c4ee1-135">此命令将你的位置更改为包含 PowerShell 配置文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-135">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="c4ee1-136">括号中的命令使用 `Split-Path` 来仅返回内置变量中存储的路径的父级 `$Profile` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-136">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="c4ee1-137">**Parent** 参数是默认的拆分位置参数。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-137">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="c4ee1-138">因此，你可以从命令中省略它。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-138">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="c4ee1-139">圆括号直接 PowerShell 以首先运行命令。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-139">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="c4ee1-140">这是一种移动到具有长路径名称的文件夹的有效方法。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-140">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="c4ee1-141">示例6：使用管道拆分路径</span><span class="sxs-lookup"><span data-stu-id="c4ee1-141">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="c4ee1-142">此命令使用管道运算符 (`|`) 将路径发送到 `Split-Path` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-142">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="c4ee1-143">路径用引号引起以指示它是一个标记。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-143">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="c4ee1-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4ee1-144">PARAMETERS</span></span>

### <span data-ttu-id="c4ee1-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="c4ee1-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="c4ee1-146">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-146">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="c4ee1-147">若要在运行此 cmdlet 时模拟其他用户或提升凭据，请使用 [Invoke 命令](../Microsoft.PowerShell.Core/Invoke-Command.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-148">-扩展</span><span class="sxs-lookup"><span data-stu-id="c4ee1-148">-Extension</span></span>

<span data-ttu-id="c4ee1-149">指示此 cmdlet 仅返回叶的扩展。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-149">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="c4ee1-150">例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `.log` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-150">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="c4ee1-151">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-152">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="c4ee1-152">-IsAbsolute</span></span>

<span data-ttu-id="c4ee1-153">指示如果路径为绝对路径，则此 cmdlet 返回 $True; 如果路径是相对路径，则为 $False。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-153">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="c4ee1-154">绝对路径的长度大于零，并且不使用点 (`.`) 来指示当前路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-154">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-155">-Leaf</span><span class="sxs-lookup"><span data-stu-id="c4ee1-155">-Leaf</span></span>

<span data-ttu-id="c4ee1-156">指示此 cmdlet 仅返回路径中的最后一项或容器。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-156">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="c4ee1-157">例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 pass1.log。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-157">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-158">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="c4ee1-158">-LeafBase</span></span>

<span data-ttu-id="c4ee1-159">指示此 cmdlet 仅返回叶的基名称。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-159">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="c4ee1-160">例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `Pass1` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-160">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="c4ee1-161">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-161">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c4ee1-162">-LiteralPath</span></span>

<span data-ttu-id="c4ee1-163">指定要拆分的路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-163">Specifies the paths to be split.</span></span> <span data-ttu-id="c4ee1-164">不同于 **Path**，**LiteralPath** 的值严格按照所键入的形式使用。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-164">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c4ee1-165">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-165">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="c4ee1-166">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-166">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c4ee1-167">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-167">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-168">-NoQualifier</span><span class="sxs-lookup"><span data-stu-id="c4ee1-168">-NoQualifier</span></span>

<span data-ttu-id="c4ee1-169">指示此 cmdlet 返回无限定符的路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-169">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="c4ee1-170">对于文件系统或注册表提供程序，限定符是提供程序路径的驱动器，例如 `C:` 或 `HKCU:` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-170">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="c4ee1-171">例如，在路径中 `C:\Test\Logs\Pass1.log` ，它仅返回 `\Test\Logs\Pass1.log` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-171">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-172">-Parent</span><span class="sxs-lookup"><span data-stu-id="c4ee1-172">-Parent</span></span>

<span data-ttu-id="c4ee1-173">指示此 cmdlet 仅返回项或路径指定的容器的父容器。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-173">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="c4ee1-174">例如，在路径中 `C:\Test\Logs\Pass1.log` ，它返回 `C:\Test\Logs` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-174">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="c4ee1-175">**Parent** 参数是默认的拆分位置参数。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-175">The **Parent** parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-176">-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-176">-Path</span></span>

<span data-ttu-id="c4ee1-177">指定要拆分的路径。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-177">Specifies the paths to be split.</span></span> <span data-ttu-id="c4ee1-178">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-178">Wildcard characters are permitted.</span></span> <span data-ttu-id="c4ee1-179">如果路径包括空格，请将其括在引号中。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-179">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="c4ee1-180">还可以通过管道将路径传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-180">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c4ee1-181">-Qualifier</span><span class="sxs-lookup"><span data-stu-id="c4ee1-181">-Qualifier</span></span>

<span data-ttu-id="c4ee1-182">指示此 cmdlet 仅返回指定路径的限定符。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-182">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="c4ee1-183">对于文件系统或注册表提供程序，限定符是提供程序路径的驱动器，例如 `C:` 或 `HKCU:` 。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-183">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c4ee1-184">-Resolve</span><span class="sxs-lookup"><span data-stu-id="c4ee1-184">-Resolve</span></span>

<span data-ttu-id="c4ee1-185">指示此 cmdlet 显示生成的拆分路径所引用的项，而不是显示路径元素。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-185">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="c4ee1-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4ee1-186">CommonParameters</span></span>

<span data-ttu-id="c4ee1-187">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4ee1-188">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4ee1-189">输入</span><span class="sxs-lookup"><span data-stu-id="c4ee1-189">INPUTS</span></span>

### <span data-ttu-id="c4ee1-190">System.String</span><span class="sxs-lookup"><span data-stu-id="c4ee1-190">System.String</span></span>

<span data-ttu-id="c4ee1-191">可以通过管道将包含路径的字符串传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-191">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="c4ee1-192">输出</span><span class="sxs-lookup"><span data-stu-id="c4ee1-192">OUTPUTS</span></span>

### <span data-ttu-id="c4ee1-193">System.String、System.Boolean</span><span class="sxs-lookup"><span data-stu-id="c4ee1-193">System.String, System.Boolean</span></span>

<span data-ttu-id="c4ee1-194">`Split-Path` 返回文本字符串。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-194">`Split-Path` returns text strings.</span></span> <span data-ttu-id="c4ee1-195">当你指定 **Resolve** 参数时，将 `Split-Path` 返回描述项位置的字符串; 它不返回表示项的对象，如 **FileInfo** 或 **RegistryKey** 对象。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-195">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="c4ee1-196">指定 **IsAbsolute** 参数时，将 `Split-Path` 返回一个 **布尔** 值。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-196">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="c4ee1-197">注释</span><span class="sxs-lookup"><span data-stu-id="c4ee1-197">NOTES</span></span>

- <span data-ttu-id="c4ee1-198"> (**限定符**、 **Parent**、 **Extension**、 **叶**、 **LeafBase** 和 **NoQualifier**) 的拆分位置参数是互斥的。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-198">The split location parameters (**Qualifier**, **Parent**, **Extension**, **Leaf**, **LeafBase**, and **NoQualifier**) are exclusive.</span></span> <span data-ttu-id="c4ee1-199">在每个命令中只能使用一个参数。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-199">You can use only one in each command.</span></span>

- <span data-ttu-id="c4ee1-200">包含路径 cmdlet (路径 **名词的** cmdlet) **使用路径名，** 并以所有 PowerShell 提供程序可解释的简洁格式返回名称。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-200">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="c4ee1-201">这些 cmdlet 用于需要在其中以特定格式显示全部或部分路径名称的程序或脚本中。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-201">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="c4ee1-202">使用 **Dirname**、 **Normpath**、 **Realpath**、 **Join** 或其他路径操控器的方式来使用它们。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-202">Use them in the way that you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

- <span data-ttu-id="c4ee1-203">可以将 **路径** cmdlet 与多个提供程序一起使用。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-203">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="c4ee1-204">其中包括 FileSystem、Registry 和 Certificate 提供程序。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-204">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="c4ee1-205">`Split-Path` 设计用于处理由任何提供程序公开的数据。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-205">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="c4ee1-206">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="c4ee1-207">有关详细信息，请参阅 about_Providers。</span><span class="sxs-lookup"><span data-stu-id="c4ee1-207">For more information, see about_Providers.</span></span>

## <span data-ttu-id="c4ee1-208">相关链接</span><span class="sxs-lookup"><span data-stu-id="c4ee1-208">RELATED LINKS</span></span>

[<span data-ttu-id="c4ee1-209">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-209">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="c4ee1-210">Join-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-210">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="c4ee1-211">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-211">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="c4ee1-212">Test-Path</span><span class="sxs-lookup"><span data-stu-id="c4ee1-212">Test-Path</span></span>](Test-Path.md)
