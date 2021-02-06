---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 5630c4d09a2806eb117d005466d4925c1740d3a7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595610"
---
# <span data-ttu-id="a7bad-102">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a7bad-102">Get-Credential</span></span>

## <span data-ttu-id="a7bad-103">摘要</span><span class="sxs-lookup"><span data-stu-id="a7bad-103">SYNOPSIS</span></span>
<span data-ttu-id="a7bad-104">获取基于用户名和密码的凭据对象。</span><span class="sxs-lookup"><span data-stu-id="a7bad-104">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="a7bad-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7bad-105">SYNTAX</span></span>

### <span data-ttu-id="a7bad-106">CredentialSet（默认值）</span><span class="sxs-lookup"><span data-stu-id="a7bad-106">CredentialSet (Default)</span></span>

```
Get-Credential [[-Credential] <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="a7bad-107">MessageSet</span><span class="sxs-lookup"><span data-stu-id="a7bad-107">MessageSet</span></span>

```
Get-Credential [-Message <String>] [[-UserName] <String>] [-Title <String>] [<CommonParameters>]
```

## <span data-ttu-id="a7bad-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a7bad-108">DESCRIPTION</span></span>

<span data-ttu-id="a7bad-109">`Get-Credential`Cmdlet 将为指定的用户名和密码创建凭据对象。</span><span class="sxs-lookup"><span data-stu-id="a7bad-109">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="a7bad-110">你可以在安全操作中使用凭据对象。</span><span class="sxs-lookup"><span data-stu-id="a7bad-110">You can use the credential object in security operations.</span></span>

<span data-ttu-id="a7bad-111">该 `Get-Credential` cmdlet 会提示用户输入密码或用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-111">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="a7bad-112">您可以使用 **Message** 参数在命令行提示符下指定自定义消息。</span><span class="sxs-lookup"><span data-stu-id="a7bad-112">You can use the **Message** parameter to specify a customized message in the command line prompt.</span></span>

## <span data-ttu-id="a7bad-113">示例</span><span class="sxs-lookup"><span data-stu-id="a7bad-113">EXAMPLES</span></span>

### <span data-ttu-id="a7bad-114">示例 1</span><span class="sxs-lookup"><span data-stu-id="a7bad-114">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="a7bad-115">此命令将获取凭据对象，并将其保存在 `$c` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-115">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="a7bad-116">当你输入命令时，系统将提示你输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-116">When you enter the command, you are prompted for a user name and password.</span></span> <span data-ttu-id="a7bad-117">输入所需的信息时，该 cmdlet 将创建一个表示用户凭据的 **PSCredential** 对象，并将其保存在 `$c` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-117">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="a7bad-118">你可以将对象用作请求用户身份验证的 cmdlet（例如，具有 **Credential** 参数的 cmdlet）的输入。</span><span class="sxs-lookup"><span data-stu-id="a7bad-118">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="a7bad-119">但是，某些随 PowerShell 一起安装的提供程序不支持 **Credential** 参数。</span><span class="sxs-lookup"><span data-stu-id="a7bad-119">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="a7bad-120">示例 2</span><span class="sxs-lookup"><span data-stu-id="a7bad-120">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="a7bad-121">这些命令使用 cmdlet 返回的凭据对象对 `Get-Credential` 远程计算机上的用户进行身份验证，以便它们可以使用 Windows Management Instrumentation (WMI) 来管理计算机。</span><span class="sxs-lookup"><span data-stu-id="a7bad-121">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="a7bad-122">第一个命令将获取凭据对象，并将其保存在 `$c` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-122">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="a7bad-123">第二个命令使用命令中的凭据对象 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-123">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="a7bad-124">此命令将获取 Server01 计算机上有关磁盘驱动器的信息。</span><span class="sxs-lookup"><span data-stu-id="a7bad-124">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="a7bad-125">示例 3</span><span class="sxs-lookup"><span data-stu-id="a7bad-125">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="a7bad-126">此命令显示如何将命令包含 `Get-Credential` 在命令中  `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-126">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="a7bad-127">此命令使用 `Get-CimInstance` cmdlet 来获取有关 Server01 计算机上的 BIOS 的信息。</span><span class="sxs-lookup"><span data-stu-id="a7bad-127">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="a7bad-128">它使用 **credential** 参数对 user、Domain01\User01 和 `Get-Credential` command 作为 **Credential** 参数的值进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a7bad-128">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="a7bad-129">示例 4</span><span class="sxs-lookup"><span data-stu-id="a7bad-129">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="a7bad-130">此示例将创建一个包含用户名（不带域名）的凭据。</span><span class="sxs-lookup"><span data-stu-id="a7bad-130">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="a7bad-131">第一个命令获取用户名为 User01 的凭据，并将其存储在 `$c` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-131">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="a7bad-132">第二个命令将显示生成的凭据对象的 **Username** 属性值。</span><span class="sxs-lookup"><span data-stu-id="a7bad-132">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="a7bad-133">示例 5</span><span class="sxs-lookup"><span data-stu-id="a7bad-133">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="a7bad-134">此命令使用 **PromptForCredential** 方法提示用户输入其用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-134">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="a7bad-135">该命令将生成的凭据保存在 `$Credential` 变量中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-135">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="a7bad-136">**PromptForCredential** 方法是使用 cmdlet 的替代方法 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-136">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a7bad-137">当使用 **PromptForCredential** 时，可以指定在提示中显示的标题、消息和用户名。</span><span class="sxs-lookup"><span data-stu-id="a7bad-137">When you use **PromptForCredential**, you can specify the caption, messages, and user name that appear in the prompt.</span></span>

<span data-ttu-id="a7bad-138">有关详细信息，请参阅 SDK 中的 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 文档。</span><span class="sxs-lookup"><span data-stu-id="a7bad-138">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="a7bad-139">示例 6</span><span class="sxs-lookup"><span data-stu-id="a7bad-139">Example 6</span></span>

<span data-ttu-id="a7bad-140">此示例演示如何创建一个与不提示用户就返回的对象完全相同的凭据对象 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-140">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="a7bad-141">此方法要求输入纯文本密码，这可能会违反某些企业内的安全标准。</span><span class="sxs-lookup"><span data-stu-id="a7bad-141">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="a7bad-142">第一个命令将用户帐户名称保存在 `$User` 参数中。</span><span class="sxs-lookup"><span data-stu-id="a7bad-142">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="a7bad-143">该值必须具有“Domain\User”或“ComputerName\User”格式。</span><span class="sxs-lookup"><span data-stu-id="a7bad-143">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="a7bad-144">第二个命令使用 `ConvertTo-SecureString` cmdlet 从纯文本密码创建一个安全字符串。</span><span class="sxs-lookup"><span data-stu-id="a7bad-144">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="a7bad-145">该命令使用 **AsPlainText** 参数来指示该字符串为纯文本，并使用 **Force** 参数来确认你了解使用纯文本的风险。</span><span class="sxs-lookup"><span data-stu-id="a7bad-145">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="a7bad-146">第三个命令使用 `New-Object` cmdlet 从和变量中的值创建 **PSCredential** 对象 `$User` `$PWord` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-146">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="a7bad-147">示例 7</span><span class="sxs-lookup"><span data-stu-id="a7bad-147">Example 7</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="a7bad-148">此命令使用 cmdlet 的 **Message** 和 **UserName** 参数 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-148">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a7bad-149">此命令格式旨在用于共享的脚本和函数。</span><span class="sxs-lookup"><span data-stu-id="a7bad-149">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="a7bad-150">在此示例中，消息将告知用户为何需要凭据，并使他们能够确信此请求是合法的。</span><span class="sxs-lookup"><span data-stu-id="a7bad-150">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="a7bad-151">示例 8</span><span class="sxs-lookup"><span data-stu-id="a7bad-151">Example 8</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="a7bad-152">此命令将从 Server01 远程计算机获取凭据。</span><span class="sxs-lookup"><span data-stu-id="a7bad-152">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="a7bad-153">该命令使用 `Invoke-Command` cmdlet `Get-Credential` 在远程计算机上运行命令。</span><span class="sxs-lookup"><span data-stu-id="a7bad-153">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="a7bad-154">输出显示 `Get-Credential` 在身份验证提示中包含的远程安全消息。</span><span class="sxs-lookup"><span data-stu-id="a7bad-154">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="a7bad-155">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7bad-155">PARAMETERS</span></span>

### <span data-ttu-id="a7bad-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="a7bad-156">-Credential</span></span>

<span data-ttu-id="a7bad-157">指定凭据的用户名，例如 **User01** 或 **Domain01\User01**。</span><span class="sxs-lookup"><span data-stu-id="a7bad-157">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="a7bad-158">参数名称 `-Credential` 是可选的。</span><span class="sxs-lookup"><span data-stu-id="a7bad-158">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="a7bad-159">提交该命令并指定用户名时，系统将提示你输入密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-159">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="a7bad-160">如果省略此参数，系统会提示输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-160">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="a7bad-161">从 PowerShell 3.0 开始，如果输入的用户名没有域，则不再在 `Get-Credential` 名称之前插入反斜杠。</span><span class="sxs-lookup"><span data-stu-id="a7bad-161">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="a7bad-162">凭据存储在 [PSCredential](/dotnet/api/system.management.automation.pscredential) 对象中，密码存储为 [SecureString](/dotnet/api/system.security.securestring)。</span><span class="sxs-lookup"><span data-stu-id="a7bad-162">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a7bad-163">有关 **SecureString** 数据保护的详细信息，请参阅 [SecureString 的安全级别？](/dotnet/api/system.security.securestring#how-secure-is-securestring)。</span><span class="sxs-lookup"><span data-stu-id="a7bad-163">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7bad-164">-Message</span><span class="sxs-lookup"><span data-stu-id="a7bad-164">-Message</span></span>

<span data-ttu-id="a7bad-165">指定将在身份验证提示中显示的消息。</span><span class="sxs-lookup"><span data-stu-id="a7bad-165">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="a7bad-166">此参数旨在用于函数或脚本。</span><span class="sxs-lookup"><span data-stu-id="a7bad-166">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="a7bad-167">你可以使用该消息向用户说明你为什么要请求凭据以及将如何使用它们。</span><span class="sxs-lookup"><span data-stu-id="a7bad-167">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="a7bad-168">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a7bad-168">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7bad-169">-Title</span><span class="sxs-lookup"><span data-stu-id="a7bad-169">-Title</span></span>

<span data-ttu-id="a7bad-170">设置控制台中身份验证提示的标题行的文本。</span><span class="sxs-lookup"><span data-stu-id="a7bad-170">Sets the text of the title line for the authentication prompt in the console.</span></span>

<span data-ttu-id="a7bad-171">此参数是在 PowerShell 6.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a7bad-171">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7bad-172">-UserName</span><span class="sxs-lookup"><span data-stu-id="a7bad-172">-UserName</span></span>

<span data-ttu-id="a7bad-173">指定用户名。</span><span class="sxs-lookup"><span data-stu-id="a7bad-173">Specifies a user name.</span></span> <span data-ttu-id="a7bad-174">身份验证提示要求输入该用户名对应的密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-174">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="a7bad-175">默认情况下，用户名为空并且身份验证提示将请求输入用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="a7bad-175">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="a7bad-176">此参数是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="a7bad-176">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7bad-177">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7bad-177">CommonParameters</span></span>

<span data-ttu-id="a7bad-178">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a7bad-178">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7bad-179">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a7bad-179">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7bad-180">输入</span><span class="sxs-lookup"><span data-stu-id="a7bad-180">INPUTS</span></span>

### <span data-ttu-id="a7bad-181">无</span><span class="sxs-lookup"><span data-stu-id="a7bad-181">None</span></span>

<span data-ttu-id="a7bad-182">不能通过管道将输入传递给此 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a7bad-182">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a7bad-183">输出</span><span class="sxs-lookup"><span data-stu-id="a7bad-183">OUTPUTS</span></span>

### <span data-ttu-id="a7bad-184">System.Management.Automation.PSCredential</span><span class="sxs-lookup"><span data-stu-id="a7bad-184">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="a7bad-185">`Get-Credential` 返回凭据对象。</span><span class="sxs-lookup"><span data-stu-id="a7bad-185">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="a7bad-186">注释</span><span class="sxs-lookup"><span data-stu-id="a7bad-186">NOTES</span></span>

<span data-ttu-id="a7bad-187">你可以使用 `Get-Credential` 在请求用户身份验证的 cmdlet （例如，具有 **Credential** 参数的 Cmdlet）中创建的 PSCredential 对象。</span><span class="sxs-lookup"><span data-stu-id="a7bad-187">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="a7bad-188">与 PowerShell 一起安装的所有提供程序都不支持 **Credential** 参数。</span><span class="sxs-lookup"><span data-stu-id="a7bad-188">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="a7bad-189">从 PowerShell 3.0 开始，在 select cmdlet （如和 cmdlet）上受 `Get-Content` 支持 `New-PSDrive` 。</span><span class="sxs-lookup"><span data-stu-id="a7bad-189">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="a7bad-190">相关链接</span><span class="sxs-lookup"><span data-stu-id="a7bad-190">RELATED LINKS</span></span>

[<span data-ttu-id="a7bad-191">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="a7bad-191">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
