---
title: ページ、ルーティング、レイアウト
description: Blazor でページを作成する方法、クライアント側のルーティングを使用する方法、およびページレイアウトを管理する方法について説明します。
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: 693eee270a46ccb56ed5fef8fced1d4a1cf1974f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "73841235"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="806ba-103">ページ、ルーティング、レイアウト</span><span class="sxs-lookup"><span data-stu-id="806ba-103">Pages, routing, and layouts</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="806ba-104">ASP.NET Web フォームアプリは、 *.aspx*ファイルで定義されたページで構成されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="806ba-105">各ページのアドレスは、プロジェクトの物理ファイルパスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="806ba-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="806ba-106">ブラウザーがページに要求を行うと、ページの内容がサーバーに動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="806ba-107">ページの HTML マークアップとそのサーバーコントロールの両方に対する表示アカウント。</span><span class="sxs-lookup"><span data-stu-id="806ba-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="806ba-108">Blazor では、アプリの各ページは、通常、1つまたは複数の指定されたルートを使用して、razor ファイルで定義されているコンポーネントです *。*</span><span class="sxs-lookup"><span data-stu-id="806ba-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="806ba-109">ルーティングは、ほとんどの場合、特定のサーバー要求を介さずにクライアント側で行われます。</span><span class="sxs-lookup"><span data-stu-id="806ba-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="806ba-110">ブラウザーはまず、アプリのルートアドレスに要求を行います。</span><span class="sxs-lookup"><span data-stu-id="806ba-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="806ba-111">次に、Blazor アプリ内のルート `Router` コンポーネントが、受信ナビゲーション要求を処理し、正しいコンポーネントに処理します。</span><span class="sxs-lookup"><span data-stu-id="806ba-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="806ba-112">Blazor は*ディープリンク*もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="806ba-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="806ba-113">ディープリンクは、ブラウザーがアプリのルート以外の特定のルートに対して要求を行うときに発生します。</span><span class="sxs-lookup"><span data-stu-id="806ba-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="806ba-114">サーバーに送信されるディープリンクの要求は Blazor アプリにルーティングされ、その後、要求クライアント側が正しいコンポーネントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="806ba-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="806ba-115">ASP.NET Web フォームの単純なページには、次のマークアップが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="806ba-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="806ba-116">*名前 .aspx*</span><span class="sxs-lookup"><span data-stu-id="806ba-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="806ba-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="806ba-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="806ba-118">Blazor アプリの同等のページは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="806ba-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="806ba-119">*名前。 razor*</span><span class="sxs-lookup"><span data-stu-id="806ba-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="806ba-120">ページの作成</span><span class="sxs-lookup"><span data-stu-id="806ba-120">Create pages</span></span>

<span data-ttu-id="806ba-121">Blazor でページを作成するには、コンポーネントを作成し、コンポーネントのルートを指定するために `@page` Razor ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="806ba-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="806ba-122">`@page` ディレクティブは、そのコンポーネントに追加するルートテンプレートである1つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="806ba-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="806ba-123">ルートテンプレートパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="806ba-123">The route template parameter is required.</span></span> <span data-ttu-id="806ba-124">ASP.NET Web フォームとは異なり、Blazor コンポーネントへのルートはファイルの場所からは推論され*ません*(ただし、将来追加される機能である可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="806ba-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="806ba-125">ルートテンプレートの構文は、ASP.NET Web フォームでのルーティングに使用される基本構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="806ba-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="806ba-126">ルートパラメーターは、テンプレート内で中かっこを使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="806ba-127">Blazor は、ルート値を同じ名前のコンポーネントパラメーターにバインドします (大文字と小文字は区別されません)。</span><span class="sxs-lookup"><span data-stu-id="806ba-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="806ba-128">Route パラメーターの値に対して制約を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="806ba-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="806ba-129">たとえば、製品 ID を `int`に制限するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="806ba-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="806ba-130">Blazor でサポートされているルート制約の完全な一覧については、「[ルート制約](/aspnet/core/blazor/routing#route-constraints)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="806ba-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="806ba-131">ルーターコンポーネント</span><span class="sxs-lookup"><span data-stu-id="806ba-131">Router component</span></span>

<span data-ttu-id="806ba-132">Blazor でのルーティングは、`Router` コンポーネントによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="806ba-133">`Router` コンポーネントは、通常、アプリのルートコンポーネント (*app.xaml*) で使用されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="806ba-134">`Router` コンポーネントは、指定された `AppAssembly` とオプションで指定された `AdditionalAssemblies`内のルーティング可能なコンポーネントを検出します。</span><span class="sxs-lookup"><span data-stu-id="806ba-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="806ba-135">ブラウザーが移動すると、`Router` はナビゲーションをインターセプトし、展開された `RouteData` の `Found` パラメーターの内容を表示します。ルートがアドレスと一致する場合、`Router` はその `NotFound` パラメーターをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="806ba-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="806ba-136">`RouteView` コンポーネントは、`RouteData` によって指定された一致するコンポーネントがある場合、そのレイアウトを表示します。</span><span class="sxs-lookup"><span data-stu-id="806ba-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="806ba-137">一致したコンポーネントにレイアウトがない場合は、必要に応じて `DefaultLayout` を使用します。</span><span class="sxs-lookup"><span data-stu-id="806ba-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="806ba-138">`LayoutView` コンポーネントは、指定されたレイアウト内で子コンテンツをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="806ba-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="806ba-139">レイアウトについては、この章で後ほど詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="806ba-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="806ba-140">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="806ba-140">Navigation</span></span>

<span data-ttu-id="806ba-141">ASP.NET Web フォームでは、ブラウザーにリダイレクト応答を返すことによって、別のページへのナビゲーションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="806ba-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="806ba-142">例 :</span><span class="sxs-lookup"><span data-stu-id="806ba-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="806ba-143">Blazor では、通常、リダイレクト応答を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="806ba-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="806ba-144">Blazor は、要求/応答モデルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="806ba-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="806ba-145">ただし、JavaScript の場合と同様に、ブラウザーのナビゲーションを直接トリガーできます。</span><span class="sxs-lookup"><span data-stu-id="806ba-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="806ba-146">Blazor には、次のために使用できる `NavigationManager` サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="806ba-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="806ba-147">現在のブラウザーアドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="806ba-147">Get the current browser address</span></span>
- <span data-ttu-id="806ba-148">ベースアドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="806ba-148">Get the base address</span></span>
- <span data-ttu-id="806ba-149">ナビゲーションのトリガー</span><span class="sxs-lookup"><span data-stu-id="806ba-149">Trigger navigations</span></span>
- <span data-ttu-id="806ba-150">アドレスが変更されたときに通知を受け取る</span><span class="sxs-lookup"><span data-stu-id="806ba-150">Get notified when the address changes</span></span>

<span data-ttu-id="806ba-151">別のアドレスに移動するには、`NavigateTo` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="806ba-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="806ba-152">すべての `NavigationManager` メンバーの説明については、「 [URI およびナビゲーション状態ヘルパー](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="806ba-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="806ba-153">ベース Url</span><span class="sxs-lookup"><span data-stu-id="806ba-153">Base URLs</span></span>

<span data-ttu-id="806ba-154">Blazor アプリが基本パスの下にデプロイされている場合は、[作業にルーティング] プロパティで `<base>` タグを使用して、ページメタデータにベース URL を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="806ba-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="806ba-155">アプリケーションのホストページが Razor を使用してサーバーでレンダリングされる場合は、`~/` 構文を使用して、アプリのベースアドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="806ba-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="806ba-156">ホストページが静的な HTML の場合は、ベース URL を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="806ba-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="806ba-157">ページレイアウト</span><span class="sxs-lookup"><span data-stu-id="806ba-157">Page layout</span></span>

<span data-ttu-id="806ba-158">ASP.NET Web フォームのページレイアウトは、マスターページによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="806ba-159">マスターページは、1つまたは複数のコンテンツのプレースホルダーを持つテンプレートを定義します。このプレースホルダーは、個々のページで提供できます。</span><span class="sxs-lookup"><span data-stu-id="806ba-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="806ba-160">マスターページは、 *.master*ファイルで定義され、`<%@ Master %>` ディレクティブで始まります。</span><span class="sxs-lookup"><span data-stu-id="806ba-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="806ba-161">*.Master*ファイルの内容は *.aspx*ページと同じようにコード化されますが、`<asp:ContentPlaceHolder>` コントロールを追加して、ページがコンテンツを提供できる場所をマークします。</span><span class="sxs-lookup"><span data-stu-id="806ba-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="806ba-162">*サイト. master*</span><span class="sxs-lookup"><span data-stu-id="806ba-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="806ba-163">Blazor では、レイアウトコンポーネントを使用してページレイアウトを処理します。</span><span class="sxs-lookup"><span data-stu-id="806ba-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="806ba-164">レイアウトコンポーネントは `LayoutComponentBase`から継承します。これにより、ページの内容を表示するために使用できる、`RenderFragment`型の単一の `Body` プロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="806ba-165">*MainLayout。 razor*</span><span class="sxs-lookup"><span data-stu-id="806ba-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="806ba-166">レイアウトが指定されたページが表示されると、そのページは、レイアウトによって `Body` プロパティがレンダリングされる場所で、指定されたレイアウトのコンテンツ内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="806ba-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="806ba-167">ページにレイアウトを適用するには、`@layout` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="806ba-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="806ba-168">*_Imports の razor*ファイルを使用して、フォルダーおよびサブフォルダー内のすべてのコンポーネントのレイアウトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="806ba-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="806ba-169">[ルーターコンポーネント](#router-component)を使用して、すべてのページの既定のレイアウトを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="806ba-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="806ba-170">マスターページでは複数のコンテンツプレースホルダーを定義できますが、Blazor のレイアウトには、1つの `Body` プロパティしかありません。</span><span class="sxs-lookup"><span data-stu-id="806ba-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="806ba-171">Blazor レイアウトコンポーネントのこの制限は、今後のリリースで対処される予定です。</span><span class="sxs-lookup"><span data-stu-id="806ba-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="806ba-172">ASP.NET Web フォームのマスターページは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="806ba-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="806ba-173">つまり、マスターページでマスターページを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="806ba-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="806ba-174">Blazor のレイアウトコンポーネントも入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="806ba-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="806ba-175">レイアウトコンポーネントをレイアウトコンポーネントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="806ba-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="806ba-176">内部レイアウトの内容は、外側のレイアウト内にレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="806ba-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="806ba-177">*ChildLayout。 razor*</span><span class="sxs-lookup"><span data-stu-id="806ba-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="806ba-178">*インデックス。 razor*</span><span class="sxs-lookup"><span data-stu-id="806ba-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="806ba-179">ページのレンダリングされた出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="806ba-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="806ba-180">Blazor のレイアウトでは、通常、ページのルート HTML 要素 (`<html>`、`<body>`、`<head>`など) を定義しません。</span><span class="sxs-lookup"><span data-stu-id="806ba-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="806ba-181">ルート HTML 要素は、代わりに Blazor アプリのホストページで定義されます。このページは、アプリの初期 HTML コンテンツを表示するために使用されます (「[ブートストラップ Blazor](project-structure.md#bootstrap-blazor)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="806ba-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="806ba-182">ホストページでは、周囲のマークアップを含むアプリの複数のルートコンポーネントをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="806ba-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="806ba-183">Blazor のコンポーネント (ページを含む) は `<script>` タグをレンダリングできません。</span><span class="sxs-lookup"><span data-stu-id="806ba-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="806ba-184">`<script>` タグが一度読み込まれてから変更できないため、この表示制限が存在します。</span><span class="sxs-lookup"><span data-stu-id="806ba-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="806ba-185">Razor 構文を使用してタグを動的に表示しようとすると、予期しない動作が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="806ba-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="806ba-186">代わりに、すべての `<script>` タグをアプリのホストページに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="806ba-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="806ba-187">[前へ](components.md)
>[次へ](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="806ba-187">[Previous](components.md)
[Next](state-management.md)</span></span>