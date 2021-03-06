---
title: グラフィックス インターフェイスの構造体
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: 4d000adfa02555a766410833fabe4039dd06c268
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592047"
---
# <a name="structure-of-the-graphics-interface"></a>グラフィックス インターフェイスの構造体
マネージ クラスのインターフェイスに[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]60 個のクラス、50 の列挙型、および 8 の構造が含まれています。 <xref:System.Drawing.Graphics>クラスは、の中核に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]機能です。 これは、直線、曲線、図形、イメージ、およびテキストを実際に描画するクラス。  
  
## <a name="important-classes"></a>重要なクラス  
 多くのクラスの機能と組み合わせて、<xref:System.Drawing.Graphics>クラス。 たとえば、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトを描画する線の属性 (色、幅、実線/点線スタイル、およびなど) を保持します。 <xref:System.Drawing.Graphics.FillRectangle%2A>メソッドへのポインターを受け取ることができます、<xref:System.Drawing.Drawing2D.LinearGradientBrush>で動作するには、オブジェクト、<xref:System.Drawing.Graphics>徐々 に変化する色で四角形を入力するオブジェクト。 <xref:System.Drawing.Font> <xref:System.Drawing.StringFormat>オブジェクトに影響を与える方法、<xref:System.Drawing.Graphics>オブジェクト テキストを描画します。 A<xref:System.Drawing.Drawing2D.Matrix>オブジェクトを操作および格納のワールド変換を<xref:System.Drawing.Graphics>オブジェクトで、回転、拡大縮小、およびイメージを反転するために使用します。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] いくつかの構造を提供します (たとえば、 <xref:System.Drawing.Rectangle>、 <xref:System.Drawing.Point>、および<xref:System.Drawing.Size>) グラフィックス データを整理するためです。 また、特定のクラスには、主に、構造化されたデータ型が機能します。 たとえば、<xref:System.Drawing.Imaging.BitmapData>クラスのヘルパーは、<xref:System.Drawing.Bitmap>クラス、および<xref:System.Drawing.Drawing2D.PathData>クラスのヘルパーは、<xref:System.Drawing.Drawing2D.GraphicsPath>クラス。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 関連する定数のコレクションである、いくつかの列挙を定義します。 たとえば、<xref:System.Drawing.Drawing2D.LineJoin>列挙型には要素が含まれています<xref:System.Drawing.Drawing2D.LineJoin.Bevel>、 <xref:System.Drawing.Drawing2D.LineJoin.Miter>、および<xref:System.Drawing.Drawing2D.LineJoin.Round>、2 つの直線を接合に使用できるスタイルを指定しています。  
  
## <a name="see-also"></a>関連項目
- [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
- [GDI+ マネージド コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)
- [マネージド グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
