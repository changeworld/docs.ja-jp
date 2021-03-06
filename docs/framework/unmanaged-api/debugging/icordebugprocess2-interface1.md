---
title: ICorDebugProcess2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: f1a30c197373928ec10c2b84de4e805b94ea2384
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724508"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 インターフェイス

は、マネージコードを実行しているプロセスを表す、のような、の論理拡張機能です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint メソッド](icordebugprocess2-clearunmanagedbreakpoint-method.md)|の以前の呼び出しで設定された、指定したオフセット位置にあるブレークポイントを削除 `ICorDebugProcess2::SetUnmanagedBreakpoint` します。|  
|[GetDesiredNGENCompilerFlags メソッド](icordebugprocess2-getdesiredngencompilerflags-method.md)|このによって参照されるプロセスにイメージを読み込むために共通言語ランタイム (CLR) に対して設定する必要があるフラグを取得し `ICorDebugProcess2` ます。|  
|[GetReferenceValueFromGCHandle メソッド](icordebugprocess2-getreferencevaluefromgchandle-method.md)|ガベージコレクションハンドルを持つ指定したマネージオブジェクトへの参照ポインターを取得します。|  
|[GetThreadForTaskID メソッド](icordebugprocess2-getthreadfortaskid-method.md)|指定した id を持つタスクが実行されているスレッドを取得します。|  
|[GetVersion メソッド](icordebugprocess2-getversion-method.md)|デバッグ中のプロセスが実行されている CLR のバージョンを取得します。|  
|[SetDesiredNGENCompilerFlags メソッド](icordebugprocess2-setdesiredngencompilerflags-method.md)|Just-in-time (JIT) コンパイラがデバッグ中のプロセスにイメージを読み込むために必要なフラグを設定します。|  
|[SetUnmanagedBreakpoint メソッド](icordebugprocess2-setunmanagedbreakpoint-method.md)|指定したネイティブイメージオフセットにアンマネージブレークポイントを設定します。|  
  
## <a name="remarks"></a>注釈  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](debugging-interfaces.md)
