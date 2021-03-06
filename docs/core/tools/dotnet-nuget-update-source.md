---
title: dotnet nuget update source コマンド
description: dotnet nuget update source コマンドを使うと、NuGet 構成ファイルの既存のソースを更新できます。
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537855"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**この記事の対象:** ✔️ .NET Core 3.1.200 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet nuget update source` - NuGet ソースを更新します。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>説明

`dotnet nuget update source` コマンドを使うと、NuGet 構成ファイルの既存のソースを更新できます。

## <a name="arguments"></a>引数

- **`NAME`**

  ソースの名前。

## <a name="options"></a>オプション

- **`--configfile <FILE>`**

  NuGet 構成ファイル。 指定した場合、このファイルの設定のみが使用されます。 指定しない場合、現在のディレクトリからの構成ファイルの階層が使用されます。 詳細については、「[一般的な NuGet 構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。

- **`-p|--password <PASSWORD>`**

  認証済みソースに接続するときに使用するパスワード。

- **`-s|--source <SOURCE>`**

  パッケージ ソースへのパス。

- **`--store-password-in-clear-text`**

  パスワードの暗号化を無効にすることで、ポータブル パッケージ ソースの資格情報を保存できるようにします。

- **`-u|--username <USER>`**

  認証済みソースに接続するときに使用するユーザー名。

- **`--valid-authentication-types <TYPES>`**

  このソースに対して有効な認証の種類のコンマ区切りのリスト。 サーバーによって NTLM または Negotiate がアドバタイズされていて、基本メカニズムを使用して資格情報を送信する必要がある場合は、これを `basic` に設定します。たとえば、オンプレミスの Azure DevOps Server で PAT を使用する場合などです。 その他の有効な値には、`negotiate`、`kerberos`、`ntlm`、`digest` などがありますが、これらの値は役に立たない可能性があります。

## <a name="examples"></a>使用例

- `mySource` という名前のソースを更新します。

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>関連項目

- [NuGet.config ファイルのパッケージ ソース セクション](/nuget/reference/nuget-config-file#package-source-sections)

- [sources コマンド (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
