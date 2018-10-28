---
title: サンプル ビジネス シナリオとユース ケースのサーバーレス アプリ
description: イメージ処理からモバイル バックエンドとの ETL パイプラインに範囲のサンプルにアクセスして実践的なアプローチとサーバーレスについて説明します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c38d1c6c4e04f3fa38946c97af5d94758b3ed6f7
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "49370203"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="51bbc-103">サーバーレスのビジネス シナリオとユース ケース</span><span class="sxs-lookup"><span data-stu-id="51bbc-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="51bbc-104">多くのユース ケースとサーバーレス アプリケーションのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="51bbc-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="51bbc-105">この章には、さまざまなシナリオを示すサンプルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="51bbc-106">このシナリオでは関連するドキュメントとパブリックなソース コード リポジトリへのリンクを使用します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="51bbc-107">この章のサンプルには、構築して、サーバーレス ソリューションを実装する、自分で開始することが有効にします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="51bbc-108">分析し、イメージのアーカイブ</span><span class="sxs-lookup"><span data-stu-id="51bbc-108">Analyze and archive images</span></span>

<span data-ttu-id="51bbc-109">このサンプルでは、サーバーレスのイベント (Event Grid)、ワークフロー (ロジック アプリ)、およびコード (Azure Functions) を示します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="51bbc-110">このケースの Cognitive Services のイメージの分析のための別のリソースと統合する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="51bbc-111">コンソール アプリケーションを使用すると、web 上のリンクを URL に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="51bbc-112">アプリは、イベント グリッド メッセージとして URL を発行します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="51bbc-113">並列でサーバーレスの関数アプリとロジック アプリは、メッセージをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="51bbc-114">サーバーレスの関数アプリには、blob ストレージにイメージがシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="51bbc-115">Azure Table storage の情報も格納します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="51bbc-116">メタデータには、元の画像の URL と blob のイメージの名前が格納されます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="51bbc-117">ロジック アプリは、画像を分析し、マシン生成のキャプションを作成するカスタム Vision API と対話します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="51bbc-118">キャプションは、メタデータ テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-118">The caption is stored in the metadata table.</span></span>

![分析し、イメージのアーキテクチャのアーカイブ](./media/image-processing-example.png)

<span data-ttu-id="51bbc-120">別の単一ページ アプリケーション (SPA) は、イメージおよびメタデータの一覧を取得するサーバーレス関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="51bbc-121">イメージごとに、アーカイブから画像データを提供する別の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="51bbc-122">字幕を自動でギャラリーを最後になります。</span><span class="sxs-lookup"><span data-stu-id="51bbc-122">The final result is a gallery with automatic captions.</span></span>

![自動化されたイメージ ギャラリー](./media/automated-image-gallery.png)

<span data-ttu-id="51bbc-124">完全なリポジトリとロジック アプリをビルドする手順についてはここで使用可能なが:[イベント グリッド グルー](https://github.com/JeremyLikness/Event-Grid-Glue)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="51bbc-125">Xamarin.Forms と関数を使用してクロス プラットフォーム モバイル クライアント</span><span class="sxs-lookup"><span data-stu-id="51bbc-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="51bbc-126">Azure の Web ポータルで、または Visual Studio では、単純なサーバーレス Azure 関数を実装する方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51bbc-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="51bbc-127">Android、iOS、および Windows で実行されている Xamarin.Forms を使用するクライアントをビルドします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="51bbc-128">アプリケーションは、サーバーとサーバーレス バックエンドをモバイル クライアント間の通信中として JavaScript Object Notation (JSON) を使用する、絞り込みます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="51bbc-129">詳細については、次を参照してください[Xamarin.Forms クライアントの単純な Azure 関数を実装する。](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span><span class="sxs-lookup"><span data-stu-id="51bbc-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="51bbc-130">サーバーレス画像認識と写真モザイクを生成します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="51bbc-131">サンプルでは、Azure Functions と Microsoft Cognitive Services Custom Vision Service を使用して、入力の画像からフォト mosaic を生成します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="51bbc-132">イメージを認識するモデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-132">The model is trained to recognize images.</span></span> <span data-ttu-id="51bbc-133">イメージがアップロードされると、そのイメージを認識して、Bing で検索します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="51bbc-134">検索結果を使用して、元のイメージが再合成します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-134">The original image is recomposed using the search results.</span></span>

![オーランド目の写真と mosaic](./media/orlando-eye-both.png)

<span data-ttu-id="51bbc-136">たとえば、オーランド ランドマーク、オーランド目などを使用してモデルをトレーニングできます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="51bbc-137">Custom Vision オーランド目のイメージが認識され、関数はフォト mosaic Bing の画像検索結果で構成の作成「オーランド目です」</span><span class="sxs-lookup"><span data-stu-id="51bbc-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="51bbc-138">詳細については、次を参照してください。 [Azure Functions フォト mosaic ジェネレーター](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-138">For more information, see [Azure Functions photo mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="51bbc-139">既存のアプリケーションをクラウドに移行します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="51bbc-140">前の章で既に説明した、オンプレミス アプリケーションをホストする N 層アーキテクチャを採用する一般的です。</span><span class="sxs-lookup"><span data-stu-id="51bbc-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="51bbc-141">「現状有姿のリソースの移行クラウドへのリスクの小さいパスは、仮想マシンを使用して、自分のアプリケーションをリファクタリングする機会を使用する多くの企業を選択します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="51bbc-142">さいわい、リファクタリングを「オール_オア_ナッシング」残存作業がありません。</span><span class="sxs-lookup"><span data-stu-id="51bbc-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="51bbc-143">実際には、アプリを移行し、段階的な部分に対応するクラウド ネイティブ コンポーネントを交換することができます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="51bbc-144">アプリケーションでは、Azure Functions のプロキシ機能を使用して、リファクタリングでオンプレミスでレガシ コードからサーバーレスのエンドポイントにエンドポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![移行のアーキテクチャ](./media/migration-architecture.png)

<span data-ttu-id="51bbc-146">プロキシは、サーバーレスの関数に移動すると、個々 の要求を再ルーティングするように更新する 1 つの API エンドポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="51bbc-147">全体の移行について説明するビデオを表示することができます:[リフト アンド シフト サーバーレス Azure functions による](https://channel9.msdn.com/Events/Connect/2017/E102)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="51bbc-148">サンプル コードへのアクセス:[アプリケーションの持ち込み](https://github.com/JeremyLikness/bring-own-app-connect-17)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="51bbc-149">CSV ファイルを解析し、データベースに挿入</span><span class="sxs-lookup"><span data-stu-id="51bbc-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="51bbc-150">抽出、変換、および読み込み (ETL) は、さまざまなシステムを統合する共通のビジネス関数。</span><span class="sxs-lookup"><span data-stu-id="51bbc-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="51bbc-151">従来のアプローチは、多くの場合、専用の FTP サーバーをセットアップし、ファイルを解析し、業務用に変換するスケジュールされたジョブを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51bbc-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="51bbc-152">サーバーレス アーキテクチャ簡単ジョブ ファイルがアップロードされたときにトリガーを起動できるためです。</span><span class="sxs-lookup"><span data-stu-id="51bbc-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="51bbc-153">Azure Functions あたってタスクなどの特定の問題に焦点を少量のコードの最適な構成で ETL。</span><span class="sxs-lookup"><span data-stu-id="51bbc-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![ETL アーキテクチャ](./media/csvimport.png)

<span data-ttu-id="51bbc-155">ソース コードとハンズオン ラボでは、次を参照してください。 [CSV インポート ラボ](https://github.com/JeremyLikness/azure-fn-file-process-hol)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="51bbc-156">リンクを短縮し、メトリックの追跡</span><span class="sxs-lookup"><span data-stu-id="51bbc-156">Shorten links and track metrics</span></span>

<span data-ttu-id="51bbc-157">Twitter の 140 文字の制限に対応する投稿をリンク短くするツールの最初の Url を簡単に言えばエンコードを支援します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="51bbc-158">いくつかの用途を最もよく分析のためには、クリックスルーの追跡を可能にし、拡大しました。</span><span class="sxs-lookup"><span data-stu-id="51bbc-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="51bbc-159">リンクの shortener シナリオは、リンクを管理し、メトリックを報告するすべてサーバーレス アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51bbc-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="51bbc-160">Azure Functions を使用して、シングル ページ アプリケーション (SPA) を使用すると、長い URL を貼り付けて、短縮 Url を生成するサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="51bbc-161">Url は、キャンペーン (トピック) とメディアへのリンクが掲載されているソーシャル ネットワーク) などのようなものを追跡するためにタグ付けされます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="51bbc-162">含まれるショート コードは、値として、長い URL を使用して、キーとして Azure Table Storage に格納されます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="51bbc-163">短いリンクをクリックすると別の関数は長い URL を検索、リダイレクトを送信し、イベントに関する情報をキューに配置します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="51bbc-164">別の Azure 関数は、キューを処理し、Azure Cosmos DB に情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![リンク shortener アーキテクチャ](./media/link-shortener-architecture.png)

<span data-ttu-id="51bbc-166">収集されたデータに関する洞察を収集するために Power BI ダッシュ ボードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="51bbc-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="51bbc-167">バックエンドでは、Application Insights は、重要なメトリックを提供します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="51bbc-168">製品利用統計情報には、平均的なユーザーをリダイレクトするのにかかると、Azure Table Storage へのアクセスにかかる時間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="51bbc-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![Power BI の使用例](./media/power-bi-example.png)

<span data-ttu-id="51bbc-170">命令でフル リンク shortener リポジトリは、ここで使用可能な:[サーバーレス URL 短縮ツール](https://github.com/jeremylikness/serverless-url-shortener)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="51bbc-171">ここでは、簡略化されたバージョンについて説明することができます:[サーバーレスの .NET アプリを数分での Azure Storage](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="51bbc-172">Ping を使用してデバイスの接続を確認します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="51bbc-173">Azure IoT Hub と Azure 関数のサンプルを構成します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="51bbc-174">IoT Hub での新しいメッセージは、Azure 関数をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="51bbc-175">サーバーレス コードでは、元のメッセージ送信元デバイスにコンテンツと同じメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="51bbc-176">プロジェクトは、ソリューションに必要なすべてのコードと展開構成にします。</span><span class="sxs-lookup"><span data-stu-id="51bbc-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="51bbc-177">詳細については、次を参照してください。 [Azure IoT Hub の ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-177">For more information, see [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="51bbc-178">推奨リソース</span><span class="sxs-lookup"><span data-stu-id="51bbc-178">Recommended resources</span></span>

* [<span data-ttu-id="51bbc-179">Azure Functions の写真 mosaic ジェネレーター</span><span class="sxs-lookup"><span data-stu-id="51bbc-179">Azure Functions photo mosaic generator</span></span>](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [<span data-ttu-id="51bbc-180">Azure IoT Hub の ping</span><span class="sxs-lookup"><span data-stu-id="51bbc-180">Azure IoT Hub ping</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [<span data-ttu-id="51bbc-181">.NET アプリを数分でサーバーレスの azure Storage</span><span class="sxs-lookup"><span data-stu-id="51bbc-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [<span data-ttu-id="51bbc-182">アプリケーションを持ち込み</span><span class="sxs-lookup"><span data-stu-id="51bbc-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [<span data-ttu-id="51bbc-183">CSV インポート ラボ</span><span class="sxs-lookup"><span data-stu-id="51bbc-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [<span data-ttu-id="51bbc-184">イベント グリッド グルー</span><span class="sxs-lookup"><span data-stu-id="51bbc-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
* [<span data-ttu-id="51bbc-185">Xamarin.Forms クライアントの単純な Azure 関数を実装します。</span><span class="sxs-lookup"><span data-stu-id="51bbc-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [<span data-ttu-id="51bbc-186">リフト アンド シフトとサーバーレス Azure 関数</span><span class="sxs-lookup"><span data-stu-id="51bbc-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
* [<span data-ttu-id="51bbc-187">サーバーレス URL 短縮ツール</span><span class="sxs-lookup"><span data-stu-id="51bbc-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
<span data-ttu-id="51bbc-188">[前へ](orchestration-patterns.md)
[次へ](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="51bbc-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>