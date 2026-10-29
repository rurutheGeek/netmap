# netmap

家庭内ネットワークの構成を、図と表にして 1 ページで見せる小さな Web アプリです。
ルーターの設定、仮想化基盤、IP アドレス台帳、VPN の状態を読み取り専用で集め、
区画（セグメント）ごとの機器・経路・ファイアウォールの可否を描きます。
設定を書き換える機能はありません。

## 動かし方

Python 3.13 と、読み取りに使う各機器への到達性が必要です。

```sh
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/uvicorn app.main:app --host 127.0.0.1 --port 8096
```

設定は環境変数で渡します。必要なものは `.env.example` と、`secrets/` に置く
トークン・鍵の一覧（`compose.yaml` のコメント）を参照してください。
Docker で動かす場合は次のとおりです。

```sh
docker compose up -d --build
```

## テスト

```sh
python3 -m unittest discover -s tests
```
