---
title: IReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 867c09caa3bd3aed50de21c2ef91a02782830be2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704553"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity インターフェイス

コードオブジェクトの一意の署名への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|`IReferenceIdentity` `IReferenceIdentity` 指定した属性の変更を除き、このと同一の新しいインスタンスへのインターフェイスポインターを取得します。|  
|`IReferenceIdentity::EnumAttributes`|`IEnumIDENTITY_ATTRIBUTE`このに関連付けられている属性を格納しているインスタンスへのインターフェイスポインターを取得し `IReferenceIdentity` ます。|  
|`IReferenceIdentity::GetAttribute`|指定した名前を使用して、指定した名前空間の属性の値を取得します。|  
|`IReferenceIdentity::SetAttribute`|指定した名前空間と指定した名前を持つ属性を、指定した値に設定します。|  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** 分離 .h  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE インターフェイス](ienumidentity-attribute-interface.md)
