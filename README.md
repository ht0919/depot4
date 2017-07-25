# Depot for Rails 4.0.2

- 書籍『RailsによるアジャイルWebアプリケーション開発(第４版)』のサンプル(depot)をRails4に移植した時の変更記録です。

## 動作環境

- OS: macOS 10.12.6
- Ruby: 2.0.0-p353
- Rails: 4.0.2

## 実装手順

```
$ git clone https://github.com/ht0919/depot4.git
$ cd depot4
$ bin/bundle install
$ bin/rake db:migrate
$ bin/rake db:migrate RAILS_ENV=test
$ bin/rake db:seed
$ bin/rake test
$ bin/rails server
```

## 第6章 タスクA:アプリケーションの作成

- confirmの表記(p.71)
  - 修正前：confirm: 'Are you sure?',
  - 修正後：__data: {__ confirm: 'Are you sure?' __}__,


## 第7章 タスクB:検証とユニットテスト

- 正規表現の記号(p.78)
  - 修正前：with: %r{\.(gif|jpg|png)__$__}i,
  - 修正後：with: %r{\.(gif|jpg|png)__\z__}i,


- 機能テストのフォルダ名(p.78)
  - 修正前：test/__functional__/products_controller_test.rb
  - 修正後：test/__controllers__/products_controller_test.rb


- ユニットテストのフォルダ名(p.80)
  - 修正前：test/__unit__/product_test.rb
  - 修正後：test/__model__/product_test.rb


- ユニットテストの実行(p.81)
  - 修正前：rake test:__units__
  - 修正後：rake test:__models__


- I18nによるテスト(p.86)
  - 準備：config/locales/en.ymlを以下のように修正
  ```
  en:
    hello: "Hello world"

    activerecord:
      errors:
        messages:
          taken: "has already been taken"
  ```


## 第8章 タスクC:カタログの表示

- rootのURLを設定(p.90)
  - 修正前：root to: 'store#index', as 'store'
  - 修正後：root 'store#index'

- index.htmlの削除(p.91)
  - 修正前：rm public/index.html
  - 修正後：何もしない

- 機能テストのフォルダ名(p.98)
  - 修正前：test/__functional__/store_controller_test.rb
  - 修正後：test/__controllers__/store_controller_test.rb

- 機能テストの実行(p.100)
  - 修正前：rake test:__functionals__
  - 修正後：rake test:__controllers__


## 第9章 タスクD:カートの作成

- 機能テストのフォルダ名(p.107)
  - 修正前：test/__functional__/line_items_controller_test.rb
  - 修正後：test/__controllers__/line_items_controller_test.rb

- 機能テストの準備(p.107)
  - rake db:migrate RAILS_ENV=test

- 機能テストの実行(p.107)
  - 修正前：rake test:__functionals__
  - 修正後：rake test:__controllers__
