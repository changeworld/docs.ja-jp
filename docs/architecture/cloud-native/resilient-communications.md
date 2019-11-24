---
title: 回復性のある通信
description: Azure 向けのクラウドネイティブ .NET アプリの設計 |回復力のある通信
ms.date: 06/30/2019
ms.openlocfilehash: 324f5426af1c892db73aa6fc2336a19b7a8e499e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "73841223"
---
# <a name="resilient-communications"></a><span data-ttu-id="873bd-103">回復力のある通信</span><span class="sxs-lookup"><span data-stu-id="873bd-103">Resilient communications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="873bd-104">この本では、従来のモノリシックアプリケーション設計を超えて移行し、一連の分散された自己完結型サービスが独立して実行され、それぞれと通信するマイクロサービスベースのアーキテクチャを採用することのメリットを evangelized しました。HTTP や HTTPS などの標準の通信プロトコルを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="873bd-104">Throughout this book, we've evangelized the merits of moving beyond traditional monolithic application design and embracing a microservice-based architecture where a set of distributed, self-contained services run independently and communicate with each other using standard communication protocols such as HTTP and HTTPS.</span></span> <span data-ttu-id="873bd-105">このようなアーキテクチャには、多くの重要な利点がありますが、多くの課題があります。</span><span class="sxs-lookup"><span data-stu-id="873bd-105">While such an architecture buys you many important benefits, it also presents many challenges.</span></span> <span data-ttu-id="873bd-106">たとえば、次のような懸念事項が考えられます。</span><span class="sxs-lookup"><span data-stu-id="873bd-106">Consider, for example, the following concerns:</span></span>

- <span data-ttu-id="873bd-107">*プロセス外のネットワーク通信。*</span><span class="sxs-lookup"><span data-stu-id="873bd-107">*Out-of-process network communication.*</span></span> <span data-ttu-id="873bd-108">各サービスは、ネットワークの輻輳、待機時間、および一時的な障害が発生するネットワークプロトコルを介して通信します。</span><span class="sxs-lookup"><span data-stu-id="873bd-108">Each service communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>
- <span data-ttu-id="873bd-109">*サービスの検出。*</span><span class="sxs-lookup"><span data-stu-id="873bd-109">*Service discovery.*</span></span> <span data-ttu-id="873bd-110">各サービスがそれぞれ独自の IP アドレスとポートを持つマシンのクラスターで実行されている場合、サービスはどのようにして互いを検出して通信しますか。</span><span class="sxs-lookup"><span data-stu-id="873bd-110">With each service running across a cluster of machines with its own IP address and port, how do services discover and communicate with each other?</span></span>
- <span data-ttu-id="873bd-111">*柔軟性.*</span><span class="sxs-lookup"><span data-stu-id="873bd-111">*Resiliency.*</span></span> <span data-ttu-id="873bd-112">短時間の障害を管理し、システムの安定性を維持するにはどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="873bd-112">How do you manage short-lived failures and keep the system stable?</span></span>
- <span data-ttu-id="873bd-113">*負荷分散。*</span><span class="sxs-lookup"><span data-stu-id="873bd-113">*Load balancing.*</span></span> <span data-ttu-id="873bd-114">受信トラフィックは、サービスの複数のインスタンスにどのように分散されるのですか。</span><span class="sxs-lookup"><span data-stu-id="873bd-114">How does inbound traffic get distributed across multiple instances of a service?</span></span>
- <span data-ttu-id="873bd-115">*セキュリティ。*</span><span class="sxs-lookup"><span data-stu-id="873bd-115">*Security.*</span></span> <span data-ttu-id="873bd-116">トランスポートレベルの暗号化と証明書の管理などのセキュリティの問題はどのように適用されますか。</span><span class="sxs-lookup"><span data-stu-id="873bd-116">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>
- <span data-ttu-id="873bd-117">*分散型監視。*</span><span class="sxs-lookup"><span data-stu-id="873bd-117">*Distributed Monitoring.*</span></span> <span data-ttu-id="873bd-118">-複数の使用サービスにわたる1つの要求について、追跡可能性と監視を相互に関連付けてキャプチャする方法を教えてください。</span><span class="sxs-lookup"><span data-stu-id="873bd-118">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming services?</span></span>

<span data-ttu-id="873bd-119">これらの問題はさまざまなライブラリやフレームワークで対処できますが、コードベース内に実装すると、コストが高く複雑で時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="873bd-119">While these concerns can be addressed with various libraries and frameworks, implementing them inside your codebase can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="873bd-120">さらに、インフラストラクチャに関する懸念事項がビジネスロジックと関連付けられているソリューションもあります。</span><span class="sxs-lookup"><span data-stu-id="873bd-120">Moreover, you end up with a solution where infrastructure concerns are coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="873bd-121">サービスメッシュ</span><span class="sxs-lookup"><span data-stu-id="873bd-121">Service mesh</span></span>

<span data-ttu-id="873bd-122">より優れたアプローチは、*サービスメッシュ*の対象となる、急速に進化する新しいテクノロジを検討することです。</span><span class="sxs-lookup"><span data-stu-id="873bd-122">A better approach is to consider a new and rapidly evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="873bd-123">[サービスメッシュ](https://www.nginx.com/blog/what-is-a-service-mesh/)は、構成可能なインフラストラクチャレイヤーであり、サービス通信や前述の多くの課題を処理するための組み込みの機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="873bd-123">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and many of the challenges mentioned above.</span></span> <span data-ttu-id="873bd-124">これらの懸念事項をビジネスコードから切り離し、サービスプロキシ (各サービスに付随するのインスタンス) に移動します。</span><span class="sxs-lookup"><span data-stu-id="873bd-124">It decouples these concerns from your business code and moves them into a service proxy, an instance of which accompanies each of your services.</span></span> <span data-ttu-id="873bd-125">サービスメッシュプロキシは、サイドカー[パターン](https://docs.microsoft.com/azure/architecture/patterns/sidecar)とも呼ばれ、ビジネスコードから分離とカプセル化を行うための個別のプロセスにデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="873bd-125">Often referred to as the [Sidecar pattern](https://docs.microsoft.com/azure/architecture/patterns/sidecar), the service mesh proxy is deployed into a separate process to provide isolation and encapsulation from your business code.</span></span> <span data-ttu-id="873bd-126">ただし、プロキシは、それと共に作成されるサービスと、そのライフサイクルを共有するサービスに密接にリンクされています。</span><span class="sxs-lookup"><span data-stu-id="873bd-126">However, the proxy is closely linked to the service being created along with it and sharing its lifecycle.</span></span> <span data-ttu-id="873bd-127">図6-9 はこのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="873bd-127">Figure 6-9 shows this scenario.</span></span>

![サイドカーを使用したサービスメッシュ](./media/service-mesh-with-side-car.png)

<span data-ttu-id="873bd-129">**図 6-9**。</span><span class="sxs-lookup"><span data-stu-id="873bd-129">**Figure 6-9**.</span></span> <span data-ttu-id="873bd-130">サイドカーを使用したサービスメッシュ</span><span class="sxs-lookup"><span data-stu-id="873bd-130">Service mesh with a side car</span></span>

<span data-ttu-id="873bd-131">前の図では、プロキシがマイクロサービスとクラスター間の通信を傍受して管理する方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="873bd-131">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="873bd-132">サービスメッシュは、[データプレーン](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)と[コントロールプレーン](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)の2つの異なるコンポーネントに論理的に分割されます。</span><span class="sxs-lookup"><span data-stu-id="873bd-132">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="873bd-133">図6-10 は、これらのコンポーネントとその役割を示しています。</span><span class="sxs-lookup"><span data-stu-id="873bd-133">Figure 6-10 shows these components and their responsibilities.</span></span>

![サービスメッシュ制御とデータプレーン](./media/istio-control-and-data-plane.png)

<span data-ttu-id="873bd-135">**図 6-10.**</span><span class="sxs-lookup"><span data-stu-id="873bd-135">**Figure 6-10.**</span></span> <span data-ttu-id="873bd-136">サービスメッシュ制御とデータプレーン</span><span class="sxs-lookup"><span data-stu-id="873bd-136">Service mesh control and data plane</span></span>

<span data-ttu-id="873bd-137">構成が完了すると、サービスメッシュが非常に機能します。</span><span class="sxs-lookup"><span data-stu-id="873bd-137">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="873bd-138">サービス探索エンドポイントから、対応するインスタンスのプールを取得できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-138">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="873bd-139">その後、特定のインスタンスに要求を送信し、結果の待機時間と応答の種類を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="873bd-139">It can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="873bd-140">メッシュでは、最近の要求の待機時間など、多くの要因に基づいて高速な応答を返す可能性の高いインスタンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-140">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="873bd-141">インスタンスが応答しない場合、または失敗した場合、メッシュは別のインスタンスで要求を再試行できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-141">If an instance is unresponsive or fails, the mesh can retry the request on another instance.</span></span> <span data-ttu-id="873bd-142">プールが一貫してエラーを返す場合、メッシュは負荷分散プールからそれを削除して、回復後に定期的に再試行することができます。</span><span class="sxs-lookup"><span data-stu-id="873bd-142">If a pool consistently returns errors, a mesh can evict it from the load-balancing pool to be retried periodically later after it heals.</span></span> <span data-ttu-id="873bd-143">要求がタイムアウトになると、メッシュが失敗し、要求を再試行することができます。</span><span class="sxs-lookup"><span data-stu-id="873bd-143">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="873bd-144">メッシュは、メトリックと分散トレースの形式で動作をキャプチャします。これは、一元化されたメトリックシステムに出力できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-144">A mesh captures behavior in the form of metrics and distributed tracing, which then can be emitted to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="873bd-145">Iとエンボイ</span><span class="sxs-lookup"><span data-stu-id="873bd-145">Istio and Envoy</span></span>

<span data-ttu-id="873bd-146">現在、いくつかのサービスメッシュオプションが存在しますが、このドキュメントの執筆時点では、 [iと](https://istio.io/docs/concepts/what-is-istio/)して最も人気があります。</span><span class="sxs-lookup"><span data-stu-id="873bd-146">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular as of the time of this writing.</span></span> <span data-ttu-id="873bd-147">新しいまたは既存の分散アプリケーションに統合できるオープンソースのサービスであり、IBM、Google、およびその他のサービスとの共同事業です。</span><span class="sxs-lookup"><span data-stu-id="873bd-147">A joint venture from IBM, Google, and Lyft, it's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="873bd-148">マイクロサービスをセキュリティで保護、接続、監視するための一貫した完全なソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="873bd-148">It provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="873bd-149">その特徴は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="873bd-149">Its features include:</span></span>

- <span data-ttu-id="873bd-150">強力な id ベースの認証と承認を使用して、クラスター内のサービス間通信をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="873bd-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="873bd-151">HTTP、 [Grpc](https://grpc.io/)、WEBSOCKET、TCP トラフィックの自動負荷分散。</span><span class="sxs-lookup"><span data-stu-id="873bd-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="873bd-152">豊富なルーティング規則、再試行、フェールオーバー、およびフォールトインジェクションにより、トラフィックの動作をきめ細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="873bd-153">アクセス制御、レート制限、クォータをサポートするプラグ可能なポリシーレイヤーと構成 API。</span><span class="sxs-lookup"><span data-stu-id="873bd-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="873bd-154">クラスター内のすべてのトラフィック (クラスターの受信と送信を含む) の自動メトリック、ログ、およびトレース。</span><span class="sxs-lookup"><span data-stu-id="873bd-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="873bd-155">Iの実装の主要なコンポーネントは、[エンボイプロキシ](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)を持つプロキシサービスです。</span><span class="sxs-lookup"><span data-stu-id="873bd-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="873bd-156">この後、1つの章で説明されているように、後から[クラウドネイティブコンピューティングファンデーション](https://www.cncf.io/)に貢献すると、エンボイプロキシは各サービスと共に実行され、次の機能のためのプラットフォームに依存しない基礎となります。</span><span class="sxs-lookup"><span data-stu-id="873bd-156">Originating from Lyft and subsequently contributed to the [Cloud Native Computing Foundation](https://www.cncf.io/) (discussed in chapter 1), the Envoy proxy runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="873bd-157">動的サービスの検出。</span><span class="sxs-lookup"><span data-stu-id="873bd-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="873bd-158">負荷分散。</span><span class="sxs-lookup"><span data-stu-id="873bd-158">Load balancing.</span></span>
- <span data-ttu-id="873bd-159">TLS の終了。</span><span class="sxs-lookup"><span data-stu-id="873bd-159">TLS termination.</span></span>
- <span data-ttu-id="873bd-160">HTTP および gRPC プロキシ。</span><span class="sxs-lookup"><span data-stu-id="873bd-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="873bd-161">サーキットブレーカーの回復性。</span><span class="sxs-lookup"><span data-stu-id="873bd-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="873bd-162">正常性チェック。</span><span class="sxs-lookup"><span data-stu-id="873bd-162">Health checks.</span></span>
- <span data-ttu-id="873bd-163">[カナリア](https://martinfowler.com/bliki/CanaryRelease.html)デプロイによる更新のローリング。</span><span class="sxs-lookup"><span data-stu-id="873bd-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="873bd-164">既に説明したように、エンボイはクラスター内の各マイクロサービスにサイドカーとしてデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="873bd-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="873bd-165">Azure Kubernetes Services との統合</span><span class="sxs-lookup"><span data-stu-id="873bd-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="873bd-166">Azure クラウドは、azure Kubernetes Services 内での直接サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="873bd-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="873bd-167">次のリンクを使用して作業を開始できます。</span><span class="sxs-lookup"><span data-stu-id="873bd-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="873bd-168">AKS での Ip のインストール</span><span class="sxs-lookup"><span data-stu-id="873bd-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="873bd-169">AKS と Iを使用する</span><span class="sxs-lookup"><span data-stu-id="873bd-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

>[!div class="step-by-step"]
><span data-ttu-id="873bd-170">[前へ](infrastructure-resiliency-azure.md)
>[次へ](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="873bd-170">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>