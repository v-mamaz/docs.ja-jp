---
title: テキスト ファイルではないデータで機械学習モデルをトレーニングする - ML.NET
description: ML.NET を使用して、機械学習モデルのトレーニングのために非ファイル トレーニング データを予測パイプラインの一部として読み込む方法について説明します。
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4ffbc69629aa9dc6cea5d33c704bc9c57a4a612c
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092021"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>テキスト ファイルではないデータで機械学習モデルをトレーニングする - ML.NET

ML.NET で一般的に実証されているユース ケースは、`TextLoader` を使ってファイルからトレーニング データを読み取る方法です。
ただし、実際のトレーニングのシナリオでは、データは次のようなそれ以外の場所にある場合があります。

* SQL テーブル
* ログ ファイルから抽出
* その場で生成

[スキーマの理解](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md)を使って、既存の C# `IEnumerable` を `DataView` として ML.NET に取り込みます。

この例では、顧客チャーン予測モデルを構築し、実稼動システムから次の機能を抽出します。

* 顧客の ID (モデルでは無視されます)
* 顧客が解約済みかどうか (ターゲット 'ラベル')
* '人口統計カテゴリ' ('ヤング アダルト' のような 1 つの文字列)
* 過去 5 日間のアクセス数

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

このデータを `DataView` に読み込み、次のコードを使用して、モデルをトレーニングします。

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
