---
title: ICorDebugILCode::GetEHClauses メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: 38936a57944e9a0920c374f473c4cbe8e8d70abb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728668"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::GetEHClauses メソッド

[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 この中間言語 (IL) に対して定義されている例外処理 (EH) 句のリストへのポインターを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `cClauses`  
 [入力] `clauses` 配列の記憶容量。 詳細については、次の「解説」を参照してください。  
  
 `pcClauses`  
 [out] 情報が `clauses` アレイに書き込まれる場合に、対象となる句の数。  
  
 句  
 入出力この IL に対して定義されている例外処理句に関する情報を格納する [CorDebugEHClause](cordebugehclause-structure.md) オブジェクトの配列。  
  
## <a name="remarks"></a>注釈  

 `cClauses`が0で、 `pcClauses` が **null** 以外の場合、 `pcClauses` は使用可能な例外処理句の数に設定されます。 `cClauses` が 0 以外の場合は、`clauses` アレイの記憶容量を表します。 メソッドが戻るとき、`clauses` には、`cClauses` の最大項目が含まれ、`pcClauses` は、実際に`clauses` アレイに書き込まれる句の数が設定されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILCode インターフェイス](icordebugilcode-interface.md)
- [CorDebugEHClause 構造体](cordebugehclause-structure.md)
- [デバッグのインターフェイス](debugging-interfaces.md)
