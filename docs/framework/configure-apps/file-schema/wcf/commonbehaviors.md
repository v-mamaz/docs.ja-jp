---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268758"
---
# <a name="commonbehaviors"></a>\<commonBehaviors>
`commonBehaviors` セクションは、machine.config ファイルでだけ定義できます。 このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、それぞれのすべての WCF エンドポイントと、コンピューター上のサービスで使用された動作要素を定義します。 `endpointBehaviors` で定義される動作はクライアントだけに適用され、`serviceBehaviors` で定義される動作はサービスだけに適用されます。 ある動作が `commonBehaviors` と `behaviors` の両方のセクションで定義されている場合は、`behaviors` セクション内の動作が優先されます。
