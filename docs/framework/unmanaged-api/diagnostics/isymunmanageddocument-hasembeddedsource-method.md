---
title: ISymUnmanagedDocument::HasEmbeddedSource メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acff919cbeb6b5d71197664139cdc9212961e314
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629515"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a>ISymUnmanagedDocument::HasEmbeddedSource メソッド
返します`true`ドキュメントが、デバッグのシンボルに埋め込まれたソースを返しますそれ以外の場合、`false`します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]デバッグのシンボルにドキュメントがソースになっているかどうかを示す変数へのポインターが埋め込まれます。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedDocument インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
