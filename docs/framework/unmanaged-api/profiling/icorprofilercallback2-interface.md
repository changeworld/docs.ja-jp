---
title: ICorProfilerCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: 597a3dfecd42e206c98974093fa2417eba570f6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729466"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 インターフェイス

プロファイラーがサブスクライブしたイベントが発生したときにコードプロファイラーに通知するために、共通言語ランタイム (CLR) によって使用されるメソッドを提供します。 インターフェイスは、 `ICorProfilerCallback2` [ICorProfilerCallback](icorprofilercallback-interface.md) インターフェイスの拡張機能です。 つまり、.NET Framework バージョン2.0 で導入された新しいコールバックを提供します。  
  
> [!NOTE]
> 各メソッドの実装は、成功した場合は S_OK の値を持つ HRESULT を返し、失敗した場合は E_FAIL を返す必要があります。 現在、CLR では、 [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)を除く各コールバックによって返される HRESULT は無視されます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FinalizeableObjectQueued メソッド](icorprofilercallback2-finalizeableobjectqueued-method.md)|ファイナライザーを持つオブジェクトが、そのメソッドを実行するためにファイナライザースレッドに対してキューに登録されていることをコードプロファイラーに通知し `Finalize` ます。|  
|[GarbageCollectionFinished メソッド](icorprofilercallback2-garbagecollectionfinished-method.md)|ガベージコレクションが完了し、すべてのガベージコレクションコールバックが発行されたことをプロファイラーに通知します。|  
|[GarbageCollectionStarted メソッド](icorprofilercallback2-garbagecollectionstarted-method.md)|ガベージコレクションが開始されたことをコードプロファイラーに通知します。|  
|[HandleCreated メソッド](icorprofilercallback2-handlecreated-method.md)|ガベージコレクションハンドルが作成されたことをコードプロファイラーに通知します。|  
|[HandleDestroyed メソッド](icorprofilercallback2-handledestroyed-method.md)|ガベージコレクションハンドルが破棄されたことをコードプロファイラーに通知します。|  
|[RootReferences2 メソッド](icorprofilercallback2-rootreferences2-method.md)|ガベージコレクションが発生した後のルート参照をプロファイラーに通知します。 このメソッドは、 [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) メソッドの拡張です。|  
|[SurvivingReferences メソッド](icorprofilercallback2-survivingreferences-method.md)|ガベージコレクションで残ったオブジェクト参照をプロファイラーに通知します。|  
|[ThreadNameChanged メソッド](icorprofilercallback2-threadnamechanged-method.md)|スレッドの名前が変更されたことをコードプロファイラーに通知します。|  
  
## <a name="remarks"></a>注釈  

 CLR は、(または) インターフェイスのメソッドを呼び出して、 `ICorProfilerCallback` `ICorProfilerCallback2` プロファイラーがサブスクライブしているイベントが発生したときにプロファイラーに通知します。 これは、CLR がコードプロファイラーと通信するときに使用する主要なコールバックインターフェイスです。  
  
 コードプロファイラーは、インターフェイスのメソッドを実装する必要があり `ICorProfilerCallback` ます。 .NET Framework 2.0 以降のバージョンでは、プロファイラーはメソッドも実装する必要があり `ICorProfilerCallback2` ます。 各メソッドの実装は、成功した場合は S_OK の値を持つ HRESULT を返し、失敗した場合は E_FAIL を返す必要があります。 現在、CLR では、 [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)を除く各コールバックによって返される HRESULT は無視されます。  
  
 コードプロファイラーは、およびインターフェイスを実装する Microsoft Windows レジストリ (COM オブジェクト) に登録する必要があり `ICorProfilerCallback` `ICorProfilerCallback2` ます。 コードプロファイラーは、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)を呼び出して、通知を受信するイベントをサブスクライブします。 これは通常、プロファイラーによる [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)の実装で行われます。 その後、プロファイラーは、実行中のランタイムプロセスでイベントが発生するか、発生したばかりの場合に、ランタイムから通知を受け取ることができます。  
  
> [!NOTE]
> プロファイラーは、1つの COM オブジェクトを登録します。 プロファイラーが .NET Framework バージョン1.0 または1.1 を対象としている場合、その COM オブジェクトはのメソッドのみを実装する必要があり `ICorProfilerCallback` ます。 .NET Framework バージョン2.0 以降を対象としている場合、COM オブジェクトはのメソッドも実装する必要があり `ICorProfilerCallback2` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback インターフェイス](icorprofilercallback-interface.md)
- [ICorProfilerCallback3 インターフェイス](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 インターフェイス](icorprofilercallback4-interface.md)
