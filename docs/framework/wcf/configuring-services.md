---
title: WCF サービスの構成
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: a5fe0cabb1a6be7f93bf5f4d753e9bb08a39cea3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253337"
---
# <a name="configuring-wcf-services"></a>WCF サービスの構成

サービス コントラクトの設計、実装が終われば、サービスを構成できる状態になります。 クライアント側から見たサービスの動作は、ここで定義、カスタマイズします。サービスと通信するためのアドレス、メッセージの送受信に使うトランスポートやエンコーディング、必要なセキュリティ型などを指定できます。  
  
 定義やカスタマイズは、コード内で強制的に (簡単には変更できないような形で) 行う方法と、構成ファイルに記述して行う方法があります。エンドポイントのアドレス、実際に使うトランスポート、セキュリティ スキーマなど、サービスに関するさまざまな事項を定義、カスタマイズできます。 実際には、構成の記述は、WCF アプリケーションのプログラミングの主要な部分です。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [簡略化された構成](simplified-configuration.md)  
 .NET Framework 4 以降、wcf には、WCF の構成要件を簡略化する新しい既定の構成モデルが用意されています。 特定のサービスに対して WCF の構成を指定しない場合、ランタイムは既定のエンドポイント、バインド、および動作を使用してサービスを自動的に構成します。  
  
 [構成ファイルを使用してサービスを構成する方法](configuring-services-using-configuration-files.md)  
 Windows Communication Foundation (WCF) サービスは、.NET Framework 構成テクノロジを使用して構成できます。 通常、XML 要素は、WCF サービスをホストするインターネットインフォメーションサービス (IIS) サイトの Web.config ファイルに追加されます。 この要素によって、コンピューターごとにエンドポイント アドレス (サービスと通信するために使用する実際のアドレス) などの詳細情報を変更できます。  
  
 [バインド](bindings.md)  
 さらに、WCF には、システムによって提供されるいくつかの共通構成がバインド形式で含まれており、使用されるトランスポート、セキュリティ、メッセージエンコーディングなど、クライアントとサービスの通信方法に関する最も基本的な機能を簡単に選択できます。  
  
 [エンドポイント](endpoints.md)  
 WCF サービスとの通信はすべて、サービスの *エンドポイント* を介して行われます。 エンドポイントには、コントラクト、バインディングで指定されている構成情報、およびサービスの検索場所やサービスに関する情報の取得場所を示すアドレスが設定されています。  
  
 [サービスのセキュリティ保護](securing-services.md)  
 WCF と既存のセキュリティメカニズムを使用すると、機密性、整合性、認証、および承認を任意のサービスに実装できます。 また、セキュリティに関する成功および失敗を監査することも可能です。  
  
 [WS-I Basic Profile 1.1 の相互運用可能サービスの作成](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 他のプラットフォームやオペレーティング システム上で動作するサービスやクライアントと、相互に運用できるような形でサービスを配置するために必要な事項は、WS-I Basic Profile 1.1 の仕様に記載されています。  
  
## <a name="reference"></a>関連項目  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>関連項目  

 [基本的なプログラミング ライフサイクル](basic-programming-lifecycle.md)  
  
 [サービスの設計と実装](designing-and-implementing-services.md)  
  
 [ホスティング サービス](hosting-services.md)  
  
 [クライアントを構築する](building-clients.md)  
  
 [拡張機能の概要](introduction-to-extensibility.md)  
  
 [管理と診断](./diagnostics/index.md)  
  
## <a name="see-also"></a>関連項目

- [基本的な WCF プログラミング](basic-wcf-programming.md)
- [概念の概要](conceptual-overview.md)
- [WCF 機能の詳細](./feature-details/index.md)
