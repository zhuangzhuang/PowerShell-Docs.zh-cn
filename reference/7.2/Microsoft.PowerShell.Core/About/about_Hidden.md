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
# <a name="about_hidden"></a>about_Hidden

## <a name="short-description"></a>简短说明
介绍 Hidden 关键字，该关键字隐藏默认 Get-Member 结果中的类成员。

## <a name="long-description"></a>详细说明

如果在脚本中使用 Hidden 关键字，则默认情况下将隐藏类的成员。 Hidden 关键字可以隐藏属性、方法 (包括构造函数、事件、别名属性和其他成员类型，包括静态成员、从 Get-Member cmdlet 的默认结果和 IntelliSense 和 tab 键完成结果。 若要显示使用 Hidden 关键字隐藏的成员，请将-Force 参数添加到 Get-Member 命令。

除非完成发生在定义隐藏成员的类中，否则不会使用 tab 自动补全或 IntelliSense 显示隐藏成员。

已添加新的属性 System.management.automation.hiddenattribute，以便 C \# 代码在 PowerShell 中具有相同的语义。

Hidden 关键字适用于创建类中的属性和方法，你不一定要让类的其他用户查看这些属性和方法，或者随时可以编辑。

Hidden 关键字不会影响如何查看或更改类的成员。 与 PowerShell 中的所有语言关键字一样，隐藏不区分大小写，隐藏成员仍是公共的。

PowerShell 5.0 中引入了隐藏的和自定义类。

## <a name="example"></a>示例

下面的示例演示如何在类定义中使用 Hidden 关键字。 Car 类方法的驱动器具有不需要查看或更改 (的属性，它只计算在 Car 类上调用驱动器的次数，这对于类的用户来说并不重要;例如，请考虑在购买汽车时，不会要求卖方使用汽车的驱动器数量。

由于类的用户很少需要更改此属性，因此可以通过使用 Hidden 关键字，隐藏 Get-Member 和自动完成结果中的属性。

通过在属性及其数据类型所在的语句行上输入 Hidden 关键字，添加该关键字。 尽管关键字可以在此行上按任意顺序进行，但使用 Hidden 关键字启动语句后，以后就可以更轻松地识别所有隐藏的成员。

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

现在，创建车载类的新实例，并将其保存在变量 \$ TestCar 中。

```powershell
$TestCar = [Car]::new()
```

创建新的实例后，通过管道将 $TestCar 变量的内容传递给 Get 成员。 请注意，搭乘属性不在 Get-Member 命令结果中列出的成员中。

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

现在，请尝试再次运行 Get-Member，但这次请添加-Force 参数。
请注意，结果包含隐藏的搭乘属性以及默认情况下隐藏的其他成员。

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

## <a name="see-also"></a>另请参阅

[about_Classes](about_Classes.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_Wildcards](about_Wildcards.md)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

