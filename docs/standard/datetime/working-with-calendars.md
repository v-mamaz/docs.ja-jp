---
title: カレンダーの使用
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET Framework], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f6b758dd509ac2d318180c014ac3d262fe331f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623236"
---
# <a name="working-with-calendars"></a>カレンダーの使用

日時の値は特定の時点を表しますが、その文字列形式はカルチャに依存し、特定のカルチャで日時の値の表示に使用される規則と、そのカルチャで使用される暦の両方に応じて決まります。 このトピックでは、.NET でのカレンダーのサポートについて説明し、日付の値を使用する場合に、calendar クラスの使用について説明します。

## <a name="calendars-in-net"></a>.NET で予定表

派生して .NET でのすべてのカレンダー、<xref:System.Globalization.Calendar?displayProperty=nameWithType>クラスを基本の暦の実装を提供します。 <xref:System.Globalization.Calendar> クラスを継承するクラスの 1 つに <xref:System.Globalization.EastAsianLunisolarCalendar> クラスがあります。これは、すべての太陰太陽暦の基本クラスです。 .NET には、次のカレンダー実装が含まれています。

* <xref:System.Globalization.ChineseLunisolarCalendar>。中国の太陰太陽暦を表します。

* <xref:System.Globalization.GregorianCalendar>。グレゴリオ暦を表します。 この暦は、<xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> 列挙体で定義されるサブタイプ (アラビア語や中東フランス語など) にさらに分けられます。 <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> プロパティは、グレゴリオ暦のサブタイプを指定します。

* <xref:System.Globalization.HebrewCalendar>。ヘブライ暦を表します。

* <xref:System.Globalization.HijriCalendar>。回教暦を表します。

* <xref:System.Globalization.JapaneseCalendar>。和暦を表します。

* <xref:System.Globalization.JapaneseLunisolarCalendar>。日本の太陰太陽暦を表します。

* <xref:System.Globalization.JulianCalendar>。ユリウス暦を表します。

* <xref:System.Globalization.KoreanCalendar>。韓国暦を表します。

* <xref:System.Globalization.KoreanLunisolarCalendar>。韓国の太陰太陽暦を表します。

* <xref:System.Globalization.PersianCalendar>。ペルシャ暦を表します。

* <xref:System.Globalization.TaiwanCalendar>。台湾暦を表します。

* <xref:System.Globalization.TaiwanLunisolarCalendar>。台湾の太陰太陽暦を表します。

* <xref:System.Globalization.ThaiBuddhistCalendar>。タイ仏暦を表します。

* <xref:System.Globalization.UmAlQuraCalendar>。ウムアルクラ暦を表します。

暦は、次の 2 とおりの方法で使用できます。

* 特定のカルチャで使用される暦として使用する。 <xref:System.Globalization.CultureInfo> オブジェクトにはそれぞれ、現在の暦 (オブジェクトで現在使用している暦) があります。 あらゆる日付と時刻の値の文字列形式には、現在のカルチャとその現在の暦が自動的に反映されます。 通常、現在の暦は、カルチャの既定の暦になります。 <xref:System.Globalization.CultureInfo> オブジェクトは、カルチャで使用できるその他の暦を含む、オプションの暦もあります。

* 特定のカルチャに依存しないスタンドアロンの暦として使用する。 この場合、暦が反映された値として日付を表すには、<xref:System.Globalization.Calendar> のメソッドを使用します。

<xref:System.Globalization.ChineseLunisolarCalendar>、<xref:System.Globalization.JapaneseLunisolarCalendar>、<xref:System.Globalization.JulianCalendar>、<xref:System.Globalization.KoreanLunisolarCalendar>、<xref:System.Globalization.PersianCalendar>、および <xref:System.Globalization.TaiwanLunisolarCalendar> の 6 つの Calendar クラスは、スタンドアロンの暦としてのみ使用できます。 これらは、どのカルチャでも、既定の暦またはオプションの暦としては使用されません。

## <a name="calendars-and-cultures"></a>暦とカルチャ

各カルチャには既定の暦があり、<xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> プロパティで定義されます。 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> プロパティは、特定のカルチャでサポートされるすべての暦を指定する <xref:System.Globalization.Calendar> オブジェクトの配列を返します。これには、そのカルチャの既定の暦も含まれます。

<xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> プロパティと <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> プロパティの例を次に示します。 この例では、タイ語 (タイ) と日本語 (日本) のカルチャの `CultureInfo` オブジェクトをそれぞれ作成し、それらの既定の暦とオプションの暦を表示します。 どちらについても、カルチャの既定の暦は <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> コレクションにも含まれます。

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

特定の <xref:System.Globalization.CultureInfo> オブジェクトで現在使用されている暦は、カルチャの <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> プロパティで定義されます。 カルチャの <xref:System.Globalization.DateTimeFormatInfo> オブジェクトは、<xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> プロパティから返されます。 カルチャの作成時の既定値は <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> プロパティの値と同じですが、 カルチャの現在の暦は、<xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> プロパティから返される配列に含まれる任意の暦に変更することができます。 現在の暦を <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> プロパティの値に含まれない暦に設定しようとすると、<xref:System.ArgumentException> がスローされます。

アラビア語 (サウジアラビア) のカルチャで使用する暦を変更する例を次に示します。 まず、<xref:System.DateTime> 値をインスタンス化し、現在のカルチャ (この例では英語 (米国)) と現在のカルチャの暦 (この例ではグレゴリオ暦) を使用して日付を表示します。 次に、現在のカルチャをアラビア語 (サウジアラビア) に変更し、そのカルチャの既定のウムアルクラ暦を使用して日付を表示します。 さらに、`CalendarExists` メソッドを呼び出して、アラビア語 (サウジアラビア) のカルチャで回教暦がサポートされているかどうかを判別します。 この暦はサポートされているため、現在の暦を回教暦に変更し、日付をもう一度表示します。 いずれの場合も、日付は、現在のカルチャの現在の暦を使用して表示されます。

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>日付と暦

<xref:System.Globalization.Calendar> 型のパラメーターを含み、指定した暦の値を日付の要素 (月、日、および年) に反映できるコンストラクターは例外として、<xref:System.DateTime> と <xref:System.DateTimeOffset> の値は、どちらも常にグレゴリオ暦に基づきます。 つまり、たとえば <xref:System.DateTime.Year%2A?displayProperty=nameWithType> プロパティはグレゴリオ暦の年を返し、<xref:System.DateTime.Day%2A?displayProperty=nameWithType> プロパティはグレゴリオ暦の月の日付を返します。

> [!IMPORTANT]
> 日付の値とその文字列形式で処理が異なることに注意してください。 日付の値はグレゴリオ暦に基づき、文字列形式は特定のカルチャの現在の暦に基づきます。

次の例は、<xref:System.DateTime> のプロパティと、それに対応する <xref:System.Globalization.Calendar> のメソッドの違いを示しています。 この例では、現在のカルチャはアラビア語 (エジプト)、現在の暦はウムアルクラ暦です。 <xref:System.DateTime> 値は、2011 年の 7 番目の月の 15 番目の日に設定されています。 この値は、明らかにグレゴリオ暦の日付と解釈されます。<xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> メソッドでインバリアント カルチャの規則を使用した場合に、これらと同じ値が返されるためです。 現在のカルチャの規則を使用して書式指定された日付の文字列形式は 14/08/32 です。これは、この日付に相当するウムアルクラ暦の日付です。 次に、`DateTime` と `Calendar` のメンバーを使用して、<xref:System.DateTime> 値の日、月、および年が返されます。 いずれの場合も、<xref:System.DateTime> のメンバーから返される値にはグレゴリオ暦の値が反映され、<xref:System.Globalization.UmAlQuraCalendar> のメンバーから返される値にはウムアルクラ暦の値が反映されます。

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>カレンダーに基づく日付をインスタンス化します。

<xref:System.DateTime> と <xref:System.DateTimeOffset> の値はグレゴリオ暦に基づくため、別の暦の日、月、または年の値を使用する場合は、<xref:System.Globalization.Calendar> 型のパラメーターを含むオーバーロードされたコンストラクターを呼び出して日付の値をインスタンス化する必要があります。 また、特定の暦の <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> メソッドのいずれかのオーバーロードを呼び出して、特定の暦の値に基づいて <xref:System.DateTime> オブジェクトをインスタンス化することもできます。

次の例では、<xref:System.DateTime> オブジェクトを <xref:System.Globalization.HebrewCalendar> コンストラクターに渡して 1 つの <xref:System.DateTime> 値をインスタンス化し、<xref:System.DateTime> メソッドを呼び出してもう 1 つの <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> 値をインスタンス化しています。 2 つの値はヘブライ暦の同一の値を使用して作成されるため、<xref:System.DateTime.Equals%2A?displayProperty=nameWithType> メソッドを呼び出すと、2 つの <xref:System.DateTime> 値が等しいことが示されます。

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>現在の暦で日付を表す

日時書式指定メソッドでは、日付を文字列に変換する際に、常に現在の暦を使用します。 つまり、年、月、および日の文字列形式には現在の暦が反映され、必ずしもグレゴリオ暦が反映されるとは限りません。

次の例は、現在の暦が日付の文字列形式にどのように影響するかを示しています。 この例では、現在のカルチャを中国語 (繁体字、台湾) に変更し、日付の値をインスタンス化します。 その後、現在の暦と日付を表示し、現在の暦を <xref:System.Globalization.TaiwanCalendar> に変更して、現在の暦と日付をもう一度表示します。 最初に日付を表示したときは、日付がグレゴリオ暦の日付として表され、 2 回目に表示したときは、台湾暦の日付として表されます。

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>現在ではないカレンダーにおける日付を表す

特定のカルチャの現在の暦以外の暦を使用して日付を表すには、その <xref:System.Globalization.Calendar> オブジェクトのメソッドを呼び出す必要があります。 たとえば、<xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>、および <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> の各メソッドは、それぞれ年、月、および日を、特定の暦を反映した値に変換します。

> [!WARNING]
> 一部の暦はどのカルチャのオプションの暦にもなっていないため、そのような暦で日付を表す場合は、常に Calendar のメソッドを呼び出す必要があります。 これは、<xref:System.Globalization.EastAsianLunisolarCalendar> クラス、<xref:System.Globalization.JulianCalendar> クラス、および <xref:System.Globalization.PersianCalendar> クラスから派生したすべての暦に当てはまります。

次の例では、<xref:System.Globalization.JulianCalendar> オブジェクトを使用して、ユリウス暦の 1905 年 1 月 9 日という日付をインスタンス化します。 この日付を既定の暦 (グレゴリオ暦) を使用して表示した場合は、1905 年 1 月 22 日と表されます。 <xref:System.Globalization.JulianCalendar> の各メソッドを呼び出すことで、この日付をユリウス暦で表すことができます。

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>暦と日付範囲

暦でサポートされている最も古い日付は、暦の <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> プロパティによって示されます。 <xref:System.Globalization.GregorianCalendar> クラスでは、その日付は西暦 0001 年 1 月 1 日 です。 .NET の他のカレンダーの大半は、以降の日付をサポートします。 暦でサポートされている最も古い日付より前の日付と時刻の値を処理しようとすると、<xref:System.ArgumentOutOfRangeException> 例外がスローされます。

ただし、重要な例外が 1 つあります。 <xref:System.DateTime> オブジェクトと <xref:System.DateTimeOffset> オブジェクトの既定の (初期化されていない) 値は、<xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 値と同じです。 西暦 0001 年 1 月 1日をサポートしない予定表では、この日付の書式設定しようとする場合 書式指定子を指定しない、書式指定メソッドは、"G"(一般の日付/時刻のパターン) 書式指定子ではなく、"s"(並べ替え可能な日付/時刻のパターン) 書式指定子を使用します。 その結果、書式設定操作は <xref:System.ArgumentOutOfRangeException> 例外をスローしません。 代わりに、サポートされていない日付を返します。 この問題を、次の例で説明します。この例は、現在のカルチャが日本語 (日本) に設定されていれば和暦で、アラビア語 (エジプト) に設定されていればウムアルクラ暦で、<xref:System.DateTime.MinValue?displayProperty=nameWithType> の値を表示します。 また、現在のカルチャを英語 (米国) に設定し、これらの各 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> オブジェクトで <xref:System.Globalization.CultureInfo> メソッドを呼び出します。 どの場合も、並べ替え可能な日付と時刻のパターンを使用して、日付が表示されます。

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>時代 (年号) の操作

暦では通常、日付が時代 (年号) に分けられます。 ただし、 <xref:System.Globalization.Calendar> .NET のクラスは、予定表とのほとんどによって定義されたすべての時代をサポートしていません、<xref:System.Globalization.Calendar>クラスは時代は 1 つのみをサポートします。 複数の時代 (年号) をサポートしているのは、<xref:System.Globalization.JapaneseCalendar> クラスと <xref:System.Globalization.JapaneseLunisolarCalendar> クラスだけです。

> [!IMPORTANT]
>  <xref:System.Globalization.JapaneseCalendar> と <xref:System.Globalization.JapaneseLunisolarCalendar> での新しい時代が 2019 年 5 月 1 日に始まります。 この変更は、これらのカレンダーを使用するすべてのアプリケーションに影響します。 詳細については「[.NET での日本語のカレンダーの新しい時代](https://blogs.msdn.microsoft.com/dotnet/2018/11/14/handling-a-new-era-in-the-japanese-calendar-in-net/)」をご覧いただき、アプリケーションが影響を受けるかどうかを判断します。 参照してください[、アプリケーション、日本語の時代 (年号) の変更の準備](/windows/uwp/design/globalizing/japanese-era-change)については、時代 (年号) の変更に対する準備状況を確認する Windows 上のアプリケーションをテストします。

### <a name="eras-and-era-names"></a>時代 (年号) と時代 (年号) の名前

.NET では、特定の暦の実装でサポートされる時代 (年号) を表す整数が逆の順序で格納、<xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType>配列。 現在の時代 (年号) のインデックスは 0 で、複数の時代 (年号) をサポートする <xref:System.Globalization.Calendar> クラスの場合は、後に続く各インデックスが前の時代 (年号) に対応します。 <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> 配列における現在の時代 (年号) のインデックスは、静的な <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> プロパティで定義されます。これは定数であり、値は常に 0 になります。 個々の <xref:System.Globalization.Calendar> クラスには、現在の時代 (年号) の値を返す静的フィールドも含まれています。 これらを次の表に示します。

| Calendar クラス                                        | 現在の時代 (年号) のフィールド                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

特定の時代 (年号) を表す数値に対応する名前は、その数値を <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> メソッドに渡すことで取得できます。 次の例では、これらのメソッドを呼び出して、<xref:System.Globalization.GregorianCalendar> クラスでサポートされる時代 (年号) に関する情報を取得しています。

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

また、"g" カスタム日時書式指定文字列では、日付と時刻の文字列形式に暦の時代 (年号) の名前が含まれます。 詳細については、次を参照してください。[カスタム日時書式指定文字列](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)します。

### <a name="instantiating-a-date-with-an-era"></a>日付、時代 (年号) のインスタンス化します。

複数の時代 (年号) をサポートする 2 つの <xref:System.Globalization.Calendar> クラスでは、特定の年、月、および日の値で構成される日付があいまいになることがあります。たとえば、<xref:System.Globalization.JapaneseCalendar> では、4 つのすべての時代 (年号) に数値が 1 ～ 15 になる年があります。 通常、時代 (年号) が指定されていない場合は、日時および暦のどちらのメソッドでも、値が現在の時代 (年号) に属すると見なされます。 複数の時代 (年号) をサポートする <xref:System.Globalization.Calendar> クラスの日付をインスタンス化するときに時代 (年号) を明示的に指定するには、<xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> メソッドを呼び出します。 このメソッドを使用すると、時代 (年号) を、暦の年、月、日、時、分、秒、およびミリ秒と共に明示的に指定できます。

次の例では、<xref:System.Globalization.Calendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> メソッドを使用して、<xref:System.Globalization.JapaneseCalendar> クラスでサポートされるそれぞれの時代 (年号) の同じ日付 (2 番目の年の最初の月の最初の日) をインスタンス化しています。 その後、和暦とグレゴリオ暦の両方で日付を表示しています。 また、この例では <xref:System.DateTime> コンストラクターも呼び出して、時代 (年号) を指定せずに日付の値を作成した場合は現在の時代 (年号) の日付が作成されることを示しています。

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs#7)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb#7)]

### <a name="representing-dates-in-calendars-with-eras"></a>時代 (年号) を含む暦で日付を表す

<xref:System.Globalization.Calendar> オブジェクトの現在の暦が、時代 (年号) をサポートする <xref:System.Globalization.CultureInfo> オブジェクトである場合は、完全な日付と時刻、長い日付、および短い日付の各パターンにおいて、日付と時刻の値の文字列形式に時代 (年号) が含まれます。 それらの日付パターンを表示する例を次に示します。現在のカルチャは日本 (日本語)、現在の暦は和暦です。

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar>クラスが唯一のカレンダー クラスの現在の暦は、両方のサポートしている日付の 1 つ以上の時代 (年号) に .NET で、<xref:System.Globalization.CultureInfo>オブジェクト - 具体的には、<xref:System.Globalization.CultureInfo>日本語 (日本) のカルチャを表すオブジェクト。

どの暦の場合も、"g" カスタム書式指定子の結果の文字列には時代 (年号) が含まれます。 次の例では、"MM-dd-yyyy g" というカスタム書式指定文字列を使用して、結果の文字列に時代 (年号) を含めています。現在の暦はグレゴリオ暦です。

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

日付の文字列形式を現在の暦以外の暦で表す場合は、<xref:System.Globalization.Calendar> クラスの <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> メソッドを <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>、および <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> の各メソッドと一緒に使用して、日付とそれが属する時代 (年号) を明確に示すことができます。 <xref:System.Globalization.JapaneseLunisolarCalendar> クラスを使用した具体的な例を次に示します。 ただし、時代 (年号) を表す整数ではなく、名前または省略形を結果の文字列に含めるには、<xref:System.Globalization.DateTimeFormatInfo> オブジェクトをインスタンス化し、その現在の暦を <xref:System.Globalization.JapaneseCalendar> にする必要があります  (<xref:System.Globalization.JapaneseLunisolarCalendar> 暦をカルチャの現在の暦にすることはできませんが、この場合は 2 つの暦で同じ時代 (年号) が共有されます)。

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

## <a name="see-also"></a>関連項目

- [方法: グレゴリオ暦以外の暦で日付の表示](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [サンプル: カレンダーの週の範囲のユーティリティ](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
