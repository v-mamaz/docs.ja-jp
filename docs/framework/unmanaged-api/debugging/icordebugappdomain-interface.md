---
title: ICorDebugAppDomain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db2052bafb259f07370f007f699f6858c532b11d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973757"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain インターフェイス

アプリケーション ドメインをデバッグするためのメソッドを提供します。 このインターフェイスは、ICorDebugController のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Attach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|アプリケーション ドメインに、デバッガーをアタッチします。|  
|[EnumerateAssemblies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|アプリケーション ドメインでアセンブリの列挙子を取得します。|  
|[EnumerateBreakpoints メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|アプリケーション ドメインですべてのアクティブなブレークポイントの列挙子を取得します。|  
|[EnumerateSteppers メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|アプリケーション ドメイン内のすべてのアクティブ ステッパの列挙子を取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|アプリケーション ドメインの一意の ID を取得します。|  
|[GetModuleFromMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|特定のメタデータ インターフェイスを持つ ICorDebugModule オブジェクトを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|アプリケーション ドメインの名前を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|共通言語ランタイム (CLR) のアプリケーション ドメインにインターフェイス ポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|アプリケーション ドメインを格納しているプロセスを取得します。|  
|[IsAttached メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|アプリケーション ドメインに、デバッガーがアタッチされているかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
