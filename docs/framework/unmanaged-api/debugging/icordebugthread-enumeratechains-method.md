---
title: ICorDebugThread::EnumerateChains メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 76b231f00651186518d3bccfafa5780f258c4f75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688186"
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains メソッド

この ICorDebugChainEnum Thread オブジェクト内のすべてのスタックチェーンを含む、列挙子へのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `ppChains`  
 入出力 `ICorDebugChainEnum` アクティブな (つまり、最新の) チェーンを開始位置として、このスレッド内のすべてのスタックチェーンを列挙できるようにするオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>注釈  

 スタックチェーンは、スレッドの物理的な呼び出し履歴を表します。 次の状況では、スタックチェーン境界が作成されます。  
  
- マネージからアンマネージ、または管理対象外の遷移。  
  
- コンテキストスイッチ。  
  
- ユーザースレッドのデバッガーハイジャック。  
  
 単一のコンテキストで純粋なマネージコードを実行しているスレッドの単純なケースでは、スレッドとスタックチェーンの間に1対1の対応が存在します。  
  
 デバッガーは、すべてのスレッドの物理的な呼び出し履歴を論理呼び出し履歴に再配置することが必要になる場合があります。 これには、すべてのスレッドのチェーンを呼び出し元/呼び出し先の関係によって並べ替え、それらを再グループ化することが含まれます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
