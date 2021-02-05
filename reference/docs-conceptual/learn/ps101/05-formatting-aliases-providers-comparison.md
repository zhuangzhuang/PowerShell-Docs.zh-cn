---
title: 格式设置, 别名, 提供程序, 比较
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: 本章介绍输出格式设置、命令别名、提供程序和比较操作的概念。
ms.openlocfilehash: 5573ca58601af0c6af15736b772a9792d8d77a79
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2021
ms.locfileid: "99596004"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="22605-103">第 5 章 - 格式设置、别名、提供程序、比较</span><span class="sxs-lookup"><span data-stu-id="22605-103">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="22605-104">要求</span><span class="sxs-lookup"><span data-stu-id="22605-104">Requirements</span></span>

<span data-ttu-id="22605-105">本章所述的某些示例需要 SQL Server PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="22605-105">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="22605-106">此模块作为 [SQL Server Management Studio (SMSS)][SMSS] 的一部分安装。</span><span class="sxs-lookup"><span data-stu-id="22605-106">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="22605-107">后续章节也会使用此模块。</span><span class="sxs-lookup"><span data-stu-id="22605-107">It's also used in subsequent chapters.</span></span> <span data-ttu-id="22605-108">将它下载并安装在 Windows 10 实验室环境计算机上。</span><span class="sxs-lookup"><span data-stu-id="22605-108">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="22605-109">右对齐格式</span><span class="sxs-lookup"><span data-stu-id="22605-109">Format Right</span></span>

<span data-ttu-id="22605-110">在第 4 章中，你已了解如何尽可能靠左侧进行筛选。</span><span class="sxs-lookup"><span data-stu-id="22605-110">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="22605-111">手动设置命令输出的格式的规则类似于该规则，不同之处在于它需要尽可能出现在右侧。</span><span class="sxs-lookup"><span data-stu-id="22605-111">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="22605-112">最常见的格式命令是 `Format-Table` 和 `Format-List`。</span><span class="sxs-lookup"><span data-stu-id="22605-112">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="22605-113">还可以使用 `Format-Wide` 和 `Format-Custom`，但不太常见。</span><span class="sxs-lookup"><span data-stu-id="22605-113">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="22605-114">如第 3 章所述，除非使用自定义格式设置，否则返回超过四个属性的命令默认为列表。</span><span class="sxs-lookup"><span data-stu-id="22605-114">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="22605-115">使用 `Format-Table` cmdlet 手动替代格式设置，并在表中而不是在列表中显示输出。</span><span class="sxs-lookup"><span data-stu-id="22605-115">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="22605-116">`Get-Service` 的默认输出是表中的三个属性。</span><span class="sxs-lookup"><span data-stu-id="22605-116">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="22605-117">使用 `Format-List` cmdlet 替代默认格式设置，并在列表中返回结果。</span><span class="sxs-lookup"><span data-stu-id="22605-117">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="22605-118">请注意，仅通过管道将 `Get-Service` 传送到 `Format-List` 会使其返回其他属性。</span><span class="sxs-lookup"><span data-stu-id="22605-118">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="22605-119">并非每个命令都会出现这种情况，因为特定命令的格式是在后台设置的。</span><span class="sxs-lookup"><span data-stu-id="22605-119">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="22605-120">使用 cmdlet 格式时，首先需要注意的是，它们生成的格式对象与 PowerShell 中的普通对象不同。</span><span class="sxs-lookup"><span data-stu-id="22605-120">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="22605-121">这意味着无法通过管道将格式命令传送给大多数其他命令。</span><span class="sxs-lookup"><span data-stu-id="22605-121">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="22605-122">可以将格式命令通过管道传送给一些 `Out-*` 命令，但仅此而已。</span><span class="sxs-lookup"><span data-stu-id="22605-122">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="22605-123">因此，建议在行尾执行任何格式设置（右对齐格式）。</span><span class="sxs-lookup"><span data-stu-id="22605-123">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="22605-124">别名</span><span class="sxs-lookup"><span data-stu-id="22605-124">Aliases</span></span>

<span data-ttu-id="22605-125">PowerShell 的别名是命令的较短名称。</span><span class="sxs-lookup"><span data-stu-id="22605-125">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="22605-126">PowerShell 包含一组内置别名，你也可以定义自己的别名。</span><span class="sxs-lookup"><span data-stu-id="22605-126">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="22605-127">`Get-Alias` cmdlet 用于查找别名。</span><span class="sxs-lookup"><span data-stu-id="22605-127">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="22605-128">如果你已知道命令的别名，则 Name 参数用于确定与该别名关联的命令。</span><span class="sxs-lookup"><span data-stu-id="22605-128">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="22605-129">可以为 Name 参数的值指定多个别名。</span><span class="sxs-lookup"><span data-stu-id="22605-129">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="22605-130">你会经常看到 Name 参数被忽略，因为它是位置参数。</span><span class="sxs-lookup"><span data-stu-id="22605-130">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="22605-131">如果要查找命令的别名，需要使用 Definition 参数。</span><span class="sxs-lookup"><span data-stu-id="22605-131">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="22605-132">不能按位置使用 Definition 参数，因此必须指定它。</span><span class="sxs-lookup"><span data-stu-id="22605-132">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="22605-133">使用别名可以减少按键次数，并且在将命令输入到控制台时也可行。</span><span class="sxs-lookup"><span data-stu-id="22605-133">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="22605-134">它们不应在脚本或任何要保存或与他人共享的代码中使用。</span><span class="sxs-lookup"><span data-stu-id="22605-134">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="22605-135">如本书前面所述，使用完整的 cmdlet 和参数名称是自文档化，并且更易于理解。</span><span class="sxs-lookup"><span data-stu-id="22605-135">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="22605-136">创建自己的别名时要小心，因为它们将仅存在于计算机上的当前 PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="22605-136">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="22605-137">提供程序</span><span class="sxs-lookup"><span data-stu-id="22605-137">Providers</span></span>

<span data-ttu-id="22605-138">PowerShell 中的提供程序是一种允许文件系统访问数据存储的接口。</span><span class="sxs-lookup"><span data-stu-id="22605-138">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="22605-139">PowerShell 中提供了许多内置提供程序。</span><span class="sxs-lookup"><span data-stu-id="22605-139">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="22605-140">如上面的结果所示，存在用于注册表、别名、环境变量、文件系统、函数、变量、证书和 WSMan 的内置提供程序。</span><span class="sxs-lookup"><span data-stu-id="22605-140">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="22605-141">这些提供程序用于公开其数据存储的实际驱动器可使用 `Get-PSDrive` cmdlet 确定。</span><span class="sxs-lookup"><span data-stu-id="22605-141">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="22605-142">`Get-PSDrive` cmdlet 不仅显示由提供程序公开的驱动器，而且还显示 Windows 逻辑驱动器，其中包括映射到网络共享的驱动器。</span><span class="sxs-lookup"><span data-stu-id="22605-142">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="22605-143">第三方模块（例如 Active Directory PowerShell 模块和 SQL Server PowerShell 模块）都添加了自己的 PowerShell 提供程序和 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="22605-143">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="22605-144">导入 Active Directory 和 SQL Server PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="22605-144">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="22605-145">检查以确定是否添加了任何其他 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="22605-145">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="22605-146">请注意，在前面的结果集中，现在存在两个新的 PowerShell 提供程序，一个用于 Active Directory，另一个用于 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="22605-146">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="22605-147">此外，还为每个模块添加了一个 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="22605-147">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="22605-148">可以像访问传统文件系统一样访问 PSDrive。</span><span class="sxs-lookup"><span data-stu-id="22605-148">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="22605-149">比较运算符</span><span class="sxs-lookup"><span data-stu-id="22605-149">Comparison Operators</span></span>

<span data-ttu-id="22605-150">PowerShell 包含许多比较运算符，用于比较值或查找与特定模式匹配的值。</span><span class="sxs-lookup"><span data-stu-id="22605-150">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="22605-151">表 5-1 包含 PowerShell 中的比较运算符的列表。</span><span class="sxs-lookup"><span data-stu-id="22605-151">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="22605-152">操作员</span><span class="sxs-lookup"><span data-stu-id="22605-152">Operator</span></span>    |                          <span data-ttu-id="22605-153">定义</span><span class="sxs-lookup"><span data-stu-id="22605-153">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="22605-154">等于</span><span class="sxs-lookup"><span data-stu-id="22605-154">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="22605-155">不等于</span><span class="sxs-lookup"><span data-stu-id="22605-155">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="22605-156">大于</span><span class="sxs-lookup"><span data-stu-id="22605-156">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="22605-157">大于或等于</span><span class="sxs-lookup"><span data-stu-id="22605-157">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="22605-158">小于</span><span class="sxs-lookup"><span data-stu-id="22605-158">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="22605-159">小于或等于</span><span class="sxs-lookup"><span data-stu-id="22605-159">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="22605-160">使用 `*` 通配符进行匹配</span><span class="sxs-lookup"><span data-stu-id="22605-160">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="22605-161">不使用 `*` 通配符进行匹配</span><span class="sxs-lookup"><span data-stu-id="22605-161">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="22605-162">匹配指定的正则表达式</span><span class="sxs-lookup"><span data-stu-id="22605-162">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="22605-163">不匹配指定的正则表达式</span><span class="sxs-lookup"><span data-stu-id="22605-163">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="22605-164">确定集合中是否包含指定的值</span><span class="sxs-lookup"><span data-stu-id="22605-164">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="22605-165">确定集合是否不包含特定值</span><span class="sxs-lookup"><span data-stu-id="22605-165">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="22605-166">确定指定的值是否在集合中</span><span class="sxs-lookup"><span data-stu-id="22605-166">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="22605-167">确定指定的值是否不在集合中</span><span class="sxs-lookup"><span data-stu-id="22605-167">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="22605-168">替换指定的值</span><span class="sxs-lookup"><span data-stu-id="22605-168">Replaces the specified value</span></span>                                 |

<span data-ttu-id="22605-169">表 5-1 中列出的所有运算符都不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="22605-169">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="22605-170">将 `c` 放置在表 5-1 中列出的运算符之前，使其区分大小写。</span><span class="sxs-lookup"><span data-stu-id="22605-170">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="22605-171">例如，`-ceq` 是区分大小写的 `-eq` 比较运算符。</span><span class="sxs-lookup"><span data-stu-id="22605-171">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="22605-172">首字母大写的“PowerShell”等效于使用等于比较运算符的小写的“powershell”。</span><span class="sxs-lookup"><span data-stu-id="22605-172">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="22605-173">使用区分大小写的等于比较运算符时，不等效。</span><span class="sxs-lookup"><span data-stu-id="22605-173">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="22605-174">不等于比较运算符反转条件。</span><span class="sxs-lookup"><span data-stu-id="22605-174">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="22605-175">大于、大于或等于、小于和小于或等于均可用于字符串或数值。</span><span class="sxs-lookup"><span data-stu-id="22605-175">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="22605-176">在上一个示例中，使用大于或等于而不是大于，会返回布尔值 true，因为 5 等于 5。</span><span class="sxs-lookup"><span data-stu-id="22605-176">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="22605-177">根据上述两个示例中的结果，你可能会猜到使用小于和小于或等于的情况。</span><span class="sxs-lookup"><span data-stu-id="22605-177">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="22605-178">即使对于经验丰富的 PowerShell 用户，`-Like` 和 `-Match` 运算符也可能会造成混淆。</span><span class="sxs-lookup"><span data-stu-id="22605-178">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="22605-179">`-Like` 与通配符 `*` 和 `?` 结合使用，以执行“like”匹配。</span><span class="sxs-lookup"><span data-stu-id="22605-179">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="22605-180">`-Match` 使用正则表达式执行匹配。</span><span class="sxs-lookup"><span data-stu-id="22605-180">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="22605-181">使用范围运算符将数字 1 到 10 存储在变量中。</span><span class="sxs-lookup"><span data-stu-id="22605-181">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="22605-182">确定 `$Numbers` 变量是否包含 15。</span><span class="sxs-lookup"><span data-stu-id="22605-182">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="22605-183">确定它是否包含数字 10。</span><span class="sxs-lookup"><span data-stu-id="22605-183">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="22605-184">`-NotContains` 反转逻辑，以查看 `$Numbers` 变量是否不包含值。</span><span class="sxs-lookup"><span data-stu-id="22605-184">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="22605-185">前面的示例返回布尔值 true，因为 `$Numbers` 变量不包含 15。</span><span class="sxs-lookup"><span data-stu-id="22605-185">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="22605-186">但它包含数字 10，因此在进行测试时，结果为 false。</span><span class="sxs-lookup"><span data-stu-id="22605-186">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="22605-187">PowerShell 版本 3.0 首次引入了“in”比较运算符。</span><span class="sxs-lookup"><span data-stu-id="22605-187">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="22605-188">它用于确定某个值是否“位于”数组中。</span><span class="sxs-lookup"><span data-stu-id="22605-188">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="22605-189">`$Numbers` 变量是数组，因为它包含多个值。</span><span class="sxs-lookup"><span data-stu-id="22605-189">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="22605-190">换言之，`-in` 执行与 contains 比较运算符相同的测试，不过方向相反。</span><span class="sxs-lookup"><span data-stu-id="22605-190">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="22605-191">15 不在 `$Numbers` 数组中，因此在下面的示例中返回 false。</span><span class="sxs-lookup"><span data-stu-id="22605-191">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="22605-192">与 `-contains` 运算符一样，`not` 反转 `-in` 运算符的逻辑。</span><span class="sxs-lookup"><span data-stu-id="22605-192">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="22605-193">上面的示例返回 false，因为 `$Numbers` 数组包含 10，并且条件进行了测试以确定它是否不包含 10。</span><span class="sxs-lookup"><span data-stu-id="22605-193">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="22605-194">15“不位于”`$Numbers` 数组中，因此它返回布尔值 true。</span><span class="sxs-lookup"><span data-stu-id="22605-194">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="22605-195">`-replace` 运算符所执行的操作和你想象的一样。</span><span class="sxs-lookup"><span data-stu-id="22605-195">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="22605-196">它用于替换内容。</span><span class="sxs-lookup"><span data-stu-id="22605-196">It's used to replace something.</span></span> <span data-ttu-id="22605-197">如果指定一个值，则会将该值替换为空值。</span><span class="sxs-lookup"><span data-stu-id="22605-197">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="22605-198">在下面的示例中，我将“Shell”替换为空值。</span><span class="sxs-lookup"><span data-stu-id="22605-198">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="22605-199">如果要将值替换为其他值，请在要替换的模式之后指定新值。</span><span class="sxs-lookup"><span data-stu-id="22605-199">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="22605-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span><span class="sxs-lookup"><span data-stu-id="22605-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="22605-201">在下面的示例中，我将“Saturday”这个词替换为缩写“Sat”。</span><span class="sxs-lookup"><span data-stu-id="22605-201">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="22605-202">还有一些可用于替换内容的方法（如 Replace()），其工作原理类似于替换运算符。</span><span class="sxs-lookup"><span data-stu-id="22605-202">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="22605-203">但是，默认情况下，`-Replace` 运算符不区分大小写，而 Replace() 方法区分大小写。</span><span class="sxs-lookup"><span data-stu-id="22605-203">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="22605-204">请注意，上述示例中未替换“Saturday”一词。</span><span class="sxs-lookup"><span data-stu-id="22605-204">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="22605-205">这是因为所指定的大小写格式与原始格式不同。</span><span class="sxs-lookup"><span data-stu-id="22605-205">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="22605-206">当指定的“Saturday”的大小写格式与原始格式相同时，Replace() 方法会按预期替换它。</span><span class="sxs-lookup"><span data-stu-id="22605-206">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="22605-207">使用方法转换数据时要小心，因为可能会遇到无法预料的问题，例如 Turkey Test 失败。</span><span class="sxs-lookup"><span data-stu-id="22605-207">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="22605-208">有关示例，请参阅标题为[使用 Pester 测试具有其他区域性的 PowerShell 代码][]的博客文章。</span><span class="sxs-lookup"><span data-stu-id="22605-208">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="22605-209">我建议尽量使用运算符而不是方法，以避免这些类型的问题。</span><span class="sxs-lookup"><span data-stu-id="22605-209">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="22605-210">尽管可以像前面的示例中所示使用比较运算符，但我通常将它们与 `Where-Object` cmdlet 一起使用来执行某种类型的筛选。</span><span class="sxs-lookup"><span data-stu-id="22605-210">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="22605-211">总结</span><span class="sxs-lookup"><span data-stu-id="22605-211">Summary</span></span>

<span data-ttu-id="22605-212">在本章中，你已了解了多个不同的主题，其中包含右对齐格式设置、别名、提供程序和比较运算符。</span><span class="sxs-lookup"><span data-stu-id="22605-212">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="22605-213">审阅</span><span class="sxs-lookup"><span data-stu-id="22605-213">Review</span></span>

1. <span data-ttu-id="22605-214">为什么有必要尽可能靠右侧执行格式设置？</span><span class="sxs-lookup"><span data-stu-id="22605-214">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="22605-215">如何确定 `%` 别名的实际 cmdlet 是什么？</span><span class="sxs-lookup"><span data-stu-id="22605-215">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="22605-216">为什么不应在保存的脚本或与其他人共享的代码中使用别名？</span><span class="sxs-lookup"><span data-stu-id="22605-216">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="22605-217">在与其中某个注册表提供程序相关联的驱动器上执行目录列表。</span><span class="sxs-lookup"><span data-stu-id="22605-217">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="22605-218">使用替换运算符而不是替换方法的其中一个主要好处是什么？</span><span class="sxs-lookup"><span data-stu-id="22605-218">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="22605-219">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="22605-219">Recommended Reading</span></span>

- <span data-ttu-id="22605-220">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="22605-220">[Format-Table][]</span></span>
- <span data-ttu-id="22605-221">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="22605-221">[Format-List][]</span></span>
- <span data-ttu-id="22605-222">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="22605-222">[Format-Wide][]</span></span>
- <span data-ttu-id="22605-223">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="22605-223">[about_Aliases][]</span></span>
- <span data-ttu-id="22605-224">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="22605-224">[about_Providers][]</span></span>
- <span data-ttu-id="22605-225">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="22605-225">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="22605-226">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="22605-226">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[使用 Pester 测试具有其他区域性的 PowerShell 代码]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
