---
title: < (より小さい) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 389c50a697c90dadb075369fe696f7382caf3cff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161920"
---
# <a name="-less-than-entity-sql"></a>\< (より小さい) (Entity SQL)

2 つの式を比較して、左の式の値が右の式の値よりも小さいかどうかを判別します。  
  
## <a name="syntax"></a>構文  
  
```sql  
expression < expression  
```  
  
## <a name="arguments"></a>引数  

 `expression`  
 任意の有効な式。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。  
  
## <a name="result-types"></a>戻り値の型  

 左の式の値が右の式の値よりも小さい場合は`true` 、そうでない場合は `false`。  
  
## <a name="example"></a>例  

 次の Entity SQL クエリは、「<」比較演算子を使用して 2 つの式を比較し、左の式の値が右の式の値よりも小さいかどうかを判別します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2. 次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-sql[DP EntityServices Concepts#LESS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](entity-sql-reference.md)
