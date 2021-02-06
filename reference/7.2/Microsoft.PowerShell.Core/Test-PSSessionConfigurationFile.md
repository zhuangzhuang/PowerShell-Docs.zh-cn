---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: c6d6d305b283522215d43b7339683b1617a85804
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596036"
---
# <span data-ttu-id="0bd5b-102">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0bd5b-102">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="0bd5b-103">摘要</span><span class="sxs-lookup"><span data-stu-id="0bd5b-103">SYNOPSIS</span></span>
<span data-ttu-id="0bd5b-104">验证会话配置文件中的键和值。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-104">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="0bd5b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0bd5b-105">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="0bd5b-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0bd5b-106">DESCRIPTION</span></span>

<span data-ttu-id="0bd5b-107">此 cmdlet 验证会话配置文件是否包含有效的密钥，以及这些值是否为正确的类型。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-107">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="0bd5b-108">对于枚举值，该 cmdlet 将验证指定的值是否有效。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-108">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="0bd5b-109">`$True`如果文件通过了所有测试，则该 cmdlet 将返回， `$False` 否则返回。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-109">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="0bd5b-110">若要查找任何错误，请使用 **Verbose** 参数。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-110">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="0bd5b-111">`Test-PSSessionConfigurationFile` 验证会话配置文件，如由 cmdlet 创建的文件 `New-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-111">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="0bd5b-112">有关会话配置的详细信息，请参阅 [about_Session_Configurations](About/about_Session_Configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-112">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="0bd5b-113">有关会话配置文件的信息，请参阅 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-113">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="0bd5b-114">此 cmdlet 是在 PowerShell 3.0 中引入的。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="0bd5b-115">示例</span><span class="sxs-lookup"><span data-stu-id="0bd5b-115">EXAMPLES</span></span>

### <span data-ttu-id="0bd5b-116">示例1：测试会话配置文件</span><span class="sxs-lookup"><span data-stu-id="0bd5b-116">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="0bd5b-117">示例2：测试会话配置的会话配置文件</span><span class="sxs-lookup"><span data-stu-id="0bd5b-117">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="0bd5b-118">在此示例中，我们将测试 **受限** 会话配置中使用的配置文件。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-118">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="0bd5b-119">**Path** 参数的值是 `Get-PSSessionConfiguration` 用于获取 **受限** 会话配置的命令的结果。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-119">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="0bd5b-120">会话配置文件的路径存储在会话配置的 **ConfigFilePath** 属性的值中。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-120">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="0bd5b-121">示例3：测试所有会话配置文件</span><span class="sxs-lookup"><span data-stu-id="0bd5b-121">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="0bd5b-122">此示例中的函数测试本地计算机上的所有会话配置文件。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-122">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="0bd5b-123">函数使用 `Get-PSSessionConfiguration` cmdlet 获取所有会话配置。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-123">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="0bd5b-124">循环内的代码 `ForEach-Object` 显示文件路径并测试每个会话配置。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-124">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="0bd5b-125">会话配置的 **ConfigFilePath** 属性包含在会话配置中使用的会话配置文件的路径（如果有）。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-125">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="0bd5b-126">如果填充了 **ConfigFilePath** 属性的值（该值为 true），则该命令将获取（打印）**ConfigFilePath** 属性值。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-126">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="0bd5b-127">然后，它使用 `Test-PSSessionConfigurationFile` cmdlet 来测试 **ConfigFilePath** 值中的文件。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-127">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="0bd5b-128">当文件无法通过测试时，**Verbose** 参数将返回文件错误。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-128">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="0bd5b-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0bd5b-129">PARAMETERS</span></span>

### <span data-ttu-id="0bd5b-130">-Path</span><span class="sxs-lookup"><span data-stu-id="0bd5b-130">-Path</span></span>

<span data-ttu-id="0bd5b-131">指定会话配置文件的路径和文件名 ( .pssc) 。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-131">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="0bd5b-132">如果省略该路径，则默认为当前文件夹。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-132">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="0bd5b-133">支持通配符，但它们必须解析为单个文件。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-133">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="0bd5b-134">还可以通过管道将会话配置文件路径传递给 `Test-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-134">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0bd5b-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0bd5b-135">CommonParameters</span></span>

<span data-ttu-id="0bd5b-136">此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0bd5b-137">有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0bd5b-138">输入</span><span class="sxs-lookup"><span data-stu-id="0bd5b-138">INPUTS</span></span>

### <span data-ttu-id="0bd5b-139">System.String</span><span class="sxs-lookup"><span data-stu-id="0bd5b-139">System.String</span></span>

<span data-ttu-id="0bd5b-140">你可以通过管道将会话配置文件路径传递给 `Test-PSSessionConfigurationFile` 。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-140">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="0bd5b-141">输出</span><span class="sxs-lookup"><span data-stu-id="0bd5b-141">OUTPUTS</span></span>

### <span data-ttu-id="0bd5b-142">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="0bd5b-142">System.Boolean</span></span>

## <span data-ttu-id="0bd5b-143">注释</span><span class="sxs-lookup"><span data-stu-id="0bd5b-143">NOTES</span></span>

<span data-ttu-id="0bd5b-144">此 cmdlet 仅在 Windows 平台上可用。</span><span class="sxs-lookup"><span data-stu-id="0bd5b-144">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="0bd5b-145">相关链接</span><span class="sxs-lookup"><span data-stu-id="0bd5b-145">RELATED LINKS</span></span>

[<span data-ttu-id="0bd5b-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-147">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0bd5b-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="0bd5b-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="0bd5b-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="0bd5b-151">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="0bd5b-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="0bd5b-154">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0bd5b-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="0bd5b-155">WSMan 提供程序</span><span class="sxs-lookup"><span data-stu-id="0bd5b-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="0bd5b-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="0bd5b-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="0bd5b-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="0bd5b-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
