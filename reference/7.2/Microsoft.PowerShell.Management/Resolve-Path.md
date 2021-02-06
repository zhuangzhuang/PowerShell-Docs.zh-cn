---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 0481526aead285e3d5fb494218d1573e03216f2e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598474"
---
# <span data-ttu-id="aed11-102">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-102">Resolve-Path</span></span>

## <span data-ttu-id="aed11-103">摘要</span><span class="sxs-lookup"><span data-stu-id="aed11-103">SYNOPSIS</span></span>
<span data-ttu-id="aed11-104">解析路径中的通配符并显示路径内容。</span><span class="sxs-lookup"><span data-stu-id="aed11-104">Resolves the wildcard characters in a path, and displays the path contents.</span></span>

## <span data-ttu-id="aed11-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aed11-105">SYNTAX</span></span>

### <span data-ttu-id="aed11-106">Path（默认值）</span><span class="sxs-lookup"><span data-stu-id="aed11-106">Path (Default)</span></span>

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="aed11-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aed11-107">LiteralPath</span></span>

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="aed11-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="aed11-108">DESCRIPTION</span></span>

<span data-ttu-id="aed11-109">`Resolve-Path`Cmdlet 将在指定位置显示与通配符模式匹配的项和容器。</span><span class="sxs-lookup"><span data-stu-id="aed11-109">The `Resolve-Path` cmdlet displays the items and containers that match the wildcard pattern at the location specified.</span></span> <span data-ttu-id="aed11-110">匹配可以包括文件、文件夹、注册表项或可从 New-psdrive 提供程序访问的任何其他对象。</span><span class="sxs-lookup"><span data-stu-id="aed11-110">The match can include files, folders, registry keys, or any other object accessible from a PSDrive provider.</span></span>

## <span data-ttu-id="aed11-111">示例</span><span class="sxs-lookup"><span data-stu-id="aed11-111">EXAMPLES</span></span>

### <span data-ttu-id="aed11-112">示例1：解析主文件夹路径</span><span class="sxs-lookup"><span data-stu-id="aed11-112">Example 1: Resolve the home folder path</span></span>

<span data-ttu-id="aed11-113">颚化符 (~) 是当前用户的主文件夹的速记表示法。</span><span class="sxs-lookup"><span data-stu-id="aed11-113">The tilde character (~) is shorthand notation for the current user's home folder.</span></span> <span data-ttu-id="aed11-114">此示例显示了如何 `Resolve-Path` 返回完全限定的路径值。</span><span class="sxs-lookup"><span data-stu-id="aed11-114">This example shows `Resolve-Path` returning the fully qualified path value.</span></span>

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### <span data-ttu-id="aed11-115">示例2：解析 Windows 文件夹的路径</span><span class="sxs-lookup"><span data-stu-id="aed11-115">Example 2: Resolve the path of the Windows folder</span></span>

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

<span data-ttu-id="aed11-116">从 C：驱动器的根目录运行时，此命令将返回 C：驱动器中 Windows 文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-116">When run from the root of the C: drive, this command returns the path of the Windows folder in the C: drive.</span></span>

### <span data-ttu-id="aed11-117">示例3：获取 Windows 文件夹中的所有路径</span><span class="sxs-lookup"><span data-stu-id="aed11-117">Example 3: Get all paths in the Windows folder</span></span>

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

<span data-ttu-id="aed11-118">此命令返回 C：\Windows 文件夹中的所有文件夹。</span><span class="sxs-lookup"><span data-stu-id="aed11-118">This command returns all of the folders in the C:\Windows folder.</span></span> <span data-ttu-id="aed11-119">该命令使用管道运算符 (|) 将路径字符串发送到 `Resolve-Path` 。</span><span class="sxs-lookup"><span data-stu-id="aed11-119">The command uses a pipeline operator (|) to send a path string to `Resolve-Path`.</span></span>

### <span data-ttu-id="aed11-120">示例4：解析 UNC 路径</span><span class="sxs-lookup"><span data-stu-id="aed11-120">Example 4: Resolve a UNC path</span></span>

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

<span data-ttu-id="aed11-121">此命令解析通用命名约定 (UNC) 路径并返回路径中的共享部分。</span><span class="sxs-lookup"><span data-stu-id="aed11-121">This command resolves a Universal Naming Convention (UNC) path and returns the shares in the path.</span></span>

### <span data-ttu-id="aed11-122">示例5：获取相对路径</span><span class="sxs-lookup"><span data-stu-id="aed11-122">Example 5: Get relative paths</span></span>

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

<span data-ttu-id="aed11-123">此命令返回 C: 驱动器根目录中目录的相对路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-123">This command returns relative paths for the directories at the root of the C: drive.</span></span>

### <span data-ttu-id="aed11-124">示例6：解析包含括号的路径</span><span class="sxs-lookup"><span data-stu-id="aed11-124">Example 6: Resolve a path containing brackets</span></span>

<span data-ttu-id="aed11-125">此示例使用 **LiteralPath** 参数解析测试 \[ xml \] 子文件夹的路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-125">This example uses the **LiteralPath** parameter to resolve the path of the Test\[xml\] subfolder.</span></span>
<span data-ttu-id="aed11-126">使用 **LiteralPath** 会导致将方括号视为普通字符，而不是正则表达式。</span><span class="sxs-lookup"><span data-stu-id="aed11-126">Using **LiteralPath** causes the brackets to be treated as normal characters rather than a regular expression.</span></span>

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## <span data-ttu-id="aed11-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aed11-127">PARAMETERS</span></span>

### <span data-ttu-id="aed11-128">-Credential</span><span class="sxs-lookup"><span data-stu-id="aed11-128">-Credential</span></span>

<span data-ttu-id="aed11-129">指定有权执行此操作的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="aed11-129">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="aed11-130">默认为当前用户。</span><span class="sxs-lookup"><span data-stu-id="aed11-130">The default is the current user.</span></span>

<span data-ttu-id="aed11-131">键入用户名（如 User01 或 Domain01\User01）或传递 **PSCredential** 对象。</span><span class="sxs-lookup"><span data-stu-id="aed11-131">Type a user name, such as User01 or Domain01\User01, or pass a **PSCredential** object.</span></span> <span data-ttu-id="aed11-132">可以使用 cmdlet 创建 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="aed11-132">You can create a **PSCredential** object using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="aed11-133">键入用户名时，此 cmdlet 会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="aed11-133">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="aed11-134">随 PowerShell 一起安装的任何提供程序都不支持此参数。</span><span class="sxs-lookup"><span data-stu-id="aed11-134">This parameter is not supported by any providers installed with PowerShell.</span></span>

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

### <span data-ttu-id="aed11-135">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aed11-135">-LiteralPath</span></span>

<span data-ttu-id="aed11-136">指定要解析的路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-136">Specifies the path to be resolved.</span></span>
<span data-ttu-id="aed11-137">**LiteralPath** 参数的值完全按类型使用。</span><span class="sxs-lookup"><span data-stu-id="aed11-137">The value of the **LiteralPath** parameter is used exactly as typed.</span></span>
<span data-ttu-id="aed11-138">不会将任何字符解释为通配字符。</span><span class="sxs-lookup"><span data-stu-id="aed11-138">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="aed11-139">如果路径包括转义符，请将其括在单引号中。</span><span class="sxs-lookup"><span data-stu-id="aed11-139">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="aed11-140">单引号指示 PowerShell 不要将任何字符解释为转义序列。</span><span class="sxs-lookup"><span data-stu-id="aed11-140">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="aed11-141">-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-141">-Path</span></span>

<span data-ttu-id="aed11-142">指定要解析的 PowerShell 路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-142">Specifies the PowerShell path to resolve.</span></span>
<span data-ttu-id="aed11-143">此参数是必需的。</span><span class="sxs-lookup"><span data-stu-id="aed11-143">This parameter is required.</span></span>
<span data-ttu-id="aed11-144">还可以通过管道将路径字符串传递给 `Resolve-Path` 。</span><span class="sxs-lookup"><span data-stu-id="aed11-144">You can also pipe a path string to `Resolve-Path`.</span></span>
<span data-ttu-id="aed11-145">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="aed11-145">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="aed11-146">-Relative</span><span class="sxs-lookup"><span data-stu-id="aed11-146">-Relative</span></span>

<span data-ttu-id="aed11-147">指示此 cmdlet 返回相对路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-147">Indicates that this cmdlet returns a relative path.</span></span>

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

### <span data-ttu-id="aed11-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aed11-148">CommonParameters</span></span>

<span data-ttu-id="aed11-149">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="aed11-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aed11-150">有关详细信息，请参阅 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="aed11-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="aed11-151">输入</span><span class="sxs-lookup"><span data-stu-id="aed11-151">INPUTS</span></span>

### <span data-ttu-id="aed11-152">System.String</span><span class="sxs-lookup"><span data-stu-id="aed11-152">System.String</span></span>

<span data-ttu-id="aed11-153">可以通过管道将包含路径的字符串传递给此 cmdlet</span><span class="sxs-lookup"><span data-stu-id="aed11-153">You can pipe a string that contains a path to this cmdlet</span></span>

## <span data-ttu-id="aed11-154">输出</span><span class="sxs-lookup"><span data-stu-id="aed11-154">OUTPUTS</span></span>

### <span data-ttu-id="aed11-155">PathInfo，System.web. String</span><span class="sxs-lookup"><span data-stu-id="aed11-155">System.Management.Automation.PathInfo, System.String</span></span>

<span data-ttu-id="aed11-156">返回 **PathInfo** 对象。</span><span class="sxs-lookup"><span data-stu-id="aed11-156">Returns a **PathInfo** object.</span></span> <span data-ttu-id="aed11-157">如果指定 **相对** 参数，则返回解析的路径的字符串值。</span><span class="sxs-lookup"><span data-stu-id="aed11-157">Returns a string value for the resolved path if you specify the **Relative** parameter.</span></span>

## <span data-ttu-id="aed11-158">注释</span><span class="sxs-lookup"><span data-stu-id="aed11-158">NOTES</span></span>

<span data-ttu-id="aed11-159">这些 `*-Path` cmdlet 适用于 FileSystem、Registry 和 Certificate 提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed11-159">The `*-Path` cmdlets work with the FileSystem, Registry, and Certificate providers.</span></span>

<span data-ttu-id="aed11-160">`Resolve-Path` 适用于任何提供程序。</span><span class="sxs-lookup"><span data-stu-id="aed11-160">`Resolve-Path` is designed to work with any provider.</span></span> <span data-ttu-id="aed11-161">若要列出会话中可用的提供程序，请键入 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="aed11-161">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="aed11-162">有关详细信息，请参阅 [about_providers](../microsoft.powershell.core/about/about_providers.md)。</span><span class="sxs-lookup"><span data-stu-id="aed11-162">For more information, see [about_providers](../microsoft.powershell.core/about/about_providers.md).</span></span>

<span data-ttu-id="aed11-163">`Resolve-Path` 仅解析现有路径。</span><span class="sxs-lookup"><span data-stu-id="aed11-163">`Resolve-Path` only resolves existing paths.</span></span> <span data-ttu-id="aed11-164">它无法用于解析尚不存在的位置。</span><span class="sxs-lookup"><span data-stu-id="aed11-164">It cannot be used to resolve a location that does not exist yet.</span></span>

## <span data-ttu-id="aed11-165">相关链接</span><span class="sxs-lookup"><span data-stu-id="aed11-165">RELATED LINKS</span></span>

[<span data-ttu-id="aed11-166">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-166">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="aed11-167">Join-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-167">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="aed11-168">Split-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-168">Split-Path</span></span>](Split-Path.md)

[<span data-ttu-id="aed11-169">Test-Path</span><span class="sxs-lookup"><span data-stu-id="aed11-169">Test-Path</span></span>](Test-Path.md)

