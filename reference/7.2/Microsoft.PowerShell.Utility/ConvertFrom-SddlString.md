---
external help file: Microsoft.PowerShell.Utility-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 5c8e963486c0d4f5f3e7d643cb65c752720f37d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603401"
---
# <span data-ttu-id="0ee4e-102">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="0ee4e-102">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="0ee4e-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0ee4e-103">SYNOPSIS</span></span>
<span data-ttu-id="0ee4e-104">将 SDDL 字符串转换为自定义对象。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-104">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="0ee4e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0ee4e-105">SYNTAX</span></span>

### <span data-ttu-id="0ee4e-106">全部</span><span class="sxs-lookup"><span data-stu-id="0ee4e-106">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="0ee4e-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0ee4e-107">DESCRIPTION</span></span>

<span data-ttu-id="0ee4e-108">`ConvertFrom-SddlString`Cmdlet 可将安全描述符定义语言字符串转换为具有以下属性的自定义 **PSCustomObject** 对象： Owner、Group、descriptor.discretionaryacl、SystemAcl 和 RawDescriptor。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-108">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="0ee4e-109">所有者、组、Descriptor.discretionaryacl 和 SystemAcl 属性包含 SDDL 字符串中指定的访问权限的可读文本表示形式。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-109">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="0ee4e-110">此 cmdlet 是在 PowerShell 5.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-110">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="0ee4e-111">示例</span><span class="sxs-lookup"><span data-stu-id="0ee4e-111">EXAMPLES</span></span>

### <span data-ttu-id="0ee4e-112">示例1：将文件系统访问权限 SDDL 转换为 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0ee4e-112">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="0ee4e-113">第一个命令使用 `Get-Acl` cmdlet 来获取 C：\Windows 文件夹的安全描述符，并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-113">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="0ee4e-114">第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-114">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="0ee4e-115">示例2：将注册表访问权限 SDDL 转换为 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0ee4e-115">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="0ee4e-116">第一个命令使用 `Get-Acl` cmdlet 来获取 HKLM： \ SOFTWARE\Microsoft\ 密钥的安全描述符，并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-116">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="0ee4e-117">第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-117">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="0ee4e-118">它使用 `-Type` 参数来指定 SDDL 字符串表示注册表安全描述符。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-118">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="0ee4e-119">示例3：使用带有和不带参数的 ConvertFrom-SddlString 将注册表访问权限 SDDL 转换为 PSCustomObject `-Type`</span><span class="sxs-lookup"><span data-stu-id="0ee4e-119">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="0ee4e-120">第一个命令使用 `Get-Acl` cmdlet 来获取 HKLM： \ SOFTWARE\Microsoft\ 密钥的安全描述符，并将其保存在变量中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="0ee4e-121">第二个命令使用 `ConvertFrom-SddlString` cmdlet 来获取 sddl 字符串的文本表示形式，该对象包含在表示安全描述符的对象的 "sddl" 属性中。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-121">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="0ee4e-122">它不使用 `-Type` 参数，因此显示的访问权限用于文件系统。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-122">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="0ee4e-123">第三个命令将 `ConvertFrom-SddlString` cmdlet 与参数一起使用 `-Type` ，以使返回的访问权限用于注册表。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-123">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="0ee4e-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0ee4e-124">PARAMETERS</span></span>

### <span data-ttu-id="0ee4e-125">-Sddl</span><span class="sxs-lookup"><span data-stu-id="0ee4e-125">-Sddl</span></span>

<span data-ttu-id="0ee4e-126">指定表示安全描述符的字符串（SDDL 语法）。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-126">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0ee4e-127">-Type</span><span class="sxs-lookup"><span data-stu-id="0ee4e-127">-Type</span></span>

<span data-ttu-id="0ee4e-128">指定 SDDL 字符串表示的权限类型。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-128">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="0ee4e-129">此参数的可接受值为：</span><span class="sxs-lookup"><span data-stu-id="0ee4e-129">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0ee4e-130">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-130">FileSystemRights</span></span>
- <span data-ttu-id="0ee4e-131">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-131">RegistryRights</span></span>
- <span data-ttu-id="0ee4e-132">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-132">ActiveDirectoryRights</span></span>
- <span data-ttu-id="0ee4e-133">MutexRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-133">MutexRights</span></span>
- <span data-ttu-id="0ee4e-134">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-134">SemaphoreRights</span></span>
- <span data-ttu-id="0ee4e-135">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-135">CryptoKeyRights</span></span>
- <span data-ttu-id="0ee4e-136">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="0ee4e-136">EventWaitHandleRights</span></span>

<span data-ttu-id="0ee4e-137">默认情况下，cmdlet 使用文件系统权限。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-137">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="0ee4e-138">CryptoKeyRights 和 ActiveDirectoryRights 在 PowerShell Core 中不受支持。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-138">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0ee4e-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0ee4e-139">CommonParameters</span></span>

<span data-ttu-id="0ee4e-140">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0ee4e-141">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0ee4e-142">输入</span><span class="sxs-lookup"><span data-stu-id="0ee4e-142">INPUTS</span></span>

### <span data-ttu-id="0ee4e-143">System.String</span><span class="sxs-lookup"><span data-stu-id="0ee4e-143">System.String</span></span>

<span data-ttu-id="0ee4e-144">可以通过管道将 SDDL 字符串传递给 `ConvertFrom-SddlString` 。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-144">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="0ee4e-145">输出</span><span class="sxs-lookup"><span data-stu-id="0ee4e-145">OUTPUTS</span></span>

## <span data-ttu-id="0ee4e-146">注释</span><span class="sxs-lookup"><span data-stu-id="0ee4e-146">NOTES</span></span>

<span data-ttu-id="0ee4e-147">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="0ee4e-147">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="0ee4e-148">相关链接</span><span class="sxs-lookup"><span data-stu-id="0ee4e-148">RELATED LINKS</span></span>

[<span data-ttu-id="0ee4e-149">安全描述符定义语言</span><span class="sxs-lookup"><span data-stu-id="0ee4e-149">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)
