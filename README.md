# README

# アプリ名
サウナタイムズ


# 概要
サウナの情報を投稿、閲覧できるアプリ。


# 利用方法
店舗情報の閲覧、検索はゲストでも可能。店舗情報の登録、コメントはログインが必要。


# 制作背景
「人々が”ご機嫌に”働くことができる」ことを目指す私は、よくサウナを利用する。サウナは気分転換や心身のリラックスに非常に効果があるため、仕事や勉強などを頑張っている人々にぜひ足を運んでもらい、”整って”もらいたい。しかし、”整う”ためには施設の情報を前もって知っておくことが欠かせない。そこで、店舗の特徴や、混雑する時間帯などの情報を知ることができれば、サウナを利用しやすくなるのではないかと考え、制作に至った。


# 洗い出した要件
| 優先順位（高：3、中：2、低：1）| 機能          | 目的                               | 詳細                                                   | ストーリー(ユースケース)                                                                                               | 見積もり(所要時間) |
| ------------------------- | ------------- | --------------------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | --------------- |
| 3                         | ユーザー管理機能 | ユーザー管理を容易にする              | deviceを用いてユーザー管理機能を実装する                    | ・それぞれのボタンを押すと、新規登録・ログイン・ログアウトができるようにする                                                     | 3               |
| 3                         | 投稿機能        | サウナの情報を登録するため            | 入力フォームにサウナの情報を入力、完了したら表示する           | 入力フォームにサウナの情報を入力、完了したら表示する                                                                         | 5               |
| 2                         | コメント機能     | サウナの口コミを投稿するため          | サウナの基本情報だけでなく、実際に行ってみた感想などを投稿できる | ・登録された店舗の詳細ページにコメント欄を設ける  ・「コメント完了ボタン」をクリックすると、コメントとそれに紐づいたユーザー名が表示される | 5               |
| 2                         | 検索機能        | ユーザーが簡単に店舗検索できるようにする | 複数条件を指定して、店舗の検索を可能にする                   | ・店舗名/住所/料金などの検索条件を指定する欄を設ける  ・条件に該当する店舗の検索結果を表示する                                     | 5               |


# DEMO


# 実装予定の内容
・ユーザー管理を容易にするためのユーザー管理機能  
・サウナの情報を登録するための投稿機能  
・サウナの口コミを投稿するためのコメント機能  
・ユーザーが簡単に店舗検索できるようにする検索機能  


# DB設計

## users テーブル

| Column              | Type   | Options                   |
| ------------------- | ------ | ------------------------- |
| nickname            | string | null: false               |
| email               | string | null: false, unique: true |
| password            | string | null: false               |

### Association

- has_many :stores
- has_many :user_stores
- has_many :comments


## user_stores テーブル

| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| use_id         | references | null: false, foreign_key: true |
| store_id       | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :store


## stores テーブル

| Column        | Type       | Options                        |
| ------------- | ---------- | ------------------------------ |
| name          | string     | null: false                    |
| facility_type | integer    | null: false                    |
| postal        | string     | null: false                    |
| prefecture    | integer    | null: false                    |
| address       | string     | null: false                    |
| building      | string     |                                |
| phone         | string     | null: false                    |
| hp            | string     |                                |
| hour          | string     | null: false                    |
| closed        | string     | null: false                    |
| fee           | integer    | null: false                    |

### Association

- has_many :users
- has_many :comments
- has_many :user_stores



## comments テーブル

| Column       | Type       | Options       |
| ------------ | ---------- | ------------- |
| visit_date   | string     | null: false   |
| impression   | text       | null: false   |

### Association

- belongs_to :user
- belongs_to :store


# ローカルでの動作方法
$ git clone https://github.com/aocattleya/hoge.git  
$ cd hoge  
$ bundle install  
$ rails db:create  
$ rails db:migrate  
$ rails s  
👉 http://localhost:3000


# 開発環境
## バックエンド
Ruby, Ruby on Rails

## フロントエンド
Html,css,

## データベース
MySQL, SequelPro

## Webサーバ(本番環境)
heroku

## ソース管理
GitHub, GitHubDesktop

## テスト
RSpec

## エディタ
VSCode


