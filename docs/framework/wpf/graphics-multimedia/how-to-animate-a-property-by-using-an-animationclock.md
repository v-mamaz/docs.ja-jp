---
title: '方法: AnimationClock を使用してプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: 7940d65c61d57ec9c6a2a6e02e3b1e3e0bb2795f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610475"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>方法: AnimationClock を使用してプロパティをアニメーション化する
この例は、使用する方法を示します<xref:System.Windows.Media.Animation.Clock>プロパティをアニメーション化するオブジェクト。  
  
 依存関係プロパティをアニメーション化するには次の 3 つの方法があります。  
  
-   作成、<xref:System.Windows.Media.Animation.AnimationTimeline>を使用してそのプロパティに関連付けると、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
-   オブジェクトの<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドは、1 つを適用する<xref:System.Windows.Media.Animation.AnimationTimeline>対象のプロパティにします。  
  
-   作成、<xref:System.Windows.Media.Animation.AnimationClock>から、<xref:System.Windows.Media.Animation.AnimationTimeline>プロパティに適用されます。  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトおよび<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用すると、直接の作成とクロックを配布せずにプロパティをアニメーション化する (例については、次を参照してください[ストーリー ボードを使用してプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)と[プロパティせずアニメーション化します。ストーリー ボードを使用して](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md))。クロックは作成され、自動的に配布します。  
  
## <a name="example"></a>例  
 次の例を作成する方法を示しています、<xref:System.Windows.Media.Animation.AnimationClock>同様の 2 つのプロパティに適用されます。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 対話的に制御する方法を示す例については、 <xref:System.Windows.Media.Animation.Clock> 、開始後を参照してください。[クロックを対話的に制御](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md)します。  
  
## <a name="see-also"></a>関連項目
- [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)
- [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
