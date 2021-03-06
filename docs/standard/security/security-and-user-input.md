---
title: セキュリティとユーザー入力
description: コードでは、ユーザーが入力したデータをパラメーターとして他のコードに渡すことがあり、これはセキュリティに影響を与える可能性があります。 範囲チェックを実行して、問題のある入力を拒否することができます。
ms.date: 07/15/2020
helpviewer_keywords:
- security [.NET], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: e476db90dd1fd579f4ecfe3f2088cc76c955b9c0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824058"
---
# <a name="security-and-user-input"></a>セキュリティとユーザー入力

ユーザー データにはあらゆる種類の入力 (Web 要求または URL からのデータや、Microsoft Windows Forms アプリケーションのコントロールへの入力など) がありますが、これはコードに悪影響を及ぼすことがあります。このようなデータはパラメーターとして直接使用され、他のコードを呼び出す場合が多いためです。 この状況は、悪意のあるコードが不明なパラメーターを使用してコードを呼び出すことと似ており、同じ予防策をとる必要があります。 実際には、ユーザー入力の安全性を保つ方が困難です。潜在的に信頼されていないデータの存在をトレースするスタック フレームがないためです。

これらは最も微小で見つけにくいセキュリティ バグです。セキュリティとは無関係に見えるコードに存在すことができ、他のコードに悪いデータを送り出すゲートウェイだからです。 このようなバグを探し出すには、あらゆる種類の入力データを追跡し、可能性のある値の範囲を想像し、そのデータを扱うコードがすべてのケースを処理できるかどうかを検討します。 これらのバグは、範囲チェックを使用して、コードで処理できない入力を拒否することで修正できます。

ユーザー データに関連する重要な注意事項を次に示します。

- サーバー応答内のすべてのユーザー データは、クライアント上でサーバーのサイトのコンテキストで実行されます。 Web サーバーがユーザーデータを取得し、返された Web ページに挿入する場合、たとえば、タグを含め、 **\<script>** サーバーからのように実行します。

- クライアントはすべての URL を要求できることに注意してください。

- 巧妙なパスまたは無効なパスに注意してください。

  - ..\、極端に長いパス。

  - ワイルドカード文字 (*) の使用。

  - トークンの展開 (%token%)。

  - 特別な意味を持つ変わった形式のパス。

  - 代替ファイル システム ストリーム名、`filename::$DATA` など。

  - ファイル名の短縮バージョン、`longfilename`に対して `longfi~1` など。

- Eval(userdata) は何でも実行できることに注意してください。

- ユーザー データを含む名前の遅延バインディングを警戒してください。

- Web データを扱う場合は、許容されるさまざまな形式のエスケープを検討してください。

  - 16 進数エスケープ (%nn)。

  - Unicode エスケープ (%nnn)。

  - オーバーロング UTF-8 エスケープ (%nn%nn)。

  - ダブル エスケープ (%nn が %mmnn になります。%mm は '%' のエスケープです)。

- 標準形式が複数あるユーザー名に注意してください。 たとえば、よく使用するのは MYDOMAIN\\*username* 形式または *username*@mydomain.example.com 形式です。

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](secure-coding-guidelines.md)
- [ASP.NET Core のセキュリティ](/aspnet/core/security/)
