---
title: <typeparam> - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 9150ab3e29eaa6b692e2ab2be90bb0e87ba54941
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978653"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam> (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `name`  
 型パラメーターの名前。 名前は二重引用符 (" ") で囲みます。  
  
 `description`  
 型パラメーターの説明。  
  
## <a name="remarks"></a>コメント  
 `<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。 ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。  
  
 詳細については、「[ジェネリック](../../../csharp/programming-guide/generics/index.md)」を参照してください。  
  
 `<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)、コード コメント Web レポートに表示されます。  
  
 コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミングガイド](../../../csharp/programming-guide/index.md)
- [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
