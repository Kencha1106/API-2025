# 回答用紙 （学生用）

(本Markdownファイルを記入し、課題を完成、提出すること)

##  API実習　2025　課題レポート（第3回）

**API 実習課題**: FastAPI + Streamlit + OpenAPIドキュメントの「設計」「実装」「動作確認」

###  出題範囲：　API実習2025　第7回～第9回まで

###  提出期限：　2025/12/23(火) 17:00

-------

レポート提出者：

|クラス|学籍番号|　氏名　|
|-|-|-|
|A or B| 20124001 |  會田健生 |


# 　**ToDo メモ管理 API 実習レポート（FastAPI / Streamlit）**

## 1. 実習の目的

（※ APIとは何か？今回の授業で学ぶことを100～200字程度で記述）

> **記入欄：**

---ソフトウェア同士が機能やデータをやり取りするための接続口になっている。決められたルールに従って情報を受け渡しが可能で、サービス連携や自動化を安全かつ効率的に実現ができる。

## 2. API 設計（エンドポイント仕様）

| メソッド   | パス          | 内容 | リクエスト例 | レスポンス例 |
| ------ | ----------- | -- | ------ | ------ |
| GET    | /todos      | タスク一覧を取得   |||
| POST   | /todos      | 新しいタスクを追加   | | |
| PUT    | /todos/{id} | 完了状態をトグルする   |        | |
| DELETE | /todos/{id} | タスクの削除   |        |  |

> ※ 例を JSON 形式で記載
> **記入欄：**



## 3. 使用した技術構成（選択した項目に ✓）

| 使用技術            |  使用 | 備考（任意） |
| --------------- | :-: | ------ |
| FastAPI         | [✓] |        |
| Streamlit       | [✓] |        |
| SQLite（DB 永続化）  | [ ] |        |
| SQLAlchemy（ORM） | [ ] |        |
| そのほか            | [ ] |        |

> ※ SQLite / SQLAlchemy を使用した場合は後半の加点欄も記入

---

## 4. FastAPI コード（主要部分のみ抜粋）

（※ スクリーンショット不可。**テキストで貼り付ける**）

```python
# FastAPI の主要コードをここに貼る

```
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel

app = FastAPI()

# -------------------------
# モデル定義
# -------------------------
class Todo(BaseModel):
    id: int
    title: str
    done: bool = False

class TodoCreate(BaseModel):
    title: str

# インメモリの簡易データベース
todos = []
current_id = 1

# -------------------------
# GET /todos
# -------------------------
@app.get("/todos")
def get_todos():
    return todos

# -------------------------
# POST /todos
# -------------------------
@app.post("/todos")
def create_todo(todo: TodoCreate):
    global current_id
    new_todo = Todo(id=current_id, title=todo.title, done=False)
    todos.append(new_todo)
    current_id += 1
    return new_todo

# -------------------------
# PUT /todos/{id}
# -------------------------
@app.put("/todos/{id}")
def toggle_done(id: int):
    for todo in todos:
        if todo.id == id:
            todo.done = not todo.done
            return todo
    raise HTTPException(status_code=404, detail="Todo not found")

# -------------------------
# DELETE /todos/{id}
# -------------------------
@app.delete("/todos/{id}")
def delete_todo(id: int):
    for todo in todos:
        if todo.id == id:
            todos.remove(todo)
            return {"message": "deleted"}
    raise HTTPException(status_code=404, detail="Todo not found")

---

## 5. OpenAPI ドキュメント動作確認（スクリーンショット貼付）

| 操作         | 貼付欄 |
| ---------- | --- |
| POST（新規追加） |  ![alt text](image-4.png)   |
| GET（一覧取得）  |  ![alt text](image-3.png)   |
| PUT（更新）    |   ![alt text](image-5.png)  |
| DELETE（削除） |   ![alt text](image-6.png)  |


---

## 6. Streamlit 画面 UI（スクリーンショット貼付）

| 画面キャプチャ       | 貼付欄 |
| ------------- | --- |
| 実行画面          |   ![alt text](image-7.png)  |
| 操作例（追加・更新・削除） |     |

---

## 7. API 通信ログ（サーバログ or Web通信キャプチャなど）

サーバーコンソールやログ画面のキャプチャを 1 枚以上添付

| ログ例（貼付欄） |
| -------- |
|    ![alt text](image-8.png)      |

---

## 8. 学習したこと・感想（100文字以上）

> **記入欄：**
今回の学習を通じて、API 通信の仕組みやログ解析の重要性を体感、実感しました。エラー原因を班の人、周りの友達、または自力で特定し改善できる力が身につき、開発をより主体的に進められる自信につながりました。また、実践的なトラブル対応の流れも理解が深まりました。


## チャレンジ課題：  9. SQLite / SQLAlchemy 導入内容

（使用した人のみ記述）

### 9-1. ER図（例：テーブル）

```
# 具体例を書いたり、手書きを撮影して貼っても良い

```

### 9-2. DB を使うメリット

> **記入欄：**

### 9-3. SQLAlchemy を使用した理由

> **記入欄：**


## 10. 参考資料（使用した場合のみ記入）

| 種類     | URL / 書籍名 |
| ------ | --------- |
| Webサイト |           |
| 書籍     |           |
| その他    |           |

**提出前チェックリスト**

* [ ] API のコードを貼った
* [ ] OpenAPI のスクリーンショットを貼った
* [ ] Streamlit UI の画像を貼った
* [ ] 学習したことを 100 字以上書いた
* [ ] SQLite / SQLAlchemy の加点欄（使った場合のみ）

