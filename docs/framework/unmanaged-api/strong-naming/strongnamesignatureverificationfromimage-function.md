---
title: StrongNameSignatureVerificationFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: b90cc6fe99cf592f1b3fd117888462a957e4ce35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708427"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 関数

メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。  
  
 この関数は非推奨とされます。 代わりに [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pbBase`  
 からマップされたアセンブリマニフェストの相対仮想アドレス。  
  
 `dwLength`  
 からマップされたイメージのサイズ (バイト単位)。  
  
 `dwInFlags`  
 から検証の動作に影響を与えるフラグ。 サポートされている値を次に示します。  
  
- `SN_INFLAG_FORCE_VER` (0x00000001)-レジストリ設定を上書きする必要がある場合でも、検証を強制的に実行します。  
  
- `SN_INFLAG_INSTALL` (0x00000002)-これがこのイメージに対して実行される最初の検証であることを指定します。  
  
- `SN_INFLAG_ADMIN_ACCESS` (0x00000004)-キャッシュが管理者特権を持つユーザーのみにアクセスを許可することを指定します。  
  
- `SN_INFLAG_USER_ACCESS` (0x00000008)-現在のユーザーのみがアセンブリにアクセスできるように指定します。  
  
- `SN_INFLAG_ALL_ACCESS` (0x00000010)-キャッシュがアクセス制限の保証を提供しないことを指定します。  
  
- `SN_INFLAG_RUNTIME` (0x80000000)-内部デバッグ用に予約されています。  
  
 `pdwOutFlags`  
 入出力追加の出力情報のフラグ。 次の値がサポートされています。  
  
- `SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-この値は `false` 、レジストリ設定によって検証が成功したことを指定するためにに設定されます。  
  
## <a name="return-value"></a>戻り値  

 `true` 正常に完了した場合は。それ以外の場合は `false` 。  
  
## <a name="remarks"></a>注釈  

 関数が `StrongNameSignatureVerificationFromImage` 正常に完了しない場合は、 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerificationFromImage メソッド](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
