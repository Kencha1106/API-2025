##  API実習　2025　課題レポート（第1回）修正版

####  ドラフト修正箇所
*  SheetDB無償APIの範囲内で、PATCH操作（部分更新）に修正、動作確認
*  REST4原則のチェックリストを教材テキストと整合


###  出題範囲：　API実習2025　第1回～第3回まで

###  提出期限：　2025/12/2(火) 17:00

###  提出方法：

- Githubアカウントの作成
- Githubアカウントの通知：FORMSで回答する：　**https://forms.office.com/r/CL1s98xPes**
- プライベートリポジトリの作成
- プライベートリポジトリへ、``keythrive`` を招待し承諾を得る
- **11/30までにここまで実施**する
- 課題に取り組む： Python環境**Colaboratory, Jupyter，VSCode**などで**コード記述**し，**必ず実行動作確認**する
- 課題の回答，レポートは，本マークダウンファイル（WebClassからダウンロード）を書き換えて，**自分の言葉で記述すること**
- ファイル名はそのままでよい。提出者はアカウントで特定可能
- **生成AIの回答，他学生のレポート内容をコピー＆ペーストしてはいけません**（明らかに不正行為で，自分の成長を妨げる弊害です）
- わからない問題は，進んでいる友達，学習支援センター，教員に質問して，必ず自分の理解とスキルにつなぐこと
- **考え方や不明な点を生成AIに質問して、回答そのものをもらうのではなく、考え方のヒントを聞いて、しっかり自分の中に消化吸収することは許容範囲内**
- 
- 各自のGithubのプライベートリポジトリ: https://github.com/アカウント/API-2025/report-01/ に、作成した課題レポートファイル一式をアップロード(push)、**必ずコミット**する
- 提出期限まで、ファイルの差し替え・アップデートは自由に可能
- 提出期限を過ぎたら、教員が自動取得する（**〆切を過ぎたら、差し替えできません**）

#####  指導教員：　情報学部　堀川

-------

レポート提出者：

|クラス|学籍番号|　氏名　|
|-|-|-|
|B| 20124001 | 會田健生 |


------

## 目次

## **SheetDB CRUD演習用課題レポート（11項目）**

GoogleスプレッドシートをAPI化し、SheetDBでCRUD操作を学ぶための演習課題

***

### **課題テーマ：Googleスプレッドシートをデータベースとして扱うAPI演習**

#### **前提条件**

*   Googleスプレッドシートを作成（1行目にカラム名：`id`, `name`, `email`, `score`）
*   **適当にダミーの成績データを登録する（実際の個人情報は使わない）**
*   SheetDBでAPIを作成し、エンドポイントを取得（例：`https://sheetdb.io/api/v1/XXXXXX`）
*   PostmanまたはcURLでAPIを操作して動作確認、期待した動きかどうか説明
*   更新系は、SheetDBスプレッドシート本体にデータが追加されたことを確認
*   動作確認の証跡としてスクリーンキャプチャを貼付


####  ドラフト修正箇所

*  PUT（完全更新）と PATCH（部分更新）は有償プランが必要なため、この課題から除外
  

***

### **課題一覧（10項目）**

1.  **APIエンドポイント確認**
    *   SheetDBで作成したAPIのURLを確認し、ブラウザでアクセスしてJSONレスポンスを表示
<img width="1919" height="955" alt="スクリーンショット 2025-12-01 114104" src="https://github.com/user-attachments/assets/d5749340-ae2d-463f-9c9f-e20a75cc3097" />


2.  **READ操作（GET）**
    *   全データを取得するGETリクエストをPostmanで送信。
    *   クエリパラメータ `limit` と `offset` を使ってページネーションの動作確認を実施
    *   <img width="1901" height="902" alt="スクリーンショット 2025-11-24 120651" src="https://github.com/user-attachments/assets/7d928f99-6295-4879-b0a0-a97f6fd9c07e" />

        3.  **条件検索（GET with Query）**
    *   `name` が「田中」のレコードだけ取得するGETリクエストを実行
    *   <img width="1304" height="850" alt="スクリーンショット 2025-11-25 111018" src="https://github.com/user-attachments/assets/ec2a12b9-d1de-4e43-8147-61235f2872ad" />

  4.  **CREATE操作（POST）**
    *   新しいレコード（例：`id=101, name=田中, email=test@example.com, score=85`）を追加
     <img width="1351" height="843" alt="スクリーンショット 2025-11-25 112249" src="https://github.com/user-attachments/assets/9c2436a6-df22-4af8-aafd-3c1feecbc77a" />
 
5.  **複数レコード追加（POST）**
    *   `data` 配列で複数レコードを一度に追加する。
    <img width="1918" height="932" alt="スクリーンショット 2025-12-01 093327" src="https://github.com/user-attachments/assets/a6d5ce31-9552-4f6b-b651-a129ac808480" />


6.  **DELETE操作**
    *   `id=101` のレコードを削除するDELETEリクエストを送信
    <img width="1911" height="939" alt="スクリーンショット 2025-12-01 102341" src="https://github.com/user-attachments/assets/f9297e56-c943-45a2-9779-303cf5050578" />


7.  **認証設定**
    *   SheetDBの管理画面でBasic認証を設定し、Postmanで認証付きリクエストを送信
    <img width="1914" height="935" alt="スクリーンショット 2025-12-01 102855" src="https://github.com/user-attachments/assets/41e8576c-e651-431b-ad78-0929822804f1" />


8. **エラーハンドリング**
    *   存在しない `id` を指定してDELETEを実行し、レスポンスのエラー内容を確認
   <img width="1913" height="928" alt="スクリーンショット 2025-12-01 103133" src="https://github.com/user-attachments/assets/9228c783-a3e1-4cd2-ae05-addc5f498c01" />


9. **PATCH操作（部分更新）** **修正課題**
    SheetDB無償API利用範囲で、適切なPATCH操作を行い、特定のデータを部分更新し、レスポンスを確認する：
    * エンドポイント：　https://sheetdb.io/api/v1/XXXXXX/id/23`
    * ヘッダ：　Content-Type: application/json
    * ボディ(raw json) ：
     { 
        "email": "foo@bar.baz",
    }
    * レスポンス：　HTTPステイタスコード：　200 OK
　　* curlコマンドでの動作確認も可能
    <img width="1911" height="936" alt="スクリーンショット 2025-12-02 105906" src="https://github.com/user-attachments/assets/a53b4646-7414-49b5-bf6b-1ac47dd0e9d4" />


10. **RESTの4原則対応表**
    * 上記9の設問について、下記の4原則のどれを満たしているかを表にまとめよ：

**対応表**
|番号|アドレス可能性|統一インターフェース|ステートレス|接続性|
|-|-|-|-|-|
|1|✅|　|  |✅|
|2|  |✅|✅|　|
|3|  |✅|✅|  |
|4|  |✅|✅|  |
|5|  |✅|✅✅|
|6|✅|✅|✅|✅|
|7|  |✅|✅|✅|
|8|  |✅|✅|✅|
|9|✅|✅|✅|✅|



###### RESTの4原則

1.	アドレス可能性： 情報リソースはURIで一意に特定、規則的に参照
2.	統一インターフェース → HTTPメソッド（Post/Get/Put/Delete）でリソースを操作 
3.	ステートレス → 各リクエストは独立し、サーバは状態をもたない、状態管理しない
4.	接続性：情報と情報を紐付ける情報（XML, HTML, JSON）

***

### **追加チャレンジ**  加点要素とします

*   Postmanの「Tests」タブでレスポンス検証スクリプトを記述
*   JavaScript（axios）でSheetDB APIを呼び出す簡単なWebページを作成

***



