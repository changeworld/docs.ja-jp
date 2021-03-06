---
title: Windows、Linux、および macOS にインストールされた .NET バージョンを確認する - .NET
description: コンピューターにインストールされている .NET のバージョンを一覧表示する方法について説明します。 これには .NET ランタイムと SDK が含まれます。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2fc12c8c398b1a74d623e53884df666f4d4b85f1
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851615"
---
# <a name="how-to-check-that-net-is-already-installed"></a>.NET が既にインストールされていることを確認する方法

この記事では、コンピューターにインストールされている .NET ランタイムおよび SDK のバージョンを確認する方法について説明します。 Visual Studio や Visual Studio for Mac などの統合開発環境を使用している場合は、.NET が既にインストールされている可能性があります。

SDK をインストールすると、対応するランタイムがインストールされます。

この記事のいずれかのコマンドが失敗した場合は、ランタイムまたは SDK がインストールされていません。 詳細については、[Windows](windows.md)、[macOS](macos.md)、または [Linux](linux.md) のインストールに関する記事を参照してください。

## <a name="check-sdk-versions"></a>SDK バージョンを確認する

現在インストールされている .NET SDK のバージョンをターミナルで確認できます。 ターミナルを開き、次のコマンドを実行します。

```dotnetcli
dotnet --list-sdks
```

次のような出力が得られます。

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a>ランタイムのバージョンを確認する

次のコマンドで、現在インストールされている .NET ランタイムのバージョンを確認できます。

```dotnetcli
dotnet --list-runtimes
```

次のような出力が得られます。

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a>インストール フォルダーを確認する

.NET がインストールされていても、オペレーティング システムまたはユーザー プロファイルの `PATH` 変数に追加されていない可能性があります。 この場合、前のセクションのコマンドが機能しない場合があります。 別の方法として、.NET のインストール フォルダーが存在することを確認できます。

インストーラーまたはスクリプトから .NET をインストールすると、標準のフォルダーにインストールされます。 通常、.NET のインストールに使用するインストーラーまたはスクリプトには、別のフォルダーにインストールするためのオプションがあります。 別のフォルダーにインストールする場合は、フォルダー パスの先頭を調整します。

::: zone pivot="os-windows"

- **dotnet 実行可能ファイル**\
_C:\\program files\\dotnet\\dotnet.exe_

- **.NET SDK**\
_C:\\program files\\dotnet\\sdk\\<バージョン>\\_

- **.NET ランタイム**\
_C:\\program files\\dotnet\\shared\\<ランタイムの種類>\\<バージョン>\\_

::: zone-end

::: zone pivot="os-linux"

- **dotnet 実行可能ファイル**\
_/home/user/share/dotnet/dotnet_

- **.NET SDK**\
_/home/user/share/dotnet/sdk/<バージョン>/_

- **.NET ランタイム**\
_/home/user/share/dotnet/shared/<ランタイムの種類>/<バージョン>/_

::: zone-end

::: zone pivot="os-macos"

- **dotnet 実行可能ファイル**\
_/usr/local/share/dotnet/dotnet_

- **.NET SDK**\
_/usr/local/share/dotnet/sdk/<バージョン>/_

- **.NET ランタイム**\
_/usr/local/share/dotnet/shared/<ランタイムの種類>/<バージョン>/_

::: zone-end

## <a name="more-information"></a>詳細情報

コマンド `dotnet --info` を使用すると、SDK バージョンとランタイム バージョンの両方を確認できます。 また、オペレーティング システムのバージョンやランタイム識別子 (RID) など、その他の環境に関連する情報も取得されます。

## <a name="next-steps"></a>次の手順

- [Windows 用の .NET ランタイムと SDK をインストールする](windows.md)。
- [macOS 用の .NET ランタイムと SDK をインストールする](macos.md)。
- [Linux 用の .NET ランタイムと SDK をインストールする](linux.md)。

## <a name="see-also"></a>関連項目

- [インストールされている .NET Framework バージョンを確認する](../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)
