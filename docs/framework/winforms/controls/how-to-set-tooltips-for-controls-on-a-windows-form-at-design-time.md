---
title: '方法: デザイン時に Windows フォーム上のコントロールのツールヒントを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: ebefe596728b5cabd9d24720d8c39f13c8836bd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609409"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>方法: デザイン時に Windows フォーム上のコントロールのツールヒントを設定します。
設定することができます、<xref:System.Windows.Forms.ToolTip>コードや、Windows フォーム デザイナーでの文字列。 詳細については、<xref:System.Windows.Forms.ToolTip>コンポーネントを参照してください[ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-set-a-tooltip-programmatically"></a>ツールヒントをプログラムで設定するには  
  
1.  ツールヒントを表示するコントロールを追加します。  
  
2.  使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネント。  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>デザイナーでツールヒントを設定するには  
  
1.  フォームに <xref:System.Windows.Forms.ToolTip> コンポーネントを追加します。  
  
2.  ツールヒントを表示または、フォームに追加されるコントロールを選択します。  
  
3.  **プロパティ**ウィンドウで、設定、 **ToolTip1 のツールヒント**テキストの適切な文字列値。  

### <a name="to-remove-a-tooltip-programmatically"></a>ツールヒントをプログラムで削除するには  
  
1.  使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネント。  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a>デザイナーでツールヒントを削除するには  
  
1.  ツールヒントが表示されているコントロールを選択します。  
  
2.  **プロパティ**ウィンドウ内のテキストを削除、 **ToolTip1 のツールヒント**します。  

## <a name="see-also"></a>関連項目
- [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)
- [方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更します。](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
