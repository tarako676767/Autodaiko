Tsum 無料版セットアップ

1. .env を編集
   TOKEN=Discord Bot Token
   OWNER_ID=自分のDiscordユーザーID
   SERVER_ID=使用するサーバーID
   LOG_CHANNEL_ID=ログ用チャンネルID（不要なら0）
   TSUM_DEBUG=0
   TSUM_APP_VER=12.8.1
   TSUM_RES_VER=12.8.0

2. 依存パッケージ
   python -m pip install -r requirements.txt

3. 起動
   python bot.py

主なコマンド
/ツムツム代行       全メニュー無料
/ツムツム無料30万   1人1回30万コイン
/ツムツム状態       OWNER用設定確認

削除済み
- PayPay処理
- PayPay config
- プロキシ資格情報
- 売上機能
- accounts.jsonへのLINEメール/パスワード保存
- 未実装だったBAN回避/BAN保障メニュー

注意
LINEログイン情報はファイルへ保存しません。
Discord Bot TokenはチャットやZIPに入れた状態で共有しないでください。


現行化テスト版 (Phase 1/2)
- APP_VER/RES_VERを.envから変更可能
- getPublicKey応答のkidを動的使用
- 固定KEY_IDを廃止
- 固定AESキー/固定RSA暗号文を廃止
- セッションごとに32byte鍵を生成しRSA-OAEP
- login.nhnまで[1]〜[8]の診断ログを追加
- Token/AES key/Session ID本体はログへ表示しない

まず[8] SecureSession establishedまで通るか確認してください。
通らない場合は、秘密情報を除いた[1]〜[8]のログで切り分けできます。
