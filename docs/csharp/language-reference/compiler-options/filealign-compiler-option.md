---
title: -filealign (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: 3437b0f90593eed2900829212866cf689ff54e8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660178"
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# コンパイラ オプション)
**-filealign** オプションを使用すると、出力ファイル内のセクションのサイズを指定できます。  
  
## <a name="syntax"></a>構文  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>引数  
 `number`  
 出力ファイル内のセクションのサイズを指定する値です。 有効値は 512、1024、2048、4096、および 8192 です。 これらの値はバイト単位です。  
  
## <a name="remarks"></a>コメント  
 各セクションは、**-filealign** 値の倍数である境界上にアラインされます。 固定の既定値はありません。 **-filealign** が指定されていない場合、共通言語ランタイムはコンパイル時に既定値を選択します。  
  
 セクションのサイズを指定すると、出力ファイルのサイズに影響します。 セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。  
  
 出力ファイル内のセクションに関する情報を表示するには、[DUMPBIN](/cpp/build/reference/dumpbin-options) を使用します。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **[詳細設定]** ボタンをクリックします。  
  
4.  **[ファイルの配置]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
- [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
