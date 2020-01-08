## 1. usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
|last_name|string|null: false|
|first_name|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birthdate|date|null: false|
|tel|string|null: false, unique: true|
|profile|text||
|icon|text||

### Association
- has_many :products
- has_many :likes
- has_many :comments
- has_many :messages
- has_one :address
- has_one :card
- has_one :buyer
- has_one :seller

***

## 2. addressesテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|postal_code|int|null: false, unique: true|
|password|string|null: false|
|last_name|string|null: false|
|first_name|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birthdate|date|null: false|
|tel|string|null: false, unique: true|
|profile|text||
|icon|text||

### Association
- has_many :products
- has_many :likes
- has_many :comments
- has_many :messages
- has_one :address
- has_one :card
- has_one :buyer
- has_one :seller

***