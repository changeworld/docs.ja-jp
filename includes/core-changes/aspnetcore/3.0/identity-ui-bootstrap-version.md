---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394133"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="354e7-101">ID: UI の既定の Bootstrap のバージョンが変更された</span><span class="sxs-lookup"><span data-stu-id="354e7-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="354e7-102">ASP.NET Core 3.0 以降、ID UI では既定で Bootstrap のバージョン 4 が使用されています。</span><span class="sxs-lookup"><span data-stu-id="354e7-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="354e7-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="354e7-103">Version introduced</span></span>

<span data-ttu-id="354e7-104">3.0</span><span class="sxs-lookup"><span data-stu-id="354e7-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="354e7-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="354e7-105">Old behavior</span></span>

<span data-ttu-id="354e7-106">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` メソッドの呼び出しは `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);` と同じでした</span><span class="sxs-lookup"><span data-stu-id="354e7-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="354e7-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="354e7-107">New behavior</span></span>

<span data-ttu-id="354e7-108">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` メソッドの呼び出しは `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);` と同じです</span><span class="sxs-lookup"><span data-stu-id="354e7-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="354e7-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="354e7-109">Reason for change</span></span>

<span data-ttu-id="354e7-110">Bootstrap 4 は ASP.NET Core 3.0 の期間中にリリースされました。</span><span class="sxs-lookup"><span data-stu-id="354e7-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="354e7-111">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="354e7-111">Recommended action</span></span>

<span data-ttu-id="354e7-112">既定の ID UI を使用し、次の例に示すように `Startup.ConfigureServices` にそれを追加している場合、この変更による影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="354e7-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="354e7-113">次のいずれかのアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="354e7-113">Take one of the following actions:</span></span>

- <span data-ttu-id="354e7-114">[移行ガイド](https://getbootstrap.com/docs/4.0/migration)を使用して、Bootstrap 4 を使用するようにアプリを移行します。</span><span class="sxs-lookup"><span data-stu-id="354e7-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="354e7-115">Bootstrap 3 の使用を強制するように、`Startup.ConfigureServices` を更新します。</span><span class="sxs-lookup"><span data-stu-id="354e7-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="354e7-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="354e7-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="354e7-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="354e7-117">Category</span></span>

<span data-ttu-id="354e7-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="354e7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="354e7-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="354e7-119">Affected APIs</span></span>

<span data-ttu-id="354e7-120">なし</span><span class="sxs-lookup"><span data-stu-id="354e7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->