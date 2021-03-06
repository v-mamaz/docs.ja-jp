---
title: '方法: デザイナーを使用して ToolStripMenuItems を非表示にします。'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 966ee5a7e038b80eb21b77c5ad5c0b57efa21951
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517228"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>方法: デザイナーを使用して ToolStripMenuItems を非表示にします。
メニュー項目を非表示には、アプリケーションのユーザー インターフェイス (UI) を制御し、ユーザーのコマンドを制限する方法です。 多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。 これは、ユーザーの混乱を表示します。 さらに、非表示だけでは、ユーザーはショートカット キーを使用してメニュー コマンドへのアクセスを非表示にして、メニューまたはメニュー項目を無効にする可能性があります。 メニュー項目を無効にする方法の詳細については、次を参照してください。[方法。デザイナーを使用して ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>トップレベル メニューとサブメニュー項目を非表示にするには  
  
1.  トップレベルのメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>または<xref:System.Windows.Forms.ToolStripItem.Available%2A>プロパティを`false`します。  
  
     トップレベルのメニュー項目を非表示にすると、そのメニュー内のすべてのメニュー項目でも非表示します。 以外の場所をクリックすると、<xref:System.Windows.Forms.MenuStrip>設定後<xref:System.Windows.Forms.ToolStripItem.Visible%2A>に`false`、操作の実行時の効果を示すため、フォームから、全体の最上位メニュー項目とサブメニュー項目が表示されなくなります。 デザイン時に非表示の最上位メニュー項目を表示する をクリックして、<xref:System.Windows.Forms.MenuStrip>で、**コンポーネント トレイ**の**ドキュメント アウトライン**、またはプロパティ グリッドの上部にあります。  
  
> [!NOTE]
>  複数のドキュメント インターフェイス (MDI) 子メニューにマージする場合を除くメニュー全体を非表示にはことはほとんどありません。  
  
### <a name="to-hide-a-submenu-item"></a>サブメニュー項目を非表示にするには  
  
1.  サブメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`します。  
  
     サブメニュー項目を非表示にするときにそのまま表示デザイン時にフォーム上の作業をさらに簡単に選択できるようにします。 実行時に実際には表示されません。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
- [方法: デザイナーを使用して ToolStripMenuItems を無効にします。](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
