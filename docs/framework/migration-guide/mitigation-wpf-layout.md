---
title: '軽減策: WPF レイアウト'
description: 1 ピクセル単位で動かすことでオブジェクトを配置するなど、WPF コントロール レイアウトを変更した結果として発生する問題を軽減する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244081"
---
# <a name="mitigation-wpf-layout"></a>軽減策:WPF レイアウト

WPF コントロールのレイアウトが若干変化する可能性があります。  
  
## <a name="impact"></a>影響  

 この変更の結果、以下のようになります。  
  
- 要素の幅または高さが最大で 1 ピクセル拡大または縮小することがあります。  
  
- オブジェクトの配置が最大で 1 ピクセル移動することがあります。  
  
- 中央揃えの要素が中央から最大で 1 ピクセル垂直まは水平方向にずれることがあります。  
  
 既定では、この新しいレイアウトは .NET Framework の 4.6 を対象とするアプリに対してのみ有効となります。  
  
## <a name="mitigation"></a>軽減策  

 この変更では、DPI が高いときにWPF コントロールの一番右または一番下でクリッピングの発生を除去する傾向があるため、app.config ファイルの `<runtime>` セクションに次の行を追加することによって、以前のバージョンの .NET Framework を対象としながら .NET Framework 4.6 上で実行されているアプリがこの新しい動作を選択ことができます。  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4.6 を対象としながら以前のレイアウト アルゴリズムを使用して WPF コントロールをレンダリングする必要があるアプリの場合、app.config ファイルの `<runtime>` セクションに次の行を追加することによってそれを行うことができます。  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>関連項目

- [アプリケーションの互換性](application-compatibility.md)
