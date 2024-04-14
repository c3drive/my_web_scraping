# my_web_scraping
https://github.com/GomaGoma676/echo-rest-api
## 学習の再開方法
1. docker-compose.ymlからrestart
1. goのコンテナに入る
```
docker exec -it go-rest-api /bin/bash
```
1. migrationを実行し、webサーバーを起動
```
GO_ENV=dev go run migrate/migrate.go
GO_ENV=dev go run main.go
```
1. pgAdminにログインする
http://localhost:5050/browser/

1. Servers > 登録
- ホスト名：dev-postgres ※composeファイルのサービスを指定
- ポート番号：5432
- 管理用データベース：postgres
- ユーザ名：postgres
- パスワード：postgres
を入力し「保存」ボタンを押下します。

1. PostManでuserデータを投入する
```
cd /Users/yukokanai/work/docker/my_tools/newman
docker exec newman newman run "collections/udemy-echo-collection.json" -e "environments/udemy-echo-dev-environment.json" --folder "SignUp"
```

1. PostManでLogin/Logoutを確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-logout-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```

1. PostManでLogin/Create Tasksを確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-post-tasks-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```

7. PostManでLogin/Tasksを確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-get-tasks-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```
1. PostManでLogin/Get Tasks/{id}を確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-get-tasks-id-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```
1. PostManでLogin/Update Tasks/{id}を確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-put-tasks-id-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```
1. PostManでLogin/Delete Tasks/{id}を確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-delete-tasks-id-collection.json" -e "environments/udemy-echo-dev-environment.json" 
```
1. PostManでget csrf/Login/を確認する（Cookieを取得するためfolderを指定せず実行します）
```
docker exec newman newman run "collections/udemy-echo-collection.json" -e "environments/udemy-echo-dev-environment.json" --folder "Get CSRF" --export-cookie-jar cookies/csrf.jar -r csv --reporter-csv-includeBody
書き換える
			"name": "Login",
			"request": {
				"method": "POST",
				"header": [            {
					"key": "X-CSRF-TOKEN",
					"value": "sACfIkop3Uuk8vkBFqb3QY66aRUaHeum",
					"system": true
				  }
				],
docker exec newman newman run "collections/udemy-echo-collection.json" -e "environments/udemy-echo-dev-environment.json" --folder "Login" --cookie-jar cookies/csrf.jar -r csv --reporter-csv-includeBody

```