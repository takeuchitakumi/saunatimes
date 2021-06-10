# README

# アプリ名
サウナタイムズ


# 概要
サウナの情報を投稿、閲覧できるアプリ。


# 制作背景
「人々が”ご機嫌に”働くことができる」ことを目指す私は、よくサウナを利用する。サウナは気分転換や心身のリラックスに非常に効果があるため、仕事や勉強などを頑張っている人々にぜひ足を運んでもらい、”整って”もらいたい。しかし、”整う”ためには施設の情報を前もって知っておくことが欠かせない。そこで、店舗の特徴や、混雑する時間帯などの情報を知ることができれば、サウナを利用しやすくなるのではないかと考え、制作に至った。


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

<!-- This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ... -->
