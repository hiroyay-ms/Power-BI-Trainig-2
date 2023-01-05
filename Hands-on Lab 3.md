# Power BI Hands-on training 

<br />

### **INDEX**

- [Excel ファイルからデータを読み込み](#excel-ファイルからデータを読み込み)

- [Word Cloud のインポート](#word-cloud-のインポート)

- [Word Cloud の追加](#word-cloud-の追加)

- [言語サービスを使用したキーフレーズの抽出](#言語サービスを使用したキーフレーズの抽出)

- [レポートの更新](#レポートの更新)

- [言語サービスを使用した感情分析](#言語サービスを使用した感情分析)

- [メジャーの追加](#メジャーの追加)

- [新しいページの追加](#新しいページの追加)

- [積み上げ縦棒グラフの追加](#積み上げ縦棒グラフの追加)

- [テーブルの追加](#テーブルの追加)

- [スライサーの追加](#スライサーの追加)

<br />

## AI を利用したレポート作成

### Excel ファイルからデータを読み込み

- 「**データを取得**」をクリックし、「**Excel ブック**」をクリック

  <img src="images/get-data.png" />

- 「**reviews.xlsx**」を選択し、「**開く**」をクリック

- 「**テーブル1**」を選択し、「**読み込み**」をクリック

  <img src="images/get-reviews-csv-01.png" />

- フィールド リストに「**テーブル1**」が追加

  <img src="images/get-reviews-csv-02.png" />

<br />

### Word Cloud のインポート

- 「**視覚化**」の「**…**」をクリックし、「**その他のビジュアルの取得**」を選択

  <img src="images/select-visual-others.png" />

- 右上の検索ボックスに「**Word**」と入力

- 表示された検索結果から「**Word Cloud**」をクリック

  <img src="images/get-word-cloud-01.png" />

- 「**追加する**」をクリック

  <img src="images/get-word-cloud-02.png" />

- 正常にインポートされたことを確認し「**OK**」をクリック

  <img src="images/get-word-cloud-03.png" />

<br />

### Word Cloud の追加

- 「**視覚化**」の「**Word Cloud**」をクリック

  <img src="images/select-visual-word-cloud.png" />

- 「**カテゴリ**」に「**テーブル1**」の「**Comment**」をドラッグして配置

  <img src="images/word-cloud-comment-01.png" />

- ページ一面に表示されるよう大きさを調整

  <img src="images/word-cloud-comment-02.png" />

  ※ Comment に記載された頻出単語を表示

<br />

### 言語サービスを使用したキーフレーズの抽出

- 「**ホーム**」タブの「**データの変換**」をクリック

  <img src="images/data-transform.png" />

- Power Query エディターが起動

  <img src="images/keyphrase-01.png" />

- 「**新しいソース**」-「**空のクエリ**」を選択

  <img src="images/keyphrase-02.png" />

- 画面右のクエリの設定で「**名前**」を「**KeyPhrases**」に変更

  <img src="images/keyphrase-03.png" />

- 「**詳細エディター**」をクリック

  <img src="images/keyphrase-04.png" />

- 「**詳細エディター**」が起動

  <img src="images/keyphrase-05.png" />

- 式に以下のコードを記述

  ```
  (text) => let
      apikey      = "<YOUR_API_KEY>",
      endpoint    = "https://<YOUR_CUSTOM_DOMAIN>/text/analytics/v3.0/keyPhrases",
      jsontext    = Text.FromBinary(Json.FromValue(Text.Start(Text.Trim(text), 5000))),
      jsonbody    = "{ documents: [ { language: ""en"", id: ""0"", text: " & jsontext & " } ] }",
      bytesbody   = Text.ToBinary(jsonbody),
      headers     = [#"Ocp-Apim-Subscription-Key" = apikey],
      bytesresp   = Web.Contents(endpoint, [Headers=headers, Content=bytesbody]),
      jsonresp    = Json.Document(bytesresp),
      keyphrases  = Text.Lower(Text.Combine(jsonresp[documents]{0}[keyPhrases], ", "))
  in  keyphrases
  ```

  <img src="images/keyphrase-06.png" />

  ※元の式は削除して貼り付け

- 「**apikey**」、「**endpoint**」を使用する Cognitive Services のキー、サービス エンドポイントへ変更

  「**完了**」をクリックし、詳細エディターを終了

- 画面左の「**テーブル1**」を選択

  <img src="images/keyphrase-07.png" />

- 「**Subject**」列と「**Comment**」列を選択し、「**列の追加**」タブの「**列のマージ**」をクリック

  <img src="images/keyphrase-08.png" />

- 「**列のマージ**」ダイアログで「**区切り記号**」と「**新しい列名**」を指定し「**OK**」をクリック

  - **区切り記号**： タブ

  - **新しい列名**： Merged

    <img src="images/keyphrase-09.png" />

- 「**Merged**」列がテーブル1に追加

  <img src="images/keyphrase-10.png" />

- 「**カスタム関数の呼び出し**」をクリック

  <img src="images/keyphrase-11.png" />

- 「**カスタム関数の呼び出し**」ダイアログで「**新しい列名**」、「**関数クエリ**」、「**text**」を指定し「**OK**」をクリック

  - **新しい列名**： KeyPhrases

  - **関数クエリ**： KeyPhrases

  - **text**： Merged

    <img src="images/keyphrase-12.png" />

- 「**接続情報を指定してください**」のメッセージが表示されるので、「**資格情報の編集**」をクリック

  <img src="images/keyphrase-13.png" />

- 「**Web コンテンツへのアクセス**」ダイアログで「**匿名**」タブが選択されていることを確認し「**接続**」をクリック

  <img src="images/keyphrase-14.png" />

- 「**データのプライバシーに関する情報が必要です**」のメッセージが表示されるので「**続行**」をクリック

  <img src="images/keyphrase-15.png" />

- 「**プライバシー レベル**」ダイアログで「**パブリック**」を選択し「**保存**」をクリック

  <img src="images/keyphrase-16.png" />

- 言語サービスによりキーワードが抽出された「**KeyPhrases**」列が追加

  <img src="images/keyphrase-17.png" />

- 「**ホーム**」タブの「**閉じて適用**」をクリック

  <img src="images/keyphrase-18.png" />

<br />

### レポートの更新

- ページ上の Word Cloud を選択

- 「**カテゴリ**」を「**テーブル1**」の「**KeyPhrases**」に変更

  <img src="images/word-cloud-comment-03.png" />

- Word Cloud 上の頻出単語が変更されることを確認

  <img src="images/word-cloud-comment-04.png" />

<br />

### 言語サービスを使用した感情分析

- 「**ホーム**」タブの「**データの変換**」をクリック

  <img src="images/data-transform.png" />

- Power Query エディターが起動

- 「**新しいソース**」-「**空のクエリ**」を選択

  <img src="images/keyphrase-02.png" />

- 画面右のクエリの設定で「**名前**」を「**Sentiment**」に変更

  <img src="images/sentiment-01.png" />

- 「**詳細エディター**」をクリック

  <img src="images/sentiment-02.png" />

- 式に以下のコードを記述

  ```
  (text) => let
      apikey = "<YOUR_API_KEY>",
      endpoint = "https://<YOUR_CUSTOM_DOMAIN>/text/analytics/v3.1/sentiment",
      jsontext = Text.FromBinary(Json.FromValue(Text.Start(Text.Trim(text), 5000))),
  　  jsonbody = "{ documents: [ { language: ""en"", id: ""0"", text: " & jsontext & " } ] }",
  　  bytesbody = Text.ToBinary(jsonbody),
  　  headers = [#"Ocp-Apim-Subscription-Key" = apikey],
  　  bytesresp = Web.Contents(endpoint, [Headers=headers, Content=bytesbody]),
  　  jsonresp = Json.Document(bytesresp),
  　  sentiment   = jsonresp[documents]{0}[sentiment] 
  in sentiment
  ```

- **apikey** と **endpoint** を変更し「**完了**」をクリック

  <img src="images/sentiment-03.png" />

- 画面左で「**テーブル1**」を選択し、「**列の追加**」タブの「**カスタム関数の呼び出し**」をクリック

  <img src="images/sentiment-04.png" />

- 「**カスタム関数の呼び出し**」ダイアログで「**新しい列名**」、「**関数クエリ**」、「**text**」を指定し「**OK**」をクリック

  - **新しい列名**： SentimentScore

  - **関数クエリ**： Sentiment

  - **text**： Merged

    <img src="images/sentiment-05.png" />

- 「**SentimentScore**」列が追加されたことを確認

- 「**ホーム**」タブの「**閉じて適用**」をクリック

  <img src="images/sentiment-06.png" />

<br />

### メジャーの追加

- 画面右の「**データ**」をクリック

  <img src="images/select-data.png" />

- 「**新しいメジャー**」をクリック

  <img src="images/measure-number-of-reviews-01.png" />

- 数式バーに以下を入力し、レビュー総数をカウントするメジャーを作成

  ```
  Number of Reviews = COUNTROWS('テーブル1')
  ```

- 「**書式設定**」の「**，**」をクリック

  <img src="images/measure-number-of-reviews-02.png" />

<br />

### 新しいページの追加

- 画面右の「**レポート**」をクリック

  <img src="images/select-report.png" />

- 左下の「**＋**」をクリックしてページを追加

  <img src="images/add-new-page.png" />

<br />

### 積み上げ縦棒グラフの追加

- 「**視覚化**」の「**積み上げ縦棒グラフ**」をクリック

  <img src="images/select-visual-staced-column-chart.png" />

- 「**X 軸**」、「**Y 軸**」にそれぞれフィール リストのフィールドを指定

  - **X 軸**： 「**テーブル1**」-「**Date**」-「**日付の階層**」-「**月**」

  - **Y 軸**： 「**テーブル1**」-「**Number of Reviews**」

    <img src="images/staced-column-chart-01.png" />

- ページ上で積み上げ縦棒グラフの大きさを調整

  <img src="images/staced-column-chart-02.png" />

  ※ 月ごとのレビュー数が縦棒グラフで表示

- 「**凡例**」に「**SentimentScore**」をドラッグして配置

  <img src="images/staced-column-chart-03.png" />

- レビューを mixed, negative, positive と判別して表示

  <img src="images/staced-column-chart-04.png" />

<br />

### テーブルの追加

- 「**視覚化**」の「**テーブル**」をクリック

  <img src="images/select-visual-table.png" />

- 「**列**」に「**テーブル1**」の「**Date**」と「**Comment**」をドラッグして配置

  <img src="images/table-01.png" />

- 大きさを調整し、積み上げ縦棒グラフの右に移動

  <img src="images/table-02.png" />

- 積み上げ縦棒グラフをクリックし、コメントをフィルタリングできることを確認

  <img src="images/table-03.png" />

<br />

### スライサーの追加

- 「**視覚化**」の「**スライサー**」をクリック

  <img src="images/select-visual-slicer.png" />

- 「**フィールド**」に「**テーブル1**」の「**ホテル**」をドラッグして配置

  <img src="images/slicer-hotel-01.png" />

- 「**スライサーの設定**」-「**オプション**」を展開し、「**スタイル**」を「**タイル**」に変更

  「**スライサー ヘッダー**」をオフに設定

  <img src="images/slicer-hotel-02.png" />

- 大きさを調整し、ページ上部に配置

  <img src="images/slicer-hotel-03.png" />

<br />

### 完成したレポート

- ページ１

  <img src="images/report-reviews-page-1.png" />

- ページ２

  <img src="images/report-reviews-page-2-1.png" />

  ※ ホテル名、SentimentScore でフィルタリングが可

  <img src="images/report-reviews-page-2-2.png" />

<br />