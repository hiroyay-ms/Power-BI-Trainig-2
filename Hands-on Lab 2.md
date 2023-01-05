# Power BI Hands-on training 

<br />

### **INDEX**

- [CSV ファイルからデータを読み込み](#csv-ファイルからデータを読み込み)

- [レポートへの折れ線グラフの追加](#レポートへの折れ線グラフの追加)

- [Excel ファイルからデータを読み込み](#excel-ファイルからデータを読み込み)

- [日付テーブルの追加](#日付テーブルの追加)

- [データモデルの更新](#データモデルの更新)

- [レポートの更新](#レポートの更新)

- [メジャーの追加](#メジャーの追加)

- [新しいページの追加](#新しいページの追加)

- [スライサーの追加](#スライサーの追加)

- [カードの追加](#カードの追加)

- [マップの追加](#マップの追加)

- [マトリックスの追加](#マトリックスの追加)

<br />

## オープンデータを利用したレポート作成

### CSV ファイルからデータを読み込み

- Power BI Desktop を起動

- 「**データを取得**」をクリックし、「**テキスト/CSV**」をクリック

  <img src="images/get-data.png" />

- 「**newly_confirmed_cases_daily.csv**」を選択し、「**開く**」をクリック

- **元のファイル**、**区切り記号**、**データ型検出** を設定し、「**データの変換**」をクリック

  - **元のファイル**： 65001: Unicode (UTF-8)

  - **区切り記号**： コンマ

  - **データ型検出**： 最初の 200 行に基づく

    <img src="images/get-covid-csv-01.png" />

- Power Query エディターが起動

  <img src="images/get-covid-csv-02.png" />

- 「**Date**」列を選択し、「**変換**」タブに切り替え、「**データ型**」-「**日付**」を選択

  <img src="images/get-covid-csv-03.png" />

- 「**新規手順の追加**」をクリック

  <img src="images/get-covid-csv-04.png" />

- 「**Prefecture**」列の「**▼**」をクリック、「**ALL**」のチェックを外し「**OK**」をクリック

  <img src="images/get-covid-csv-05.png" />

- 「**適用したステップ**」に行った操作を記録

  <img src="images/get-covid-csv-06.png" />

  ※ 次回以降ファイルを読み込む際も同様のステップが適用

- 「**ホーム**」タブに切り替え、「**閉じて適用**」をクリック

  <img src="images/get-covid-csv-07.png" />

- フィールド リストに読み込んだデータが追加

  <img src="images/get-covid-csv-08.png" />

<br />

### レポートへの折れ線グラフの追加

- 「**視覚化**」の「**折れ線グラフ**」をクリック

  <img src="images/select-visual-line.png" />

- フィールド リストの「**X 軸」に「**Date**」を「**Y 軸**」に「**Newly confirmed cases**」をドラッグして配置

  <img src="images/line-chart-covid-01.png" />

- レポート上の折れ線グラフをドラッグして大きさを調整

  <img src="images/line-chart-covid-02.png" />

- フィールド リストの「**Date**」-「**日付の階層**」を展開

  「**X 軸**」に「**月**」、「**Y 軸**」に「**Newly confirmed cases**」、「**凡例**」に「**年**」をドラッグして配置

  <img src="images/line-chart-covid-03.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**行**」の「**色**」を展開し、凡例に指定した年の色を指定

- 「**マーカー**」をオンに設定

  <img src="images/line-chart-covid-04.png" />

- 折れ線グラフが更新されたことを確認

  <img src="images/line-chart-covid-05.png" />

<br />

### Excel ファイルからデータを読み込み

- 「**データを取得**」をクリックし、「**Excel ブック**」をクリック

  <img src="images/get-data.png" />

- 「**都道府県.xlsx**」を選択し、「**開く**」をクリック

- 「**都道府県マスタ**」を選択し、「**データの変換**」をクリック

  <img src="images/get-prefecture-excel-01.png" />

- Power Query エディターが起動

  <img src="images/get-prefecture-excel-02.png" />

- 「**行の削除**」-「**上位の行の削除**」を選択

  <img src="images/get-prefecture-excel-03.png" />

- 「**行数**」に「**2**」を入力し「**OK**」をクリック

  <img src="images/get-prefecture-excel-04.png" />

- 「**都道府県別地方一覧**」列を選択、「**列の削除**」-「**列の削除**」を選択

  <img src="images/get-prefecture-excel-05.png" />

- 「**1 行目をヘッダーとして使用**」を選択し、1 行目を列名に昇格

  <img src="images/get-prefecture-excel-06.png" />

- 「**No**」と「**地方区分**」列を選択、「**変換**」タブの「**フィル**」-「**下**」をクリックし空白行を上位の行の値で穴埋め

  <img src="images/get-prefecture-excel-07.png" />

  <img src="images/get-prefecture-excel-08.png" />

- 「**列の追加**」タブに切り替え、「**インデックス列**」-「**1 から**」をクリック

  <img src="images/get-prefecture-excel-09.png" />

- 追加された「**インデックス**」列を右クリックし「**名前の変更**」を選択

  <img src="images/get-prefecture-excel-10.png" />

- 列名を「**都道府県No**」に変更

- 同様の手順で「**No**」列の名前を「**地方区分No**」に変更

- 「**都道府県No**」列をドラッグして一番左に配置

  <img src="images/get-prefecture-excel-11.png" />

- 「**適用したステップ**」に行った操作が記録されていることを確認

  <img src="images/get-prefecture-excel-12.png" />

- 「**ホーム**」タブの「**閉じて適用**」をクリック

  <img src="images/get-prefecture-excel-13.png" />

- フィールド リストに読み込んだデータが追加

  <img src="images/get-prefecture-excel-14.png" />

<br />

### 日付テーブルの追加

- 画面右の「**データ**」をクリック

  <img src="images/select-data.png" />

- 「**新しいテーブル**」をクリック

  <img src="images/new-table.png" />

- 数式バーに CALENDAR 関数を入力し、「**日付マスタ**」の名前で 2020 年から 2022 年までの日付でテーブルを作成

  ```
  日付マスタ = CALENDAR("2020/1/1", "2022/12/31")
  ```

- テーブルに指定した期間の日付で「** Date**」列が追加されることを確認

  <img src="images/create-date-master-01.png" />

- 「**新しい列**」をクリック

  <img src="images/new-column.png" />

- 数式バーに YEAR 関数を入力し、「**年**」列を追加

  ```
  年 = YEAR('日付マスタ'[Date]) & "年" 
  ```

  <img src="images/create-date-master-02.png" />
  
- 同様の手順で関数を使用し、以下５つの列を追加

  ```
  月 = FORMAT('日付マスタ'[Date], "MM月")
  ```

  ```
  曜日No = WEEKDAY('日付マスタ'[Date])
  ```

  ```
  曜日 = SWITCH(WEEKDAY('日付マスタ'[Date]), 1, "日曜日", 2, "月曜日", 3, "火曜日", 4, "水曜日", 5, "木彫日", 6, "金曜日", "土曜日")
  ```

  ```
  半期No = IF(MONTH('日付マスタ'[Date]) < 7, 1, 2)
  ```

  ```
  半期 = IF(MONTH('日付マスタ'[Date]) < 7, "上半期", "下半期") 
  ```

  「**月**」「**曜日No**」「**曜日**」「**半期No**」「**半期**」列をテーブルに追加

  <img src="images/create-date-master-03.png" />

- 「**曜日**」列を選択、「**列で並べ替え**」-「**曜日No**」をクリック

  <img src="images/create-date-master-04.png" />

- 「**半期**」列を選択、「**列で並べ替え**」-「**半期No**」をクリック

  <img src="images/create-date-master-05.png" />

- 「**テーブル ツール**」タブの「**日付テーブルとしてマークする**」を選択

  <img src="images/create-date-master-06.png" />

- 「**日付列**」に「**Date**」列を指定し「**OK**」をクリック

  <img src="images/create-date-master-07.png" />

### データモデルの更新

- データ リストから「**都道府県マスタ**」を選択

- 「**地方区分**」列を選択、「**列で並べ替え**」-「**地方区分No**」を選択

  <img src="images/update-prefecture-master-01.png" />

- 「**都道府県区分**」列を選択、「**列で並べ替え**」-「**都道府県No**」を選択

  <img src="images/update-prefecture-master-02.png" />

- 画面右の「**モデル**」をクリック

  <img src="images/select-model.png" />

- 「**日付マスタ**」テーブルの「**Date**」列を「**newly_confirmed_cases_daily**」テーブルの「**Date**」列にドラッグ

- 「**日付マスタ**」と「**newly_confirmed_cases_daily**」テーブルのそれぞれの Date 列を関連付け

  <img src="images/create-date-master-08.png" />

- 「**リレーションシップの管理**」をクリック

  <img src="images/create-date-master-09.png" />

- 各テーブル間のリレーションシップを確認

  <img src="images/create-date-master-10.png" />

  ※ 「**都道府県マスタ**」と「**newly_confirmed_cases_daily**」テーブル間には自動的にリレーションシップが作成

- 「**日付マスタ**」の「**年**」列を選択し「<img src="images/icon-option.png" height="15" />」をクリックし、「**階層の作成**」を選択

  <img src="images/create-date-master-11.png" />

- 「**日付マスタ**」に階層が追加

  <img src="images/create-date-master-12.png" />

- 「**半期**」列を選択し「<img src="images/icon-option.png" height="15" />」をクリック、「**階層に追加**」-「**年 階層**」を選択

  <img src="images/create-date-master-13.png" />

- 同様の手順で「**月**」列を階層に追加

  <img src="images/create-date-master-14.png" />

- 追加した階層を選択、「**プロパティ**」パネルで名前を「**日付階層**」に変更

  <img src="images/create-date-master-15.png" />

- 「**半期No**」列を選択、「**プロパティ**」パネルで「**非表示**」を「**はい**」に変更

  <img src="images/create-date-master-16.png" />

- 同様の手順で「**曜日No**」も非表示に変更

- フィールド リストで指定した内容を確認

  <img src="images/create-date-master-17.png" />

- フィールド リストで「**都道府県マスタ**」を選択

- 「**地方区分No**」、「**都道府県No**」を非表示に設定

  <img src="images/update-prefecture-master-03.png" />

<br />

### レポートの更新

- 画面右の「**レポート**」を選択

  <img src="images/select-report.png" />

- ページ上の折れ線グラフを選択

  <img src="images/line-chart-covid-06.png" />

- 「**X 軸**」の「**Date**」を「**×**」をクリックして削除

  <img src="images/line-chart-covid-07.png" />

- 「**X 軸**」に「**日付マスタ**」の「**月**」列を、「**Y 軸**」に「**年**」列をドラッグして配置

  <img src="images/line-chart-covid-08.png" />

- ページ上の折れ線グラフの「…」をクリック、「**軸の並べ替え**」-「**月**」を選択

  <img src="images/line-chart-covid-09.png" />

- 同じ手順で「**軸の並べ替え**」-「**昇順で並べ替え**」を選択

- 月ごとの感染者数を年別に表現

  <img src="images/line-chart-covid-10.png" />

- 「**スモール マルチプル**」に「**都道府県マスタ**」-「**地方区分**」をドラッグして配置

  <img src="images/line-chart-covid-11.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**スモール マルチプル**」を展開し、「**レイアウト**」の「**列**」を **４** に変更

  <img src="images/line-chart-covid-12.png" />

- 地方ごとにグラフを分割して表示

  <img src="images/line-chart-covid-13.png" />

<br />

### メジャーの追加

- 画面右の「**データ**」をクリック

  <img src="images/select-data.png" />

- データ リストから「**newly_confirmed_cases_daily**」を選択

- 「**新しいメジャー**」をクリック

  <img src="images/new-measure.png" />

- 「**数式バー**」に式を入力

  ```
  Total = SUM(newly_confirmed_cases_daily[Newly confirmed cases])
  ```

- 「**書式設定**」の「**,**」をクリック

  <img src="images/measure-confirmed-cases.png" />

- 再度、「**新しいメジャー**」をクリックし、前月比を算出するメジャーを追加

  ```
  MoM% = DIVIDE('newly_confirmed_cases_daily'[Total], CALCULATE('newly_confirmed_cases_daily'[Total], DATEADD('日付マスタ'[Date], -1, MONTH))) - 1
  ```

- 「**書式設定**」の「**％**」をクリック

  <img src="images/measure-confirmed-cases-mom.png" />

- 画面右の「**モデル**」をクリック

  <img src="images/select-model.png" />

- フィールド リストの「**newly_confirmed_cases_daily**」配下の「**Total**」、「**MoM%**」を選択

- プロパティ パネルの「**フォルダーの表示**」に **Measures** と入力

  <img src="images/model-confirmed-cases-01.png" />

- 作成したメジャーを **Measures** フォルダに整理

  <img src="images/model-confirmed-cases-02.png" />

<br />

### 新しいページの追加

- 画面右の「**レポート**」をクリック

  <img src="images/select-report.png" />

- 左下の「**＋**」をクリックしてページを追加

  <img src="images/add-new-page.png" />

<br />

### スライサーの追加

- 「**視覚化**」の「**スライサー**」をクリック

  <img src="images/select-visual-slicer.png" />

- 「**フィールド**」に「**日付マスタ**」の「**年**」をドラッグして配置

  <img src="images/slicer-year-01.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**スライサーの設定**」-「**オプション**」を展開し、「**スタイル**」を「**タイル**」に変更

  「**スライサー ヘッダー**」をオフに設定

  <img src="images/slicer-year-02.png" />

- ページ上でスライサーの大きさを１行にすべての項目が表示されるよう調整

  <img src="images/slicer-year-03.png" />

- 「**視覚化**」の「**スライサー**」をクリック

  <img src="images/select-visual-slicer.png" />

- 「**フィールド**」に「**都道府県マスタ**」の「**地方区分**」をドラッグして配置

  <img src="images/slicer-area-01.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**スライサーの設定**」-「**オプション**」を展開し、「**スタイル**」を「**タイル**」に変更

  「**スライサー ヘッダー**」をオフに設定

  <img src="images/slicer-area-02.png" />

- ページ上でスライサーの大きさを１行にすべての項目が表示されるよう調整

- ドラッグして先の手順で作成したスライサーの左に表示されるよう移動

  <img src="images/slicer-area-03.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**値**」を展開

  「**値**」の「**フォントの色**」、「**背景**」の「**色**」を任意の色に変更

  <img src="images/slicer-area-04.png" />

- ページ上のスライサーに変更が反映

  <img src="images/slicer-area-05.png" />

<br />

### カードの追加

- 「**視覚化**」の「**カード**」をクリック

  <img src="images/select-visual-card.png" />

- フィールド リストの「**newly_confirmed_cases_daily**」から「**フィールド**」に「**Total**」をドラッグして配置

  <img src="images/card-total-01.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**吹き出しの値**」-「**表示単位**」を「**なし**」に変更

  <img src="images/card-total-02.png" />

- 大きさを調整し、年スライサーの下に表示されるようドラッグして移動

  <img src="images/card-total-03.png" />

<br />

### マップの追加

- 「**視覚化**」の「**マップ**」をクリック

  <img src="images/select-visual-map.png" />

- 「**場所**」に「**都道府県区分**」、「**バブル サイズ**」に「**Total**」をドラッグして配置

  <img src="images/map-01.png" />

- 「**ビジュアルの書式設定**（<img src="images/visual-format.png" width="20" />）」を選択

- 「**全般**」の「**タイトル**」をオフに設定

  <img src="images/map-02.png" />

- 大きさを調整し、カードの下に表示されるようドラッグして移動

  <img src="images/map-03.png" />

<br />

### マトリックスの追加

- 「**視覚化**」の「**マトリックス**」をクリック

  <img src="images/select-visual-matrix.png" />

- 「**行**」に「**都道府県区分**」、「**列**」に「**月**」、「**値**」に「**Total**」を指定

  <img src="images/matrix-covid-01.png" />

- 「**Total**」の「<img src="images/icon-arrow.png" width="15" />」をクリック

  「**条件付き書式**」-「**背景色**」を選択

  <img src="images/matrix-covid-02.png" />

- 条件付き書式の設定を行い「**OK**」をクリック

  - **データ形式スタイル**： グラデーション

  - **適用先**： 値のみ

  - **基準にするフィールド**： Total

  - **からの値を書式設定する方法**： ゼロとして

  - **最小値**： 任意の色（例は #ffffff を選択）

  - **最大値**： 任意の色（例は #e68f96 を選択）

    <img src="images/matrix-covid-03.png" />

- 大きさを調整し、地方区分スライサーの下に表示されるようドラッグして移動

  <img src="images/matrix-covid-04.png" />

<br />

### 完成したレポート

- ページ１

  <img src="images/report-covid-page-1.png" />

- ページ２

  <img src="images/report-covid-page-2-1.png" />

  ※ スライサーの項目をクリックしてフィルタリング

  <img src="images/report-covid-page-2-2.png" />

<br />