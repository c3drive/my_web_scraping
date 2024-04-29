https://github.com/GomaGoma676/react-todo
# 初回のみ
go initコマンドを実行してプロジェクトディレクトリを作成します。
コンテナを起動
```
docker-compose up -d
```
コンテナ内に入る
```
docker exec -it go-rest-web /bin/bash
```
プロジェクト作成
```
npx create-react-app react-todo --template typescript --use-npm
npx tailwindcss init
```
cssを書き換える
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

# 2回目以降
必要なファイルがある状態で新たに環境構築します。
コンテナを起動
```
docker-compose up -d
```
開発
コンテナ内に入る
```
docker exec -it go-rest-web /bin/bash
```

web server
```
cd react-todo
npm start
```