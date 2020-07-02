# README

## 概要
TECH:CAMPで、チーム開発を行い作成したフリマアプリです

## 機能
機能は以下の通りです。 
* ・ログイン機能
![history](https://d2v9k5u4v94ulw.cloudfront.net/assets/images/5107682/original/51f2ebd8-241d-4a52-b0ef-78abcc571b05?1591183765)

 ・商品出品機能 ・商品情報編集機能 ・商品情報削除機能 ・商品購入機能 ・商品情報詳細機能 ・商品へのコメント機能



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



