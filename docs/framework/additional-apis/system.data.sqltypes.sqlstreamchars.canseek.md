---
title: SqlStreamChars.CanSeek プロパティ (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: bde4764af9d0160997dc202f722a12393cfa59c1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826851"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars.CanSeek プロパティ

派生クラスでオーバーライドされると、現在のストリームがシーク操作をサポートしているかどうかを示す値を取得します。 このプロパティが含まれるアセンブリには、SQLAccess.dll で友人関係があります。 SQL Server で使用するものでは。 その他のデータベースには、そのデータベースによって提供されるホスティング メカニズムを使用します。

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>プロパティの値

<xref:System.Boolean>\
`true` 現在のストリームがシーク操作をサポートしている場合それ以外の場合、`false`します。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `SqlStreamChars.CanSeek`プロパティはプライベートであり、コード内で直接使用するものではありません。
>
> Microsoft はいかなる運用アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (system.data.dll 内)

**.NET framework のバージョン:** 2.0 以降で使用可能です。