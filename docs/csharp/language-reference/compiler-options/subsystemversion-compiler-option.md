---
description: -subsystemversion (C# コンパイラ オプション)
title: -subsystemversion (C# コンパイラ オプション)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: e8001d8db214123e75fec4e1d1117ef90a9df606
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128596"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (C# コンパイラ オプション)

生成された実行可能ファイルが動作できるサブシステムの最小バージョンを指定します。これにより、実行可能ファイルが動作できる Windows のバージョンが決まります。 通常、このオプションを指定することで、実行可能ファイルが、Windows の以前のバージョンでは使用できない特定のセキュリティ機能を利用できるようになります。

> [!NOTE]
> サブシステム自体を指定するには、[-target](./target-compiler-option.md) のコンパイラ オプションを使用します。

## <a name="syntax"></a>構文

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>パラメーター

`major.minor`

サブシステムに必要な最小バージョン。メジャー バージョンおよびマイナー バージョンのドット表記で表されます。 たとえば、このオプションの値を 6.01 に設定すると、Windows 7 より古いオペレーティング システムではアプリケーションを実行できないように指定できます (このトピックの以下の表を参照)。 `major` と `minor` の値を整数で指定する必要があります。

`minor` バージョンでは、前に配置されるゼロによってバージョンが変更されることはありませんが、後ろにゼロが付くとバージョンが変わります。 たとえば、6.1 と 6.01 は同じバージョンを示しますが、6.10 は異なるバージョンを示します。 混乱を避けるため、マイナー バージョンには 2 桁の数値を使用することをお勧めします。

## <a name="remarks"></a>Remarks

次の表は、Windows の一般的なサブシステムのバージョンを示しています。

|Windows のバージョン|サブシステムのバージョン|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>既定の値

**-subsystemversion** コンパイラ オプションの既定値は条件によって異なります。その条件を次に示します。

- 次のコンパイラ オプションのいずれかが設定されている場合、既定値は 6.02 です。

  - [/target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [/target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platform:arm](./platform-compiler-option.md)

- MSBuild を使用しており、.NET Framework 4.5 が対象で、さらにこの一覧で前に指定したコンパイラ オプションを設定していない場合、既定値は 6.00 です。

- 上記の条件がどれも当てはまらない場合、既定値は 4.00 です。

## <a name="setting-this-option"></a>このオプションを設定する

Visual Studio で **-subsystemversion** コンパイラ オプションを設定するには、.csproj ファイルを開き、MSBuild XML で `SubsystemVersion` プロパティの値を指定する必要があります。 Visual Studio IDE でこのオプションを設定することはできません。 詳細については、このトピックの「既定値」または「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# コンパイラ オプション](./index.md)
