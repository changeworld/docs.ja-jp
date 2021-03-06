---
title: ICLRDataTarget3::GetExceptionContextRecord メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 87065b83e0b28eafdf5099f99fd188e2e21e7a12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723624"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord メソッド

ターゲット プロセスに関連付けられたコンテキスト レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。 たとえば、ダンプターゲットの場合、これは `ExceptionParam` Windows デバッグヘルプライブラリ (dbghelp) の [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) 関数の引数を使用して渡されたコンテキストレコードと同じになります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `bufferSize`  
 [入力] 入力バッファー サイズ (バイト単位)。 これはコンテキスト レコードを格納するのに十分な大きさである必要があります。  
  
 `bufferUsed`  
 [出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。  
  
 `buffer`  
 [出力] コンテキスト レコードのコピーを受け取るメモリ バッファーへのポインター。 例外レコードは、 [コンテキスト](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) 型として返されます。  
  
## <a name="return-value"></a>戻り値  

 戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。 次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|`S_OK`|メソッドが成功しました。 コンテキスト レコードは出力バッファーにコピーされました。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|コンテキスト レコードはターゲットに関連付けられていません。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|入力バッファーのサイズが足りないため、コンテキスト レコードを格納できません。|  
  
## <a name="remarks"></a>注釈  

 [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) は、Windows SDK によって提供されるヘッダーで定義されているプラットフォーム固有の構造体です。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** ClrData .idl, ClrData .h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget3 インターフェイス](iclrdatatarget3-interface.md)
- [GetExceptionRecord メソッド](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID メソッド](iclrdatatarget3-getexceptionthreadid-method.md)
