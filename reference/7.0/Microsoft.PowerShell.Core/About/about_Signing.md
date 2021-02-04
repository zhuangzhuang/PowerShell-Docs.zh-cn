---
description: 说明如何对脚本进行签名以使它们符合 PowerShell 执行策略。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 202af7ea491b8fa020ab2ff7ae6b1cc697829b6b
ms.sourcegitcommit: 021ea294327dec542ec040619dac0d2171397a90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/29/2020
ms.locfileid: "97804123"
---
# <a name="about-signing"></a>关于签名

## <a name="short-description"></a>简短说明
说明如何对脚本进行签名以使它们符合 PowerShell 执行策略。

## <a name="long-description"></a>长说明

受限执行策略不允许运行任何脚本。 **AllSigned** 和 **RemoteSigned** 执行策略阻止 PowerShell 运行没有数字签名的脚本。

本主题说明如何运行未签名的选定脚本，即使执行策略是 **RemoteSigned** 的，以及如何对脚本进行签名以供自己使用。

有关 PowerShell 执行策略的详细信息，请参阅 [about_Execution_Policies](about_Execution_Policies.md)。

## <a name="to-permit-signed-scripts-to-run"></a>允许要运行的签名脚本

第一次在计算机上启动 PowerShell 时， (默认) 可能有效的 **受限制** 执行策略。

**受限制** 的策略不允许运行任何脚本。

若要在计算机上查找有效的执行策略，请键入：

```powershell
Get-ExecutionPolicy
```

若要运行你在本地计算机上编写的未签名脚本和其他用户的签名脚本，请使用 "以管理员身份运行" 选项启动 PowerShell，然后使用以下命令将计算机上的执行策略更改为 **RemoteSigned**：

```powershell
Set-ExecutionPolicy RemoteSigned
```

有关详细信息，请参阅 cmdlet 的帮助主题 `Set-ExecutionPolicy` 。

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>使用 RemoteSigned 执行策略运行未签名的脚本

如果你的 PowerShell 执行策略是 **RemoteSigned**，则 powershell 将不会运行从 internet 下载的未签名脚本，包括你通过电子邮件和即时消息程序收到的未签名脚本。

如果尝试运行下载的脚本，则 PowerShell 将显示以下错误消息：

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

在运行该脚本之前，请查看代码以确保你信任它。
脚本与任何可执行程序的效果相同。

若要运行未签名的脚本，请使用 Unblock-File cmdlet，或使用以下过程。

1. 将脚本文件保存到计算机上。
2. 单击 "开始"，再单击 "我的电脑"，然后找到保存的脚本文件。
3. 右键单击脚本文件，然后单击 "属性"。
4. 单击“解除阻止”。

如果从 internet 下载的脚本已经过数字签名，但你尚未选择信任其发行者，则 PowerShell 将显示以下消息：

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

如果信任发布者，请选择 "运行一次" 或 "始终运行"。 如果你不信任发布者，请选择 "从不运行" 或 "不运行"。 如果选择 "从不运行" 或 "始终运行"，则 PowerShell 不会再次提示你提供此发布者。

## <a name="methods-of-signing-scripts"></a>脚本签名方法

你可以对你编写的脚本和从其他源获取的脚本进行签名。 对任何脚本进行签名之前，请检查每个命令以验证是否可以安全运行。

有关代码签名的最佳实践，请参阅 [代码签名最佳做法](/previous-versions/windows/hardware/design/dn653556(v=vs.85))。

有关如何对脚本文件进行签名的详细信息，请参阅 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)。

`New-SelfSignedCertificate`Cmdlet 是在 PowerShell 3.0 的 PKI 模块中引入的，它创建适用于测试的自签名证书。 有关详细信息，请参阅 New-SelfSignedCertificate cmdlet 的帮助主题。

若要将数字签名添加到脚本，必须使用代码签名证书对其进行签名。 两种类型的证书适用于对脚本文件进行签名：

- 证书颁发机构创建的证书：为了付费，公共证书颁发机构将验证你的身份，并提供代码签名证书。 从著名的证书颁发机构购买证书时，可以与运行 Windows 的其他计算机上的用户共享脚本，因为这些计算机信任证书颁发机构。

- 你创建的证书：你可以创建一个自签名证书，你的计算机为其创建证书的证书颁发机构。 此证书免费，并使你能够在你的计算机上写入、签署和运行脚本。 但是，由自签名证书签名的脚本将不会在其他计算机上运行。

通常，您只使用自签名证书来签署您为自己使用而编写的脚本，并对您从已验证为安全的其他源中获取的脚本进行签名。 它不适用于共享的脚本，甚至是企业内部的脚本。

如果创建自签名证书，请务必对证书启用强私钥保护。 这可以防止恶意程序代表您对脚本进行签名。 本主题末尾包含了相关说明。

## <a name="create-a-self-signed-certificate"></a>创建自签名证书

若要创建自签名证书，请使用 `New-SelfSignedCertificate` PKI 模块中的 cmdlet。 此模块是在 PowerShell 3.0 中引入的，并且包含在 Windows 8 和 Windows Server 2012 中。 有关详细信息，请参阅 cmdlet 的帮助主题 `New-SelfSignedCertificate` 。

若要在 Windows 的早期版本中创建自签名证书，请使用证书创建工具 `MakeCert.exe` 。 此工具包含在 Microsoft .NET SDK (版本1.1 及更高版本) 和 Microsoft Windows SDK 中。

有关 MakeCert.exe 工具的语法和参数说明的详细信息，请参阅 [# A1)  ( 证书创建工具 ](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))。

若要使用 MakeCert.exe 工具创建证书，请在 "SDK 命令提示符" 窗口中运行以下命令。

注意：第一个命令将为您的计算机创建本地证书颁发机构。 第二个命令从证书颁发机构生成个人证书。

注意：你可以完全按其显示方式复制或键入命令。 不需要进行替换，但你可以更改证书名称。

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

MakeCert.exe 工具将提示你输入私钥密码。 密码确保在未经你同意的情况下没有人可以使用或访问证书。
创建并输入可以记住的密码。 稍后将使用此密码来检索证书。

若要验证证书是否已正确生成，请使用以下命令获取计算机上的证书存储中的证书。 在文件系统目录中找不到证书文件。

在 PowerShell 提示符下，键入：

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

此命令使用 PowerShell 证书提供程序查看有关证书的信息。

如果创建了证书，则输出将显示在类似于以下内容的显示中标识证书的 **指纹** ：

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>签名脚本

创建自签名证书后，你可以对脚本进行签名。 如果使用 **AllSigned** 执行策略，则签名脚本将允许你在计算机上运行脚本。

下面的示例脚本对 `Add-Signature.ps1` 脚本进行签名。 但是，如果使用的是 **AllSigned** 执行策略，则必须在 `Add-Signature.ps1` 运行脚本之前对脚本进行签名。

> [!IMPORTANT]
> 必须使用 ASCII 或 UTF8NoBOM 编码保存脚本。你可以对使用其他编码的脚本文件进行签名。 但脚本运行失败或包含脚本的模块导入失败。

若要使用此脚本，请将以下文本复制到文本文件中，并将其命名为 `Add-Signature.ps1` 。

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

若要对 `Add-Signature.ps1` 脚本文件进行签名，请在 PowerShell 命令提示符下键入以下命令：

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

脚本签名后，可以在本地计算机上运行它。 但是，该脚本将不会在运行 PowerShell 的计算机上运行。 如果尝试，PowerShell 将显示以下错误消息：

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

如果在运行未编写的脚本时 PowerShell 显示此消息，请像处理任何未签名脚本一样处理该文件。 检查代码以确定是否可以信任该脚本。

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>为证书启用强私钥保护

如果你的计算机上有私有证书，恶意程序可能会代表你对脚本进行签名，这会授权 PowerShell 运行它们。

若要防止代表你自动登录，请使用证书管理器将 `Certmgr.exe` 签名证书导出到 `.pfx` 文件。 证书管理器包含在 Microsoft .NET SDK、Microsoft Windows SDK 和 internet Explorer 中。

若要导出证书：

1. 启动证书管理器。
2. 选择 "PowerShell 本地证书颁发机构颁发的证书" 根目录。
3. 单击 "导出" 以启动证书导出向导。
4. 选择 "是，导出私钥"，然后单击 "下一步"。
5. 选择 "启用加强保护"。
6. 键入密码，然后再次键入密码进行确认。
7. 键入具有 .pfx 文件扩展名的文件名。
8. 单击“完成”。

重新导入证书：

1. 启动证书管理器。
2. 单击 "导入" 以启动 "证书导入向导"。
3. 打开到在导出过程中创建的 .pfx 文件所在的位置。
4. 在 "密码" 页上，选择 "启用强私钥保护"，然后输入在导出过程中分配的密码。
5. 选择“个人”证书存储。
6. 单击“完成”。

## <a name="prevent-the-signature-from-expiring"></a>阻止签名过期

在签名证书过期之前，脚本中的数字签名是有效的，只要时间戳服务器可以验证脚本是否经过签名，但签名证书有效。

由于大多数签名证书仅在一年内有效，因此使用时间戳服务器可确保用户可以使用您的脚本多年。

## <a name="see-also"></a>另请参阅

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[代码签名简介](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
