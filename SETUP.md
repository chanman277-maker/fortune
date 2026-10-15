# 占いノート クラウド同期 セットアップ手順（約10分・無料）

## 1. Firebase プロジェクトを作る
1. https://console.firebase.google.com/ を開き、Googleアカウントでログイン
2. 「プロジェクトを作成」→ 名前（例: fortune-journal）→ Googleアナリティクスは「オフ」でOK → 作成

## 2. Google ログインを有効にする
1. 左メニュー「構築」→「Authentication」→「始める」
2. 「Sign-in method」タブ →「Google」→ 有効にする → サポートメール（自分のGmail）を選んで保存
3. 「設定」タブ →「承認済みドメイン」→「ドメインを追加」→ `chanman277-maker.github.io` を追加
   （※ これを忘れるとGitHub Pages上でログインできません）

## 3. Firestore データベースを作る
1. 左メニュー「構築」→「Firestore Database」→「データベースを作成」
2. ロケーションは `asia-northeast1`（東京）を選択
3. 「本番環境モード」で開始
4. 「ルール」タブを開き、`firestore.rules` の中身を貼り付けて「公開」
   （自分のログインIDのデータだけ読み書きできるルールです）

## 4. 設定値を index.html に貼る
1. プロジェクトの設定（歯車）→「全般」→「マイアプリ」→ ウェブ（`</>`）アイコンでアプリを登録
2. 表示される `firebaseConfig` の値を、`index.html` 内の `firebaseConfig` に貼り付け
   （apiKey は公開されても問題ありません。守っているのは手順3のルールと承認済みドメインです）

## 5. 公開する
`index.html` を GitHub の fortune リポジトリの `index.html` に上書きしてコミット／プッシュ。
数分後に https://chanman277-maker.github.io/fortune/ で、Googleログイン画面が出ればOKです。

## 初回ログイン時
そのブラウザに以前の記録（localStorage）が残っていれば、「クラウドに引き継ぎますか？」と聞かれます。OKで移行されます。
スマホなど別端末の古い記録は、先に「データ管理」からバックアップを書き出し、新版で読み込んでください。
