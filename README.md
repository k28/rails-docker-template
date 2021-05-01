# Dokcerでrailsを始めるためのテンプレート

## 事前準備

docker-compose.ymlのappのportを編集する(localで繋げるポートを編集する)  
デフォルトは8080になっている

## 手順

1. 以下のコマンドを実行

```
$ docker-compose run app rails new . --force --database=postgresql --skip-bundle
```

2. src/config/database.ymlを編集

```
default: &default
  adapter: postgresql
  encoding: unicode
  # For details on connection pooling, see Rails configuration guide
  # http://guides.rubyonrails.org/configuring.html#database-pooling
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: admin
  password: admin-pass
  host: postgres
```

3. ビルド

```
$ docker-compose build
```

4. コンテナの起動

```
$ docker-compose up -d
```

5. PostgresSQLにRailsのDBを構築する

```
$ docker-compose run app rails db:create
```

## コマンドの実行

```
$ docker-compose run app ... # ...の部分にコマンドを入れる
```

