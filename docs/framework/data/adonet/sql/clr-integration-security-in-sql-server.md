---
title: SQL Server の CLR 統合セキュリティ
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: e5d15b4e5ac36f7ecddf45179c65a60995a1a578
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147776"
---
# <a name="clr-integration-security-in-sql-server"></a>SQL Server の CLR 統合セキュリティ

Microsoft SQL Server で新たに導入された機能の 1 つに、.NET Framework の共通言語ランタイム (CLR) コンポーネントの統合があります。 CLR の統合により、Microsoft Visual Basic .NET や Microsoft Visual C# を含む任意の .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を作成できるようになりました。  
  
 CLR は、コード アクセス セキュリティ (CAS) と呼ばれるマネージド コード用のセキュリティ モデルをサポートしています。 このモデルでは、コードのメタデータに指定された証拠に基づいてアセンブリに権限が付与されます。 SQL Server のユーザーベースのセキュリティ モデルは、SQL Server により CLR のコード アクセスベースのセキュリティ モデルと統合されます。  
  
## <a name="external-resources"></a>外部リソース  

 SQL Server と CLR の統合の詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[コード アクセス セキュリティ](../../../misc/code-access-security.md)|.NET Framework の CAS について説明します。|  
|[CLR 統合のセキュリティ](/sql/relational-databases/clr-integration/security/clr-integration-security)|SQL Server の内部で実行されるマネージド コードのセキュリティ モデルについて説明します。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET アプリケーションのセキュリティ保護](../securing-ado-net-applications.md)
- [SQL Server におけるアプリケーション セキュリティのシナリオ](application-security-scenarios-in-sql-server.md)
- [SQL Server の共通言語ランタイム統合](sql-server-common-language-runtime-integration.md)
- [ADO.NET の概要](../ado-net-overview.md)
