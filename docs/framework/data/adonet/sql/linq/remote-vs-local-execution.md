---
title: クエリのリモート実行とローカル実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
ms.openlocfilehash: 9d72350c472ff68d8ee623d82096bdab0c88abb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547119"
---
# <a name="remote-vs-local-execution"></a>クエリのリモート実行とローカル実行
クエリは、リモートで実行することも (データベース エンジンによるデータベースに対するクエリの実行)、ローカルに実行することも ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によるローカル キャッシュに対するクエリの実行) できます。  
  
## <a name="remote-execution"></a>リモート実行  
 次のクエリがあるとします。  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 データベース内に大量の行がある場合は、小さなサブセットを処理するためにすべての行を取得するのは望ましくありません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.EntitySet%601> クラスに <xref:System.Linq.IQueryable> インターフェイスが実装されています。 これにより、このようなクエリをリモートで実行することが可能になります。 この方法には、次の 2 つの大きな利点があります。  
  
-   不要なデータは取得されません。  
  
-   多くの場合、データベース エンジンによって実行されるクエリは、データベース インデックスの効果でより効率的になります。  
  
## <a name="local-execution"></a>ローカル実行  
 一方、関連するエンティティ全体をローカル キャッシュに取り込むことが必要な場合もあります。 この目的から、<xref:System.Data.Linq.EntitySet%601> には、<xref:System.Data.Linq.EntitySet%601.Load%2A> のすべてのメンバーを明示的に読み込む <xref:System.Data.Linq.EntitySet%601> メソッドが用意されています。  
  
 <xref:System.Data.Linq.EntitySet%601> が既に読み込まれている場合、それ以降のクエリはローカルに実行されます。 この方法は、次の 2 つの点で役立ちます。  
  
-   データ全体をローカルで使用する必要がある場合、または複数回使用する必要がある場合に、リモート クエリおよびそれに伴う待機時間を回避できます。  
  
-   エンティティ全体をシリアル化できます。  
  
 次のコードは、ローカル実行を行う方法を示しています。  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a>比較  
 この 2 種類の実行方法は、強力なオプションの組み合わせになります。つまり、大規模なコレクションではリモート実行を、小規模なコレクションまたは完全なコレクションが必要な場合はローカル実行を選択できます。 リモート実行は <xref:System.Linq.IQueryable> を使用して実装し、ローカル実行はメモリ内の <xref:System.Collections.Generic.IEnumerable%601> コレクションに対して行います。 ローカル実行を強制する (つまり、 <xref:System.Collections.Generic.IEnumerable%601>) を参照してください[汎用 IEnumerable に型を変換](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)します。  
  
### <a name="queries-against-unordered-sets"></a>順序なしのセットに対するクエリ  
 実装するローカル コレクションの重要な違いに注意してください<xref:System.Collections.Generic.List%601>およびコレクションに対して実行されるリモート クエリを提供する*セットを順不同*リレーショナル データベースでします。 インデックス値を使用するメソッドなど、<xref:System.Collections.Generic.List%601> のメソッドにはリストのセマンティクスが必要ですが、これは通常、順序なしのセットに対するリモート クエリからは得られません。 このため、このようなメソッドでは、ローカル実行を可能にするために暗黙的に <xref:System.Data.Linq.EntitySet%601> が読み込まれます。  
  
## <a name="see-also"></a>関連項目
- [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
