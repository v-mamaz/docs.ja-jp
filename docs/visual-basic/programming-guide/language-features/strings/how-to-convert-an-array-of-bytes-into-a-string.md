---
title: '方法: Visual Basic で文字列のバイト配列に変換します。'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: cd091d743b04ef9d9709bde2b5a1205f3d7ae292
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979511"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>方法: Visual Basic で文字列のバイト配列に変換します。
このトピックでは、バイト配列からバイトを文字列に変換する方法を示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Text.Encoding.GetString%2A>のメソッド、<xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>バイト配列からすべてのバイトを文字列に変換するクラスをエンコードします。  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 バイト配列を文字列に変換するいくつかのエンコード オプションから選択できます。  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>:ASCII (7 ビット) 文字セットのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>:ビッグ エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>:システムの現在の ANSI コード ページのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>:リトル エンディアン バイト順を使用する utf-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>:リトル エンディアン バイト順を使用する utf-32 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>:UTF-7 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>:UTF-8 形式のエンコーディングを取得します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [方法: 文字列を Visual Basic でバイト配列に変換します。](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
