---
title: IsFrameworkAssembly 関数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728564"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 関数

指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzAssemblyReference`  
 から確認するアセンブリの名前。  
  
 `pbIsFrameworkAssembly`  
 入出力アセンブリが管理されているかどうかを示すブール値。  
  
 `pwzFrameworkAssemblyIdentity`  
 からアセンブリの一意の id を含む、正規化されていない文字列。  
  
 `pccSize`  
 [入力] `pwzFrameworkAssemblyIdentity` のサイズ。  
  
## <a name="remarks"></a>注釈  

 パラメーターは、 `pwzAssemblyReference` アセンブリの名前を含む文字列へのポインターです。  
  
 このアセンブリが .NET Framework の一部である場合、 `pbIsFrameworkAssembly` パラメーターにはのブール値が格納され `true` ます。  
  
 名前付きアセンブリが .NET Framework に含まれていない場合、またはパラメーターがアセンブリの名前を指定しない場合 `pwzAssemblyReference` 、に `pbIsFrameworkAssembly` はブール値のが格納され `false` ます。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
