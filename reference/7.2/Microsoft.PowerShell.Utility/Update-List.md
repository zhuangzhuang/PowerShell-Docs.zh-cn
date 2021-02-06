---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-list?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-List
ms.openlocfilehash: ae473541770948dee1ce927ddee45bd806d8ff29
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596635"
---
# Update-List

## 摘要
在包含对象集合的属性值中添加和删除项。

## SYNTAX

### AddRemoveSet（默认值）

```
Update-List [-Add <Object[]>] [-Remove <Object[]>] [-InputObject <PSObject>] [[-Property] <String>]
 [<CommonParameters>]
```

### ReplaceSet

```
Update-List -Replace <Object[]> [-InputObject <PSObject>] [[-Property] <String>] [<CommonParameters>]
```

## DESCRIPTION

`Update-List`Cmdlet 可在对象的属性值中添加、移除或替换项，并返回已更新的对象。 此 cmdlet 旨在用于包含对象集合的属性。

" **添加** " 和 " **删除** " 参数在集合中添加和移除单个项。
**Replace** 参数将替换整个集合。

如果未在命令中指定属性，则将 `Update-List` 返回描述更新的对象，而不是更新对象。 你可以将更新对象提交给更改对象的 cmdlet，例如 `Set` cmdlet。

仅当正在更新的属性支持使用的 **IList** 接口时，此 cmdlet 才有效 `Update-List` 。 此外， `Set` 接受更新的任何 cmdlet 都必须支持 **IList** 接口。

随 PowerShell 一起安装的核心 cmdlet 不支持此接口。 若要确定 cmdlet 是否支持 `Update-List` ，请参阅 Cmdlet 帮助主题。

此 cmdlet 已在 PowerShell 7 中引入。

## 示例

### 示例1：将项添加到属性值

在此示例中，我们将创建一个类，它表示卡的卡片组，其中卡片存储为 **列表** 集合对象。 **NewDeck ( # B1** 方法使用 `Update-List` 将一组完整的卡值添加到 **卡** 集合。

```powershell
class Cards {

    [System.Collections.Generic.List[string]]$cards
    [string]$name

    Cards([string]$_name) {
        $this.name = $_name
        $this.cards = [System.Collections.Generic.List[string]]::new()
    }

    NewDeck() {
        $_suits = "`u{2663}","`u{2666}","`u{2665}","`u{2660}"
        $_values = 'A',2,3,4,5,6,7,8,9,10,'J','Q','K'
        $_deck = foreach ($s in $_suits){ foreach ($v in $_values){ "$v$s"} }
        $this | Update-List -Property cards -Add $_deck | Out-Null
    }

    Show() {
        Write-Host
        Write-Host $this.name ": " $this.cards[0..12]
        if ($this.cards.count -gt 13) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[13..25]
        }
        if ($this.cards.count -gt 26) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[26..38]
        }
        if ($this.cards.count -gt 39) {
            Write-Host (' ' * ($this.name.length+3)) $this.cards[39..51]
        }
    }

    Shuffle() { $this.cards = Get-Random -InputObject $this.cards -Count 52 }

    Sort() { $this.cards.Sort() }
}
```

> [!NOTE]
> `Update-List`Cmdlet 可将更新后的对象输出到管道。 我们通过管道将输出传递给 `Out-Null` ，以禁止显示不需要的显示。

### 示例2：在集合属性中添加和移除项

继续使用示例1中的代码，我们将创建 **卡片** 类的实例，以表示一组卡片和两个播放器容纳的卡。 我们使用 `Update-List` cmdlet 向玩家的手中添加卡，并从纸牌中删除牌。

```powershell
$player1 = [Cards]::new('Player 1')
$player2 = [Cards]::new('Player 2')

$deck = [Cards]::new('Deck')
$deck.NewDeck()
$deck.Shuffle()
$deck.Show()

# Deal two hands
$player1 | Update-List -Property cards -Add $deck.cards[0,2,4,6,8] | Out-Null
$player2 | Update-List -Property cards -Add $deck.cards[1,3,5,7,9] | Out-Null
$deck | Update-List -Property cards -Remove $player1.cards | Out-Null
$deck | Update-List -Property cards -Remove $player2.cards | Out-Null

$player1.Show()
$player2.Show()
$deck.Show()
```

```Output
Deck :  4♦ 7♥ J♦ 5♣ A♣ 8♦ J♣ Q♥ 6♦ 3♦ 9♦ 6♣ 2♣
        K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥ Q♠
        3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠ 2♥
        6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣ 8♥

Player 1 :  4♦ J♦ A♣ J♣ 6♦

Player 2 :  7♥ 5♣ 8♦ Q♥ 3♦

Deck :  9♦ 6♣ 2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣
        Q♣ A♥ Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠
        4♣ 2♠ 2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣
        A♦ K♣ 8♥
```

输出显示将卡发到玩家之前的卡片组的状态。 您可以看到，每个玩家都接收了卡片组中的五行。 最终输出显示了将卡处理到玩家后的卡片组状态。 `Update-List` 用于从卡片组中选择卡并将其添加到播放机的集合中。 然后，使用将从中删除玩家的卡片 `Update-List` 。

### 示例3：在单个命令中添加和删除项

`Update-List` 允许你在单个命令中使用 **Add** 和 **Remove** 参数。 在此示例中，Player 1 要丢弃 `4♦` 并 `6♦` 获得两个新卡。

```powershell
# Player 1 wants two new cards - remove 2 cards & add 2 cards
$player1 | Update-List -Property cards -Remove $player1.cards[0,4] -Add $deck.cards[0..1] | Out-Null
$player1.Show()

# remove dealt cards from deck
$deck | Update-List -Property cards -Remove $deck.cards[0..1] | Out-Null
$deck.Show()
```

```Output
Player 1 :  J♦ A♣ J♣ 9♦ 6♣

Deck :  2♣ K♥ 4♠ 10♥ 8♠ 10♦ 9♠ 6♠ K♦ 7♣ 3♣ Q♣ A♥
        Q♠ 3♥ 5♥ 2♦ 5♠ J♥ J♠ 10♣ 4♥ Q♦ 10♠ 4♣ 2♠
        2♥ 6♥ 7♦ A♠ 5♦ 8♣ 9♥ K♠ 7♠ 3♠ 9♣ A♦ K♣
        8♥
```

## PARAMETERS

### -Add

指定要添加到集合中的属性值。 按照值应该在集合中出现的顺序输入值。

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要更新的对象。 还可以通过管道将对象更新为 `Update-List` 。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Property

指定包含正在更新的集合的属性。 如果省略此参数，则 `Update-List` 返回一个表示更改的对象，而不是更改该对象。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Remove

指定要从集合中删除的属性值。

```yaml
Type: System.Object[]
Parameter Sets: AddRemoveSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Replace

指定新集合。 此参数会将原始集合中的所有项替换为由此参数指定的项。

```yaml
Type: System.Object[]
Parameter Sets: ReplaceSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

此 cmdlet 支持以下常见参数：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 有关详细信息，请参阅 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 输入

### System.Management.Automation.PSObject

你可以通过管道将要更新的对象传递给 `Update-List` 。

## 输出

### 对象或 System.Management.Automation.PSListModifier

`Update-List` 返回更新的对象，或返回一个表示更新操作的对象。

## 注释

## 相关链接

[Format-List](Format-List.md)

[Select-Object](Select-Object.md)

