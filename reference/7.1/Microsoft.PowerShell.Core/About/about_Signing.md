---
description: 说明如何对脚本进行签名以使它们符合 PowerShell 执行策略。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 5ad2f417fc31c18f40e6ce823fe07883cb8367dc
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685622"
---
# <a name="about-signing"></a><span data-ttu-id="fb495-104">关于签名</span><span class="sxs-lookup"><span data-stu-id="fb495-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="fb495-105">简短说明</span><span class="sxs-lookup"><span data-stu-id="fb495-105">Short description</span></span>
<span data-ttu-id="fb495-106">说明如何对脚本进行签名以使它们符合 PowerShell 执行策略。</span><span class="sxs-lookup"><span data-stu-id="fb495-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="fb495-107">长说明</span><span class="sxs-lookup"><span data-stu-id="fb495-107">Long description</span></span>

<span data-ttu-id="fb495-108">受限执行策略不允许运行任何脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="fb495-109">**AllSigned** 和 **RemoteSigned** 执行策略阻止 PowerShell 运行没有数字签名的脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="fb495-110">本主题说明如何运行未签名的选定脚本，即使执行策略是 **RemoteSigned** 的，以及如何对脚本进行签名以供自己使用。</span><span class="sxs-lookup"><span data-stu-id="fb495-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned**, and how to sign scripts for your own use.</span></span>

<span data-ttu-id="fb495-111">有关 PowerShell 执行策略的详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。</span><span class="sxs-lookup"><span data-stu-id="fb495-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="fb495-112">允许要运行的签名脚本</span><span class="sxs-lookup"><span data-stu-id="fb495-112">To permit signed scripts to run</span></span>

<span data-ttu-id="fb495-113">第一次在计算机上启动 PowerShell 时， (默认) 可能有效的 **受限制** 执行策略。</span><span class="sxs-lookup"><span data-stu-id="fb495-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="fb495-114">**受限制** 的策略不允许运行任何脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="fb495-115">若要在计算机上查找有效的执行策略，请键入：</span><span class="sxs-lookup"><span data-stu-id="fb495-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="fb495-116">若要运行你在本地计算机上编写的未签名脚本和其他用户的签名脚本，请使用 "以管理员身份运行" 选项启动 PowerShell，然后使用以下命令将计算机上的执行策略更改为 **RemoteSigned**：</span><span class="sxs-lookup"><span data-stu-id="fb495-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned**:</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="fb495-117">有关详细信息，请参阅 cmdlet 的帮助主题 `Set-ExecutionPolicy` 。</span><span class="sxs-lookup"><span data-stu-id="fb495-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="fb495-118">使用 RemoteSigned 执行策略运行未签名的脚本</span><span class="sxs-lookup"><span data-stu-id="fb495-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="fb495-119">如果你的 PowerShell 执行策略是 **RemoteSigned**，则 powershell 将不会运行从 internet 下载的未签名脚本，包括你通过电子邮件和即时消息程序收到的未签名脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-119">If your PowerShell execution policy is **RemoteSigned**, PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="fb495-120">如果尝试运行下载的脚本，则 PowerShell 将显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="fb495-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="fb495-121">在运行该脚本之前，请查看代码以确保你信任它。</span><span class="sxs-lookup"><span data-stu-id="fb495-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="fb495-122">脚本与任何可执行程序的效果相同。</span><span class="sxs-lookup"><span data-stu-id="fb495-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="fb495-123">若要运行未签名的脚本，请使用 Unblock-File cmdlet，或使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="fb495-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="fb495-124">将脚本文件保存到计算机上。</span><span class="sxs-lookup"><span data-stu-id="fb495-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="fb495-125">单击 "开始"，再单击 "我的电脑"，然后找到保存的脚本文件。</span><span class="sxs-lookup"><span data-stu-id="fb495-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="fb495-126">右键单击脚本文件，然后单击 "属性"。</span><span class="sxs-lookup"><span data-stu-id="fb495-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="fb495-127">单击“解除阻止”。</span><span class="sxs-lookup"><span data-stu-id="fb495-127">Click Unblock.</span></span>

<span data-ttu-id="fb495-128">如果从 internet 下载的脚本已经过数字签名，但你尚未选择信任其发行者，则 PowerShell 将显示以下消息：</span><span class="sxs-lookup"><span data-stu-id="fb495-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="fb495-129">如果信任发布者，请选择 "运行一次" 或 "始终运行"。</span><span class="sxs-lookup"><span data-stu-id="fb495-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="fb495-130">如果你不信任发布者，请选择 "从不运行" 或 "不运行"。</span><span class="sxs-lookup"><span data-stu-id="fb495-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="fb495-131">如果选择 "从不运行" 或 "始终运行"，则 PowerShell 不会再次提示你提供此发布者。</span><span class="sxs-lookup"><span data-stu-id="fb495-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="fb495-132">脚本签名方法</span><span class="sxs-lookup"><span data-stu-id="fb495-132">Methods of signing scripts</span></span>

<span data-ttu-id="fb495-133">你可以对你编写的脚本和从其他源获取的脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="fb495-134">对任何脚本进行签名之前，请检查每个命令以验证是否可以安全运行。</span><span class="sxs-lookup"><span data-stu-id="fb495-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="fb495-135">有关代码签名的最佳实践，请参阅 [代码签名最佳做法](/previous-versions/windows/hardware/design/dn653556(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="fb495-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="fb495-136">有关如何对脚本文件进行签名的详细信息，请参阅 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)。</span><span class="sxs-lookup"><span data-stu-id="fb495-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="fb495-137">`New-SelfSignedCertificate`Cmdlet 是在 PowerShell 3.0 的 PKI 模块中引入的，它创建适用于测试的自签名证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="fb495-138">有关详细信息，请参阅 New-SelfSignedCertificate cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="fb495-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="fb495-139">若要将数字签名添加到脚本，必须使用代码签名证书对其进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="fb495-140">两种类型的证书适用于对脚本文件进行签名：</span><span class="sxs-lookup"><span data-stu-id="fb495-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="fb495-141">证书颁发机构创建的证书：为了付费，公共证书颁发机构将验证你的身份，并提供代码签名证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="fb495-142">从著名的证书颁发机构购买证书时，可以与运行 Windows 的其他计算机上的用户共享脚本，因为这些计算机信任证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="fb495-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="fb495-143">你创建的证书：你可以创建一个自签名证书，你的计算机为其创建证书的证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="fb495-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="fb495-144">此证书免费，并使你能够在你的计算机上写入、签署和运行脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="fb495-145">但是，由自签名证书签名的脚本将不会在其他计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fb495-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="fb495-146">通常，您只使用自签名证书来签署您为自己使用而编写的脚本，并对您从已验证为安全的其他源中获取的脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="fb495-147">它不适用于共享的脚本，甚至是企业内部的脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="fb495-148">如果创建自签名证书，请务必对证书启用强私钥保护。</span><span class="sxs-lookup"><span data-stu-id="fb495-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="fb495-149">这可以防止恶意程序代表您对脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="fb495-150">本主题末尾包含了相关说明。</span><span class="sxs-lookup"><span data-stu-id="fb495-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="fb495-151">创建自签名证书</span><span class="sxs-lookup"><span data-stu-id="fb495-151">Create a self-signed certificate</span></span>

<span data-ttu-id="fb495-152">若要创建自签名证书，请使用 `New-SelfSignedCertificate` PKI 模块中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="fb495-152">To create a self-signed certificate, use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="fb495-153">此模块是在 PowerShell 3.0 中引入的，并且包含在 Windows 8 和 Windows Server 2012 中。</span><span class="sxs-lookup"><span data-stu-id="fb495-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="fb495-154">有关详细信息，请参阅 cmdlet 的帮助主题 `New-SelfSignedCertificate` 。</span><span class="sxs-lookup"><span data-stu-id="fb495-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="fb495-155">若要在 Windows 的早期版本中创建自签名证书，请使用证书创建工具 `MakeCert.exe` 。</span><span class="sxs-lookup"><span data-stu-id="fb495-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="fb495-156">此工具包含在 Microsoft .NET SDK (版本1.1 及更高版本) 和 Microsoft Windows SDK 中。</span><span class="sxs-lookup"><span data-stu-id="fb495-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="fb495-157">有关 MakeCert.exe 工具的语法和参数说明的详细信息，请参阅 [ (MakeCert.exe) 的证书创建工具 ](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))。</span><span class="sxs-lookup"><span data-stu-id="fb495-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="fb495-158">若要使用 MakeCert.exe 工具创建证书，请在 "SDK 命令提示符" 窗口中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="fb495-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="fb495-159">注意：第一个命令将为您的计算机创建本地证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="fb495-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="fb495-160">第二个命令从证书颁发机构生成个人证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="fb495-161">注意：你可以完全按其显示方式复制或键入命令。</span><span class="sxs-lookup"><span data-stu-id="fb495-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="fb495-162">不需要进行替换，但你可以更改证书名称。</span><span class="sxs-lookup"><span data-stu-id="fb495-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="fb495-163">MakeCert.exe 工具将提示你输入私钥密码。</span><span class="sxs-lookup"><span data-stu-id="fb495-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="fb495-164">密码确保在未经你同意的情况下没有人可以使用或访问证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="fb495-165">创建并输入可以记住的密码。</span><span class="sxs-lookup"><span data-stu-id="fb495-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="fb495-166">稍后将使用此密码来检索证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="fb495-167">若要验证证书是否已正确生成，请使用以下命令获取计算机上的证书存储中的证书。</span><span class="sxs-lookup"><span data-stu-id="fb495-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="fb495-168">在文件系统目录中找不到证书文件。</span><span class="sxs-lookup"><span data-stu-id="fb495-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="fb495-169">在 PowerShell 提示符下，键入：</span><span class="sxs-lookup"><span data-stu-id="fb495-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="fb495-170">此命令使用 PowerShell 证书提供程序查看有关证书的信息。</span><span class="sxs-lookup"><span data-stu-id="fb495-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="fb495-171">如果创建了证书，则输出将显示在类似于以下内容的显示中标识证书的 **指纹** ：</span><span class="sxs-lookup"><span data-stu-id="fb495-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="fb495-172">签名脚本</span><span class="sxs-lookup"><span data-stu-id="fb495-172">Sign a script</span></span>

<span data-ttu-id="fb495-173">创建自签名证书后，你可以对脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="fb495-174">如果使用 **AllSigned** 执行策略，则签名脚本将允许你在计算机上运行脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="fb495-175">下面的示例脚本对 `Add-Signature.ps1` 脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="fb495-176">但是，如果使用的是 **AllSigned** 执行策略，则必须在 `Add-Signature.ps1` 运行脚本之前对脚本进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb495-177">必须使用 ASCII 或 UTF8NoBOM 编码保存脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-177">The script must be saved using ASCII or UTF8NoBOM encoding.</span></span> <span data-ttu-id="fb495-178">你可以对使用其他编码的脚本文件进行签名。</span><span class="sxs-lookup"><span data-stu-id="fb495-178">You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="fb495-179">但脚本运行失败或包含脚本的模块导入失败。</span><span class="sxs-lookup"><span data-stu-id="fb495-179">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="fb495-180">若要使用此脚本，请将以下文本复制到文本文件中，并将其命名为 `Add-Signature.ps1` 。</span><span class="sxs-lookup"><span data-stu-id="fb495-180">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="fb495-181">若要对 `Add-Signature.ps1` 脚本文件进行签名，请在 PowerShell 命令提示符下键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="fb495-181">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="fb495-182">脚本签名后，可以在本地计算机上运行它。</span><span class="sxs-lookup"><span data-stu-id="fb495-182">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="fb495-183">但是，该脚本将不会在运行 PowerShell 的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="fb495-183">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="fb495-184">如果尝试，PowerShell 将显示以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="fb495-184">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="fb495-185">如果在运行未编写的脚本时 PowerShell 显示此消息，请像处理任何未签名脚本一样处理该文件。</span><span class="sxs-lookup"><span data-stu-id="fb495-185">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="fb495-186">检查代码以确定是否可以信任该脚本。</span><span class="sxs-lookup"><span data-stu-id="fb495-186">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="fb495-187">为证书启用强私钥保护</span><span class="sxs-lookup"><span data-stu-id="fb495-187">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="fb495-188">如果你的计算机上有私有证书，恶意程序可能会代表你对脚本进行签名，这会授权 PowerShell 运行它们。</span><span class="sxs-lookup"><span data-stu-id="fb495-188">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="fb495-189">若要防止代表你自动登录，请使用证书管理器将 `Certmgr.exe` 签名证书导出到 `.pfx` 文件。</span><span class="sxs-lookup"><span data-stu-id="fb495-189">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="fb495-190">证书管理器包含在 Microsoft .NET SDK、Microsoft Windows SDK 和 internet Explorer 中。</span><span class="sxs-lookup"><span data-stu-id="fb495-190">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="fb495-191">若要导出证书：</span><span class="sxs-lookup"><span data-stu-id="fb495-191">To export the certificate:</span></span>

1. <span data-ttu-id="fb495-192">启动证书管理器。</span><span class="sxs-lookup"><span data-stu-id="fb495-192">Start Certificate Manager.</span></span>
2. <span data-ttu-id="fb495-193">选择 "PowerShell 本地证书颁发机构颁发的证书" 根目录。</span><span class="sxs-lookup"><span data-stu-id="fb495-193">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="fb495-194">单击 "导出" 以启动证书导出向导。</span><span class="sxs-lookup"><span data-stu-id="fb495-194">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="fb495-195">选择 "是，导出私钥"，然后单击 "下一步"。</span><span class="sxs-lookup"><span data-stu-id="fb495-195">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="fb495-196">选择 "启用加强保护"。</span><span class="sxs-lookup"><span data-stu-id="fb495-196">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="fb495-197">键入密码，然后再次键入密码进行确认。</span><span class="sxs-lookup"><span data-stu-id="fb495-197">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="fb495-198">键入具有 .pfx 文件扩展名的文件名。</span><span class="sxs-lookup"><span data-stu-id="fb495-198">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="fb495-199">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="fb495-199">Click Finish.</span></span>

<span data-ttu-id="fb495-200">重新导入证书：</span><span class="sxs-lookup"><span data-stu-id="fb495-200">To re-import the certificate:</span></span>

1. <span data-ttu-id="fb495-201">启动证书管理器。</span><span class="sxs-lookup"><span data-stu-id="fb495-201">Start Certificate Manager.</span></span>
2. <span data-ttu-id="fb495-202">单击 "导入" 以启动 "证书导入向导"。</span><span class="sxs-lookup"><span data-stu-id="fb495-202">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="fb495-203">打开到在导出过程中创建的 .pfx 文件所在的位置。</span><span class="sxs-lookup"><span data-stu-id="fb495-203">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="fb495-204">在 "密码" 页上，选择 "启用强私钥保护"，然后输入在导出过程中分配的密码。</span><span class="sxs-lookup"><span data-stu-id="fb495-204">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="fb495-205">选择“个人”证书存储。</span><span class="sxs-lookup"><span data-stu-id="fb495-205">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="fb495-206">单击“完成”。</span><span class="sxs-lookup"><span data-stu-id="fb495-206">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="fb495-207">阻止签名过期</span><span class="sxs-lookup"><span data-stu-id="fb495-207">Prevent the signature from expiring</span></span>

<span data-ttu-id="fb495-208">在签名证书过期之前，脚本中的数字签名是有效的，只要时间戳服务器可以验证脚本是否经过签名，但签名证书有效。</span><span class="sxs-lookup"><span data-stu-id="fb495-208">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="fb495-209">由于大多数签名证书仅在一年内有效，因此使用时间戳服务器可确保用户可以使用您的脚本多年。</span><span class="sxs-lookup"><span data-stu-id="fb495-209">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb495-210">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb495-210">See also</span></span>

[<span data-ttu-id="fb495-211">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="fb495-211">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="fb495-212">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="fb495-212">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="fb495-213">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fb495-213">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="fb495-214">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fb495-214">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="fb495-215">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="fb495-215">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="fb495-216">[代码签名简介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="fb495-216">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
