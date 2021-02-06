---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599053"
---
# <span data-ttu-id="d84f0-102">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="d84f0-102">Get-HotFix</span></span>

## <span data-ttu-id="d84f0-103">摘要</span><span class="sxs-lookup"><span data-stu-id="d84f0-103">SYNOPSIS</span></span>
<span data-ttu-id="d84f0-104">获取本地或远程计算机上安装的修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-104">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="d84f0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d84f0-105">SYNTAX</span></span>

### <span data-ttu-id="d84f0-106">Default（默认值）</span><span class="sxs-lookup"><span data-stu-id="d84f0-106">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="d84f0-107">说明</span><span class="sxs-lookup"><span data-stu-id="d84f0-107">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="d84f0-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d84f0-108">DESCRIPTION</span></span>

<span data-ttu-id="d84f0-109">`Get-Hotfix`Cmdlet 可获取本地计算机或指定远程计算机上安装的修补程序或更新。</span><span class="sxs-lookup"><span data-stu-id="d84f0-109">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="d84f0-110">可以 Windows 更新、Microsoft 更新、Windows Server Update Services 或手动安装这些更新。</span><span class="sxs-lookup"><span data-stu-id="d84f0-110">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="d84f0-111">示例</span><span class="sxs-lookup"><span data-stu-id="d84f0-111">EXAMPLES</span></span>

### <span data-ttu-id="d84f0-112">示例1：获取本地计算机上的所有修补程序</span><span class="sxs-lookup"><span data-stu-id="d84f0-112">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="d84f0-113">`Get-Hotfix`Cmdlet 将获取在本地计算机上安装的所有修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-113">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="d84f0-114">示例2：从由字符串筛选的多台计算机获取修补程序</span><span class="sxs-lookup"><span data-stu-id="d84f0-114">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="d84f0-115">该 `Get-Hotfix` 命令使用参数获取远程计算机上安装的修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-115">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="d84f0-116">结果按指定的描述字符串进行筛选。</span><span class="sxs-lookup"><span data-stu-id="d84f0-116">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="d84f0-117">`Get-Hotfix` 用 **Description** 参数和包含星号 () 通配符的字符串 **安全** 筛选输出 `*` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-117">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="d84f0-118">**ComputerName** 参数包含以逗号分隔的远程计算机名字符串。</span><span class="sxs-lookup"><span data-stu-id="d84f0-118">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="d84f0-119">**Credential** 参数指定有权访问远程计算机并运行命令的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d84f0-119">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="d84f0-120">示例3：验证是否已安装更新并将计算机名称写入文件</span><span class="sxs-lookup"><span data-stu-id="d84f0-120">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="d84f0-121">此示例中的命令验证是否安装了特定更新。</span><span class="sxs-lookup"><span data-stu-id="d84f0-121">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="d84f0-122">如果未安装该更新，则会将计算机名称写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-122">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="d84f0-123">`$A`变量包含通过文本文件获取的计算机名称 `Get-Content` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-123">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="d84f0-124">中的对象 `$A` 将向下发送到 `ForEach-Object` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-124">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="d84f0-125">`if`语句将 cmdlet 用于 `Get-Hotfix` **Id** 参数，并为每个计算机名称使用特定 id 号。</span><span class="sxs-lookup"><span data-stu-id="d84f0-125">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="d84f0-126">如果计算机未安装指定的修补程序 Id，则该 `Add-Content` cmdlet 会将计算机名称写入文件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-126">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="d84f0-127">示例4：获取本地计算机上的最新修补程序</span><span class="sxs-lookup"><span data-stu-id="d84f0-127">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="d84f0-128">此示例获取计算机上安装的最新修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-128">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="d84f0-129">`Get-Hotfix` 将对象向下发送到 `Sort-Object` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d84f0-129">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="d84f0-130">`Sort-Object` 按升序对对象排序，并使用 **Property** 参数来评估每个 **InstalledOn** 日期。</span><span class="sxs-lookup"><span data-stu-id="d84f0-130">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="d84f0-131">数组表示法 `[-1]` 选择最新安装的修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-131">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="d84f0-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d84f0-132">PARAMETERS</span></span>

### <span data-ttu-id="d84f0-133">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d84f0-133">-ComputerName</span></span>

<span data-ttu-id="d84f0-134">指定远程计算机。</span><span class="sxs-lookup"><span data-stu-id="d84f0-134">Specifies a remote computer.</span></span> <span data-ttu-id="d84f0-135">键入远程计算机的 NetBIOS 名称、Internet 协议 (IP) 地址或完全限定的域名 (FQDN)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-135">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="d84f0-136">当 **ComputerName** 参数未指定时， `Get-Hotfix` 将在本地计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="d84f0-136">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="d84f0-137">**ComputerName** 参数不依赖于 Windows PowerShell 远程处理。</span><span class="sxs-lookup"><span data-stu-id="d84f0-137">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="d84f0-138">如果你的计算机未配置为运行远程命令，请使用 **ComputerName** 参数。</span><span class="sxs-lookup"><span data-stu-id="d84f0-138">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d84f0-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="d84f0-139">-Credential</span></span>

<span data-ttu-id="d84f0-140">指定有权访问计算机并运行命令的用户帐户。</span><span class="sxs-lookup"><span data-stu-id="d84f0-140">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="d84f0-141">默认值为当前用户</span><span class="sxs-lookup"><span data-stu-id="d84f0-141">The default is the current user</span></span>

<span data-ttu-id="d84f0-142">键入用户名（如 **User01** 或 **Domain01\User01**），或输入 cmdlet 生成的 **PSCredential** 对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-142">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d84f0-143">如果键入用户名，系统会提示输入密码。</span><span class="sxs-lookup"><span data-stu-id="d84f0-143">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="d84f0-144">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-144">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="d84f0-145">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-145">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d84f0-146">-Description</span><span class="sxs-lookup"><span data-stu-id="d84f0-146">-Description</span></span>

<span data-ttu-id="d84f0-147">`Get-HotFix` 使用 **Description** 参数指定修补程序类型。</span><span class="sxs-lookup"><span data-stu-id="d84f0-147">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="d84f0-148">允许使用通配符。</span><span class="sxs-lookup"><span data-stu-id="d84f0-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="d84f0-149">-Id</span><span class="sxs-lookup"><span data-stu-id="d84f0-149">-Id</span></span>

<span data-ttu-id="d84f0-150">筛选 `Get-HotFix` 特定修补程序 id 的结果。</span><span class="sxs-lookup"><span data-stu-id="d84f0-150">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="d84f0-151">不接受通配符。</span><span class="sxs-lookup"><span data-stu-id="d84f0-151">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d84f0-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d84f0-152">CommonParameters</span></span>

<span data-ttu-id="d84f0-153">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d84f0-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d84f0-154">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d84f0-155">输入</span><span class="sxs-lookup"><span data-stu-id="d84f0-155">INPUTS</span></span>

### <span data-ttu-id="d84f0-156">字符串</span><span class="sxs-lookup"><span data-stu-id="d84f0-156">String</span></span>

<span data-ttu-id="d84f0-157">可以通过管道将一个或多个计算机名称传递给修补程序。</span><span class="sxs-lookup"><span data-stu-id="d84f0-157">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="d84f0-158">输出</span><span class="sxs-lookup"><span data-stu-id="d84f0-158">OUTPUTS</span></span>

### <span data-ttu-id="d84f0-159">System.management.managementobject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="d84f0-159">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="d84f0-160">`Get-HotFix` 返回表示计算机上的修补程序的对象。</span><span class="sxs-lookup"><span data-stu-id="d84f0-160">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="d84f0-161">注释</span><span class="sxs-lookup"><span data-stu-id="d84f0-161">NOTES</span></span>

<span data-ttu-id="d84f0-162">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="d84f0-162">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="d84f0-163">**Win32_QuickFixEngineering** [WMI 类](/windows/desktop/WmiSdk/retrieving-a-class)表示系统范围较小的更新，通常称为 "快速修补工程"， (QFE) update，应用于当前操作系统。</span><span class="sxs-lookup"><span data-stu-id="d84f0-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="d84f0-164">此类仅返回由基于组件的服务所提供的更新 (CBS) 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="d84f0-165">注册表中未列出这些更新。</span><span class="sxs-lookup"><span data-stu-id="d84f0-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="d84f0-166">**Win32_QuickFixEngineering** 未返回 MICROSOFT WINDOWS INSTALLER (MSI) 或 [Windows 更新](https://update.microsoft.com)站点提供的更新。</span><span class="sxs-lookup"><span data-stu-id="d84f0-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="d84f0-167">有关详细信息，请参阅 [Win32_QuickFixEngineering 类](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="d84f0-168">`Get-HotFix`不同操作系统上的输出可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="d84f0-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="d84f0-169">相关链接</span><span class="sxs-lookup"><span data-stu-id="d84f0-169">RELATED LINKS</span></span>

[<span data-ttu-id="d84f0-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="d84f0-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="d84f0-171">Add-Content</span><span class="sxs-lookup"><span data-stu-id="d84f0-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="d84f0-172">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d84f0-172">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="d84f0-173">Win32_QuickFixEngineering 类</span><span class="sxs-lookup"><span data-stu-id="d84f0-173">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
