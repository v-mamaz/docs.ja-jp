---
title: '方法: Windows フォーム内で非同期的にサウンドを読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 8619ea3fb06a9c7c6896176fe3ae2a4b8dfe4ded
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260702"
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>方法: Windows フォーム内で非同期的にサウンドを読み込む
次のコード例では、URL からサウンドを非同期的に読み込み、新しいスレッド上で再生します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
-   ファイル名 `"http://www.tailspintoys.com/sounds/stop.wav"` を有効なファイル名に置き換えます。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、次を参照してください。 [、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)します。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイルの操作は、適切な例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。 たとえば、無効な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException> クラス)。  
  
-   パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。  
  
-   パス名が `Nothing` である場合 (<xref:System.ArgumentNullException> クラス)。  
  
-   パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。  
  
-   パスが有効でない場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。  
  
-   パスがコロン":" のみである場合 (<xref:System.NotSupportedException> クラス)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Media.SoundPlayer.LoadAsync%2A>
- <xref:System.Media.SoundPlayer.LoadCompleted>
- <xref:System.Media.SoundPlayer.Play%2A>
- [Windows フォームからサウンドを再生します。](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
