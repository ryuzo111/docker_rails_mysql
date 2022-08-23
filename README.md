# rails_study_docker
dcokerでrailsとmysqlを構築する

# 使ったコマンドと初期設定
```docker-compose run web rails new . --force --database=mysql```

```docker-compose build```

src/config/database.ymlのdbの接続情報を書き変え
```
default: &default
  adapter: mysql2
  encoding: utf8mb4
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password
  host: db
  ```
  host はdocker-composeでdepend on した dbにする

```docker-compose run web rails db:create```
dcoker compose でwebの方で次のコマンドを実行して、dbを作成する

# 起動
```
docker-compose up -d
```
コンテナを立ち上げる<br>

localhost:3000で開く<br>
3000番ポートを指定したため<br>

# サーバーの止め方
```docker-comopose down```
削除される

# コンテナ内で任意のコマンドの実行
```docker-compose exec web [コマンド名]```

# dockerファイルやgemfileの修正を反映させたい時
イメージを作り直す
```docker-compose build```
```docker-compose up -d```
