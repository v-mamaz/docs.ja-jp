---
title: '方法: 実行時にコントロールを非表示にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: 00f352e0b2c0582c45710f7e5a26e68ab7fbd944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597794"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>方法: 実行時にコントロールを非表示にします。
実行時に表示されているユーザー コントロールを作成する場合もあります。 たとえば、アラーム時計コントロールはを除き、アラームが鳴っているときに表示でない可能性があります。 設定して、テストは簡単、<xref:System.Windows.Forms.Control.Visible%2A>プロパティ。 場合、<xref:System.Windows.Forms.Control.Visible%2A>プロパティは`true`コントロールを通常どおりに表示されます。 場合`false`コントロールが非表示にします。 コントロール内のコードは、非表示のとき実行可能性がありますが、ユーザー インターフェイスを使用するコントロールと対話することはできません。 ユーザー (マウス クリックなど) の入力に応答できる状態でコントロールを非表示を作成する場合は、透過的なコントロールを作成する必要があります。 詳細については、次を参照してください。[制御を透明な背景を与える](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)します。  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>実行時にコントロールを非表示にするには  
  
1.  <xref:System.Windows.Forms.Control.Visible%2A> プロパティを `false`に設定します。  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Control.Visible%2A>
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [方法: コントロールに透明な背景を提供します。](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
