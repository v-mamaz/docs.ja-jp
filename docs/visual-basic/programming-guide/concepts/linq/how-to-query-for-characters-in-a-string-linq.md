---
title: '方法: クエリ (LINQ) (Visual Basic)、文字列内の文字'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 3a4f3bbca313747e0b16170719b9028e5dc9174f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559750"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>方法: クエリ (LINQ) (Visual Basic)、文字列内の文字
<xref:System.String> クラスはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装しているため、任意の文字列を文字のシーケンスとしてクエリできます。 ただし、これは LINQ の一般的な使用方法ではありません。 複雑なパターン一致操作には、<xref:System.Text.RegularExpressions.Regex> クラスを使用してください。  
  
## <a name="example"></a>例  
 次の例では、文字列を対象にクエリを実行して、その文字列に含まれる数字の数を特定します。 クエリは、最初に使用された後も "再利用" されます。 これができるのは、クエリ自体には実際の結果が格納されないためです。  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll および System.Linq 名前空間の `Imports` ステートメントを参照設定します。  
  
## <a name="see-also"></a>関連項目
- [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [方法: LINQ クエリは、正規表現を使用 (Visual Basic) とを組み合わせる](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
