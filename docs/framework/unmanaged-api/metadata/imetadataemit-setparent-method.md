---
title: IMetaDataEmit::SetParent メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a37edd38cd8dc6971ee9185f73d6c6d8ab5332b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657132"
---
# <a name="imetadataemitsetparent-method"></a>IMetaDataEmit::SetParent メソッド
確立する前回の呼び出しで定義されている、指定されたメンバー [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)、前回の呼び出しで定義されている、指定した型のメンバーである[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mr`  
 [in]`mdMemberRef`新しい親を受信するトークン。  
  
 `tk`  
 [in]`mdToken`新しい親。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
