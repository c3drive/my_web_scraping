# 初回のみ
go initコマンドを実行してプロジェクトディレクトリを作成します。
コンテナを起動
```
docker-compose up -d
```
コンテナ内に入る
```
docker exec -it go-rest-api /bin/bash
```
コンテナ内で初期化
```
go mod init go-rest-api
go mod tidy
```

## 2回目以降。
必要なファイルがある状態で新たに環境構築します。
コンテナを起動
```
docker-compose up -d
```
開発
goコマンドが必要な場合。コンテナ内に入る
```
docker exec -it go-rest-api /bin/bash
```
モジュールのインストール（import定義しているモジュールをインストールしてくれる）
```
go mod tidy
```
migrate
```
GO_ENV=dev go run migrate/migrate.go
```
web server
```
GO_ENV=dev go run main.go
```