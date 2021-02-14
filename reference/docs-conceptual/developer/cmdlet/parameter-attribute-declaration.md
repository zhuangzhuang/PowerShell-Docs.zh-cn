---
ms.date: 09/13/2016
ms.topic: reference
title: 参数属性声明
description: 参数属性声明
ms.openlocfilehash: 24a49406b1493a7f8c23bca798ddb3e73a901111
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500223"
---
# <a name="parameter-attribute-declaration"></a>参数属性声明

参数属性将 cmdlet 类的公共属性标识为 cmdlet 参数。

## <a name="syntax"></a>语法

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>parameters

`Mandatory` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数是必需的。 如果在调用 cmdlet 时未提供所需的参数，则 Windows PowerShell 会提示用户输入参数值。 默认值为 `false`。

`ParameterSetName` ([system.string](/dotnet/api/System.String)) 可选的命名参数。 指定此 cmdlet 参数所属的参数集。 如果未指定参数集，则参数属于所有参数集。

`Position` ([system.object](/dotnet/api/System.Int32)) 可选的命名参数。 指定参数在 Windows PowerShell 命令中的位置。

`ValueFromPipeline` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数从管道对象获取其值。 如果 cmdlet 访问完整对象，而不仅仅是对象的属性，请指定此关键字。 默认值为 `false`。

`ValueFromPipelineByPropertyName` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数从管道对象的属性中获取其值，该对象具有与此参数相同的名称或别名。 例如，如果该 cmdlet 具有 `Name` 参数并且管道对象还具有一个 `Name` 属性，则该属性的值将 `Name` 分配给该 cmdlet 的 `Name` 参数。 默认值为 `false`。

`ValueFromRemainingArguments` ([system.object](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数接受传递到 cmdlet 的所有剩余参数。 默认值为 `false`。

`HelpMessage` 可选的命名参数。 指定参数的简短说明。 运行 cmdlet 时，Windows PowerShell 会显示此消息，未指定必需的参数。

`HelpMessageBaseName` 可选的命名参数。 指定资源标识符驻留的位置。 例如，此参数可以指定包含要本地化的帮助消息的资源程序集。

`HelpMessageResourceId` 可选的命名参数。指定帮助消息的资源标识符。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅 [如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。

- Cmdlet 可以有任意数量的参数。 但是，为了获得更好的用户体验，请限制参数的数目。

- 必须对公共非静态字段或属性声明参数。 应在属性上声明参数。 该属性必须具有公共集访问器，如果指定了 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 关键字，则该属性必须具有公共 get 访问器。

- 当指定位置参数时，请将参数集中的位置参数数目限制为小于5。 和，位置参数不必是连续的。 位置5、100和250的工作方式与位置0、1和2相同。

- 如果 `Position` 未指定关键字，则必须按其名称引用 cmdlet 参数。

- 使用参数集时，请注意以下事项：

  - 每个参数集必须至少具有一个唯一参数。 良好的 cmdlet 设计指明此唯一参数应该也是必需的（如果可能）。 如果你的 cmdlet 设计为不带参数运行，则 unique 参数不是必需的。

  - 参数集应包含多个具有相同位置的位置参数。

  - 参数集中只应声明一个参数 `ValueFromPipeline = true` 。

  - 可以定义多个参数 `ValueFromPipelineByPropertyName = true` 。

- 有关参数名称的准则的详细信息，请参阅 [Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)。

- 参数属性是由 [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 类定义的。

## <a name="see-also"></a>另请参阅

[System.web. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
