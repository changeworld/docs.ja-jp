---
title: 定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e820287f0ddf462b30867d90501f7d730c9c6739
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163156"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>BC30424:定数は、class、structure、または array 型ではなく、組み込み型または列挙型でなければなりません。

定数をクラス、構造体、または配列型として宣言しようとしたか、格納先のジェネリック型によって定義された型パラメーターとして宣言しようとしました。

 定数は、組み込み型 (`Boolean`、`Byte`、`Date`、`Decimal`、`Double`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、または `UShort`)、または整数型のいずれかに基づいた `Enum` 型である必要があります。

 **エラー ID:** BC30424

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 定数を組み込み型または `Enum` 型として宣言します。

2. 定数は、`True`、`False`、`Nothing` などの特別な値でもかまいません。 コンパイラは、これらの定義済みの値を適切な組み込み型と見なします。

## <a name="see-also"></a>関連項目

- [定数と列挙体](../constants-and-enumerations.md)
- [データの種類](../../programming-guide/language-features/data-types/index.md)
- [データの種類](../data-types/index.md)
