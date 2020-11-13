---
ms.openlocfilehash: 2599e1f65720c25695f1fb5cfa39cabb842efc1d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888626"
---
### <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a><span data-ttu-id="444a1-101">TripleDES.Create で作成されるインスタンスの既定の FeedbackSize 値の変更</span><span class="sxs-lookup"><span data-stu-id="444a1-101">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>

<span data-ttu-id="444a1-102"><xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> から返される <xref:System.Security.Cryptography.TripleDES> インスタンスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> プロパティの既定値が 64 から 8 に変更され、.NET Framework からの移行がより簡単になりました。</span><span class="sxs-lookup"><span data-stu-id="444a1-102">The default value for the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType> property on the <xref:System.Security.Cryptography.TripleDES> instance returned from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> has changed from 64 to 8 to make migration from .NET Framework easier.</span></span> <span data-ttu-id="444a1-103">このプロパティは、呼び出し元のコードで直接使用されていない限り、<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> プロパティが <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="444a1-103">This property, unless used directly in caller code, is used only when the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property is <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="444a1-104"><xref:System.Security.Cryptography.CipherMode.CFB> モードのサポートは最初に 5.0 RC1 リリース用の .NET に追加されたため、この変更の影響を受けるのは .NET 5.0 RC1 および .NET 5.0 RC2 アプリケーションのみであるはずです。</span><span class="sxs-lookup"><span data-stu-id="444a1-104">Support for the <xref:System.Security.Cryptography.CipherMode.CFB> mode was first added to .NET for the 5.0 RC1 release, so only .NET 5.0 RC1 and .NET 5.0 RC2 applications should be impacted by this change.</span></span>

#### <a name="change-description"></a><span data-ttu-id="444a1-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="444a1-105">Change description</span></span>

<span data-ttu-id="444a1-106">.Net Core と以前のプレリリース バージョンの .NET 5.0 では、`TripleDES.Create().FeedbackSize` の既定値は 64 です。</span><span class="sxs-lookup"><span data-stu-id="444a1-106">In .NET Core and previous pre-release versions of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 64.</span></span> <span data-ttu-id="444a1-107">RTM バージョンの .NET 5.0 以降では、`TripleDES.Create().FeedbackSize` の既定値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="444a1-107">Starting in the RTM version of .NET 5.0, `TripleDES.Create().FeedbackSize` has a default value of 8.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="444a1-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="444a1-108">Reason for change</span></span>

<span data-ttu-id="444a1-109">.NET Framework によって、<xref:System.Security.Cryptography.TripleDES> 基底クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> の値は既定で 64 に設定されますが、<xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> クラスの既定値は 8 に上書きされます。</span><span class="sxs-lookup"><span data-stu-id="444a1-109">In .NET Framework, the <xref:System.Security.Cryptography.TripleDES> base class defaults the value of <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> to 64, but the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class overwrites the default to 8.</span></span> <span data-ttu-id="444a1-110">バージョン 2.0 で <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティが .NET Core に導入されたときに、同じ動作が維持されました。</span><span class="sxs-lookup"><span data-stu-id="444a1-110">When the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property was introduced to .NET Core in version 2.0, this same behavior was preserved.</span></span> <span data-ttu-id="444a1-111">しかし、.NET Framework では、<xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> から <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> のインスタンスが返されるため、アルゴリズム ファクトリの既定値は 8 となります。</span><span class="sxs-lookup"><span data-stu-id="444a1-111">However, in .NET Framework, <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> returns an instance of <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>, so the default value from the algorithm factory is 8.</span></span> <span data-ttu-id="444a1-112">.NET Core および .NET 5 以降の場合、アルゴリズム ファクトリからパブリックではない実装が返されます。これまで、その既定値は 64 でした。</span><span class="sxs-lookup"><span data-stu-id="444a1-112">For .NET Core and .NET 5+, the algorithm factory returns a non-public implementation, which, until now, had a default value of 64.</span></span>

<span data-ttu-id="444a1-113"><xref:System.Security.Cryptography.TripleDES> 実装クラスの <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> の値を 8 に変更すると、暗号モードを <xref:System.Security.Cryptography.CipherMode.CFB> として指定していても、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティを明示的に代入していない .NET Framework 用に作成されたアプリケーションは、引き続き .NET 5 で機能できます。</span><span class="sxs-lookup"><span data-stu-id="444a1-113">Changing the <xref:System.Security.Cryptography.TripleDES> implementation class' <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> value to 8 allows for applications written for .NET Framework that specified the cipher mode as <xref:System.Security.Cryptography.CipherMode.CFB> but didn't explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property, to continue to function on .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="444a1-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="444a1-114">Version introduced</span></span>

<span data-ttu-id="444a1-115">5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="444a1-115">5.0 RTM</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="444a1-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="444a1-116">Recommended action</span></span>

<span data-ttu-id="444a1-117">RC1 または RC2 バージョンの .NET 5.0 でデータの暗号化またはその解除を行うアプリケーションにより、次の条件が満たされたときに CFB64 を使用して操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="444a1-117">Applications that encrypt or decrypt data in the RC1 or RC2 versions of .NET 5.0 do so with CFB64, when the following conditions are met:</span></span>

- <span data-ttu-id="444a1-118"><xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> の <xref:System.Security.Cryptography.TripleDES> インスタンスを使用する。</span><span class="sxs-lookup"><span data-stu-id="444a1-118">With a <xref:System.Security.Cryptography.TripleDES> instance from <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="444a1-119"><xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> に既定値を使用する。</span><span class="sxs-lookup"><span data-stu-id="444a1-119">Using the default value for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span>
- <span data-ttu-id="444a1-120"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> プロパティが <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> に設定されている。</span><span class="sxs-lookup"><span data-stu-id="444a1-120">With the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> property set to <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="444a1-121">この動作を維持するには、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティを `64` に代入します。</span><span class="sxs-lookup"><span data-stu-id="444a1-121">To maintain this behavior, assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property to `64`.</span></span>

<span data-ttu-id="444a1-122">すべての `TripleDES` 実装で、<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> に同じ既定値が使用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="444a1-122">Not all `TripleDES` implementations use the same default for <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize>.</span></span> <span data-ttu-id="444a1-123"><xref:System.Security.Cryptography.TripleDES> インスタンスで <xref:System.Security.Cryptography.CipherMode.CFB> 暗号モードを使用する場合は、常に <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> プロパティ値を明示的に代入することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="444a1-123">We recommend that if you use the <xref:System.Security.Cryptography.CipherMode.CFB> cipher mode on <xref:System.Security.Cryptography.TripleDES> instances, you should always explicitly assign the <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> property value.</span></span>

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

#### <a name="category"></a><span data-ttu-id="444a1-124">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="444a1-124">Category</span></span>

- <span data-ttu-id="444a1-125">暗号</span><span class="sxs-lookup"><span data-stu-id="444a1-125">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="444a1-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="444a1-126">Affected APIs</span></span>

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

-->