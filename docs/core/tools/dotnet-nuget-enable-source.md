---
title: dotnet nuget enable source コマンド
description: dotnet nuget enable source コマンドを使うと、NuGet 構成ファイルの既存のソースを有効にできます。
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537935"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget enable source

**この記事の対象:** ✔️ .NET Core 3.1.200 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet nuget enable source` - NuGet ソースを有効にします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a>説明

`dotnet nuget enable source` コマンドを使うと、NuGet 構成ファイルの既存のソースを有効にできます。

## <a name="arguments"></a>引数

- **`NAME`**

  ソースの名前。

## <a name="options"></a>オプション

- **`--configfile <FILE>`**

  NuGet 構成ファイル。 指定した場合、このファイルの設定のみが使用されます。 指定しない場合、現在のディレクトリからの構成ファイルの階層が使用されます。 詳細については、「[一般的な NuGet 構成](/nuget/consume-packages/configuring-nuget-behavior)」をご覧ください。

## <a name="examples"></a>使用例

- `mySource` という名前のソースを有効にします。

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>関連項目

- [NuGet.config ファイルのパッケージ ソース セクション](/nuget/reference/nuget-config-file#package-source-sections)

- [sources コマンド (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
