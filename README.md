# README

## 概要
TECH:CAMPで、チーム開発を行い作成したフリマアプリです
* Top画面

![main](https://user-images.githubusercontent.com/63226783/86332392-6fc3da00-bc85-11ea-8315-6f16b2cbd789.gif)

* 購入画面

![login](https://user-images.githubusercontent.com/63226783/86332705-d812bb80-bc85-11ea-8e11-e6a8a5facd94.gif)

* クレジット登録画面

![reg](https://i.gyazo.com/d8b0ed3e7403f9c0c31086e72b8a2656.png)

## 機能
・ログイン機能・商品出品機能 ・商品情報編集機能 ・商品情報削除機能 ・商品購入機能 ・商品情報詳細機能 ・商品へのコメント機能

## ・使用技術(開発環境)
* Ruby 2.5.1, Rails 5.0.7.2
* MySQL 5.6.47
* Capistrano, Nginx, Puma, unicorn
* AWS（VPC, EC2, RDS, Route 53, ALB, S3）
* Pay.jp
* RSpec
* Sass, jQuery
* Visual Studio Code  
* Github


## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|first_name|string|null: false|
|first_name_furigana|string|null: false|
|last_name|string|null: false|
|last_name_furigana|string|null: false|
|birthday|date|null: false|
|profile_photo|string|null: false|
|tel_number|string|null: false|
|introduction|text|


### Association
- has_many :likes
- has_many :products
- has_many :comments
- has_many :cards
- has_one :address


## productsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|explanation|text|null: false|
|price|integer|null: false|
|brand|string|
|status|integer|null: false|
|bear|integer|null: false|
|days|integer|null: false|
|user_id|integer|foreign_key: true, null: false|
|category_id|integer|foreign_key: true, null: false|

### Association
- has_many :likes, -> { order(created_at: :desc) }, dependent: :destroy
- has_many :product_photos
- has_many :comments
- belongs_to :category
- belongs_to :user


## addressesテーブル

|Column|Type|Options|
|------|----|-------|
|postal_code|integer|null: false|
|city|string|null: false|
|other|string|null: false|
|building_name|string|
|user_id|integer|foreign_key: true, null: false|

### Association
- belongs_to :user


## cardsテーブル

|Column|Type|Options|
|------|----|-------|
|customer_id|string|null: false|
|card_id|string|null: false|
|user_id|integer|foreign_key: true, null: false|

### Association
- belongs_to :user


## likesテーブル

|Column|Type|Options|
|------|----|-------|
|user|reference|foreign_key: true, null: false|
|product_id|integer|foreign_key: true, null: false|

### Association
- belongs_to :product
- belongs_to :user


## product_photosテーブル

|Column|Type|Options|
|------|----|-------|
|photo|string|null: false|
|product_id|integer|foreign_key: true, null: false|

### Association
- belongs_to :product


## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user|reference|foreign_key: true, null: false|
|product_id|integer|foreign_key: true, null: false|

### Association
- belongs_to :user
- belongs_to :product


## categoriesテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|foreign_key: true, null: false|

### Association
- has_many :products



