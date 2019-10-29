---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394167"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="e3ebd-101">SignalR: UseSignalR および UseConnections メソッドが古いものとしてマークされた</span><span class="sxs-lookup"><span data-stu-id="e3ebd-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="e3ebd-102">メソッド `UseConnections` と `UseSignalR` およびクラス `ConnectionsRouteBuilder` と `HubRouteBuilder` は、ASP.NET Core 3.0 では古いものとマークされています。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e3ebd-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e3ebd-103">Version introduced</span></span>

<span data-ttu-id="e3ebd-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e3ebd-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e3ebd-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="e3ebd-105">Old behavior</span></span>

<span data-ttu-id="e3ebd-106">SignalR ハブ ルーティングは、`UseSignalR` または `UseConnections` を使用して構成されました。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e3ebd-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="e3ebd-107">New behavior</span></span>

<span data-ttu-id="e3ebd-108">ルーティングを構成する従来の方法は古くなり、エンドポイント ルーティングに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e3ebd-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="e3ebd-109">Reason for change</span></span>

<span data-ttu-id="e3ebd-110">ミドルウェアは、新しいエンドポイント ルーティング システムに移行されています。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="e3ebd-111">ミドルウェアを追加する以前の方法は、古くなっています。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e3ebd-112">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="e3ebd-112">Recommended action</span></span>

<span data-ttu-id="e3ebd-113">`UseSignalR` を `UseEndpoints` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e3ebd-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="e3ebd-114">**古いコード:**</span><span class="sxs-lookup"><span data-stu-id="e3ebd-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="e3ebd-115">**新しいコード:**</span><span class="sxs-lookup"><span data-stu-id="e3ebd-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="e3ebd-116">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="e3ebd-116">Category</span></span>

<span data-ttu-id="e3ebd-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e3ebd-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3ebd-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e3ebd-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->