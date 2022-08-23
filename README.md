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
