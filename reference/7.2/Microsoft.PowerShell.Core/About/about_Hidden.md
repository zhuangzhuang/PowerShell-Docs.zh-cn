---
description: 介绍 Hidden 关键字，该关键字隐藏默认 Get-Member 结果中的类成员。
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 8340a955b7cfa540baccde0da233d6d9cf0c5552
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597034"
---
# <a name="about_hidden"></a><span data-ttu-id="183bc-103">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="183bc-103">about_Hidden</span></span>

## <a name="short-description"></a><span data-ttu-id="183bc-104">简短说明</span><span class="sxs-lookup"><span data-stu-id="183bc-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="183bc-105">介绍 Hidden 关键字，该关键字隐藏默认 Get-Member 结果中的类成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-105">Describes the Hidden keyword, which hides class members from default Get-Member results.</span></span>

## <a name="long-description"></a><span data-ttu-id="183bc-106">详细说明</span><span class="sxs-lookup"><span data-stu-id="183bc-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="183bc-107">如果在脚本中使用 Hidden 关键字，则默认情况下将隐藏类的成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-107">When you use the Hidden keyword in a script, you hide the members of a class by default.</span></span> <span data-ttu-id="183bc-108">Hidden 关键字可以隐藏属性、方法 (包括构造函数、事件、别名属性和其他成员类型，包括静态成员、从 Get-Member cmdlet 的默认结果和 IntelliSense 和 tab 键完成结果。</span><span class="sxs-lookup"><span data-stu-id="183bc-108">The Hidden keyword can hide properties, methods (including constructors, events, alias properties, and other member types, including static members, from the default results of the Get-Member cmdlet, and from IntelliSense and tab completion results.</span></span> <span data-ttu-id="183bc-109">若要显示使用 Hidden 关键字隐藏的成员，请将-Force 参数添加到 Get-Member 命令。</span><span class="sxs-lookup"><span data-stu-id="183bc-109">To display members that you have hidden with the Hidden keyword, add the -Force parameter to a Get-Member command.</span></span>

<span data-ttu-id="183bc-110">除非完成发生在定义隐藏成员的类中，否则不会使用 tab 自动补全或 IntelliSense 显示隐藏成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-110">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="183bc-111">已添加新的属性 System.management.automation.hiddenattribute，以便 C \# 代码在 PowerShell 中具有相同的语义。</span><span class="sxs-lookup"><span data-stu-id="183bc-111">A new attribute, System.Management.Automation.HiddenAttribute, has been added, so that C\# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="183bc-112">Hidden 关键字适用于创建类中的属性和方法，你不一定要让类的其他用户查看这些属性和方法，或者随时可以编辑。</span><span class="sxs-lookup"><span data-stu-id="183bc-112">The Hidden keyword is useful for creating properties and methods within a class that you do not necessarily want other users of the class to see, or readily be able to edit.</span></span>

<span data-ttu-id="183bc-113">Hidden 关键字不会影响如何查看或更改类的成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-113">The Hidden keyword has no effect on how you can view or make changes to members of a class.</span></span> <span data-ttu-id="183bc-114">与 PowerShell 中的所有语言关键字一样，隐藏不区分大小写，隐藏成员仍是公共的。</span><span class="sxs-lookup"><span data-stu-id="183bc-114">Like all language keywords in PowerShell, Hidden is not case-sensitive, and hidden members are still public.</span></span>

<span data-ttu-id="183bc-115">PowerShell 5.0 中引入了隐藏的和自定义类。</span><span class="sxs-lookup"><span data-stu-id="183bc-115">Hidden, along with custom classes, was introduced in PowerShell 5.0.</span></span>

## <a name="example"></a><span data-ttu-id="183bc-116">示例</span><span class="sxs-lookup"><span data-stu-id="183bc-116">EXAMPLE</span></span>

<span data-ttu-id="183bc-117">下面的示例演示如何在类定义中使用 Hidden 关键字。</span><span class="sxs-lookup"><span data-stu-id="183bc-117">The following example shows how to use the Hidden keyword in a class definition.</span></span> <span data-ttu-id="183bc-118">Car 类方法的驱动器具有不需要查看或更改 (的属性，它只计算在 Car 类上调用驱动器的次数，这对于类的用户来说并不重要;例如，请考虑在购买汽车时，不会要求卖方使用汽车的驱动器数量。</span><span class="sxs-lookup"><span data-stu-id="183bc-118">The Car class method, Drive, has a property, rides, that does not need to be viewed or changed (it merely tallies the number of times that Drive is called on the Car class, a metric that is not important to users of the class; consider, for example, that when you are buying a car, you do not ask the seller on how many drives the car has been taken.</span></span>

<span data-ttu-id="183bc-119">由于类的用户很少需要更改此属性，因此可以通过使用 Hidden 关键字，隐藏 Get-Member 和自动完成结果中的属性。</span><span class="sxs-lookup"><span data-stu-id="183bc-119">Because there is little need for users of the class to change this property, we can hide the property from Get-Member and automatic completion results by using the Hidden keyword.</span></span>

<span data-ttu-id="183bc-120">通过在属性及其数据类型所在的语句行上输入 Hidden 关键字，添加该关键字。</span><span class="sxs-lookup"><span data-stu-id="183bc-120">Add the Hidden keyword by entering it on the same statement line as the property and its data type.</span></span> <span data-ttu-id="183bc-121">尽管关键字可以在此行上按任意顺序进行，但使用 Hidden 关键字启动语句后，以后就可以更轻松地识别所有隐藏的成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-121">Although the keyword can be in any order on this line, starting the statement with the Hidden keyword makes it easier for you later to identify all members that you have hidden.</span></span>

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

<span data-ttu-id="183bc-122">现在，创建车载类的新实例，并将其保存在变量 \$ TestCar 中。</span><span class="sxs-lookup"><span data-stu-id="183bc-122">Now, create a new instance of the Car class, and save it in a variable, \$TestCar.</span></span>

```powershell
$TestCar = [Car]::new()
```

<span data-ttu-id="183bc-123">创建新的实例后，通过管道将 $TestCar 变量的内容传递给 Get 成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-123">After you create the new instance, pipe the contents of the $TestCar variable to Get-Member.</span></span> <span data-ttu-id="183bc-124">请注意，搭乘属性不在 Get-Member 命令结果中列出的成员中。</span><span class="sxs-lookup"><span data-stu-id="183bc-124">Observe that the rides property is not among the members listed in the Get-Member command results.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

<span data-ttu-id="183bc-125">现在，请尝试再次运行 Get-Member，但这次请添加-Force 参数。</span><span class="sxs-lookup"><span data-stu-id="183bc-125">Now, try running Get-Member again, but this time, add the -Force parameter.</span></span>
<span data-ttu-id="183bc-126">请注意，结果包含隐藏的搭乘属性以及默认情况下隐藏的其他成员。</span><span class="sxs-lookup"><span data-stu-id="183bc-126">Note that the results contain the hidden rides property, among other members that are hidden by default.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a><span data-ttu-id="183bc-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="183bc-127">SEE ALSO</span></span>

[<span data-ttu-id="183bc-128">about_Classes</span><span class="sxs-lookup"><span data-stu-id="183bc-128">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="183bc-129">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="183bc-129">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="183bc-130">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="183bc-130">about_Wildcards</span></span>](about_Wildcards.md)

[<span data-ttu-id="183bc-131">Get-Member</span><span class="sxs-lookup"><span data-stu-id="183bc-131">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

